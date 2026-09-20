---
title: "Hands-On Labs: Reliability for Beginners (2026)"
layout: default
---

# Hands-On Labs: Reliability for Beginners (2026)

*Companion to "Reliability First: An SRE Guide for People Starting Out in 2026."*
Cloud-agnostic — every lab runs on any laptop, any cloud, or a rented box. Assume nothing but curiosity, a terminal, and ~6 focused sessions.

**How to use:** do the labs in order. Each one hands you a template or a scenario — you do the thinking, we supply the rails. Estimated time per lab: 1–1.5 hours.

---

## Lab 0 — The playground (30 min)

Spin up a *pet service* — you'll break it on purpose over the next sessions, so keep it tiny and non-precious.

**Pick one** (any works, or build your own):
- A small HTTP API that returns "hello" with a random 50ms–1500ms delay (to simulate latency)
- A service that queues "orders" into a local message broker and processes them
- The SRE Classroom distributed image server (see sre.google/classroom)

**Requirements:**
- Runs locally or on any single cloud box
- A health endpoint (`/health`)
- Logs to a file (`access.log`), one line per request, with a timestamp
- Deployable with one command

**Deliverable:** the pet service runs and `curl /health` works.

---

## Lab 1 — Design it on paper first (NALSD)

Before touching more code, draw the whole thing. Find a whiteboard (or a napkin).

For your pet service, answer in writing:

1. **Users** — who calls it? How many requests/second at peak? What does "good" look like from their side?
2. **Traffic path** — every hop from client → you: DNS, load balancer, app, database, broker. Draw it.
3. **Storage** — where does state live? What happens if it's lost?
4. **Failure modes** — list 10 ways it can break (network blip, disk full, a dependency down, a bad config pushed, a traffic spike, a zombie process...).
5. For each failure mode: **what does the user experience?** Button fails silently? Timeout? Blank page?
6. **Big red button** — for each failure: what single, simple action reverts or contains it?

**Deliverable:** one diagram + one table (failure mode → user impact → big red button). This is literally the Non-Abstract Large System Design exercise from the SRE library.

---

## Lab 2 — Write the SLO by hand

Now make "reliable" measurable. Skip the fancy tools — a spreadsheet or even a notebook is fine.

1. **Choose one SLI** that reflects the user experience. Suggested default for an API:
   `successful requests / all requests`, where "successful" = HTTP 200 AND latency < 500ms.
2. **Collect the data.** Add instrumentation to your pet service: log whether each request was a success, then script a daily count. Run it for a few days or use the built-in latency.
3. **Set the SLO.** Pick a target (99%, 99.9%, 99.99%) and defend the choice in three sentences — what's the cost of going higher?
4. **Compute the error budget.** For a 30-day window, how many failures can you afford?
5. **Write the SLO document** using this template (adapt from Appendix A of *The Site Reliability Workbook*):

```
# SLO: <<service name>>
Owner: <<you>>
Last updated: <<date>>

## Service description
What it does, who depends on it, why it exists.

## SLI definitions
- Availability = good_requests / total_requests, where good = 2xx/3xx (not 4xx) AND latency <= 500ms
- Measurement window: rolling 30 days, daily sampling

## SLO targets
- Availability: 99.9% (error budget ~43.8 min/mo)

## What happens when the budget is exhausted
- <<e.g., we pause feature work; we add capacity; we fix the biggest failure first>>

## Why this target (the honest negotiation)
- <<the cost/revenue/user discussion that justifies 99.9% vs 99.99%>>
```

**Deliverable:** a complete SLO document, plus one sentence answering: *"What non-obvious thing did you discover when you had to define 'good'?"*

---

## Lab 3 — One alert that means something

Most alerting fails by alerting on everything. Design one alert that a reasonable human would want to wake up for.

1. **Start from the SLO, not the symptom.** Your alert should fire when the *error budget is being consumed faster than planned* — not when CPU hits 90%.
   Model it simply: track successes vs request count; when the observed failure rate would exhaust this month's budget within X hours, fire.
2. **Write the alert's "runbook"** (the one pager the on-call sees):
   - What the alert means, in one sentence
   - First thing to check (your big red button list)
   - The response expected (e.g. "roll back the last deploy")
   - When NOT to page (escalation criteria, "wait and watch")
3. Turn off or silence at least half of whatever auto-generated alerts your stack emits. **This step is mandatory.** Deleting noise is a reliability improvement.
4. **Test the alert** — break the pet service, confirm it fires, confirm the message makes sense *to someone who wasn't you when you wrote it*.

**Deliverable:** one alert + its runbook, and a note on what you deleted.

---

## Lab 4 — Canaries and the big red button

Safe change management in one hour. Do this on your pet service after adding a deliberate "bad deploy" (e.g., a version that always sleeps 20 seconds).

**Part A — Canary:**
1. Deploy the good version to 100%.
2. Now roll the *bad* version to 5% of traffic (or one instance in a pool).
3. Watch the SLI you defined in Lab 2. How long until the signal looks wrong? (If your setup can't split traffic, simulate: run bad + good instances side by side and compare their `/health` latency.)
4. Roll back bad → good. Confirm recovery.
**Write down:** how much user impact did the canary prevent versus rolling straight to 100%?

**Part B — Big red button:**
1. Define it *before* the change: "revert to previous image + restart service" as one documented command.
2. Test that it actually works. Time it.
3. Now break the service, wait 30 seconds, and exercise the button. Target: recovery in under 2 minutes.

**Deliverable:** the canary step logs + your red-button command with its measured recovery time.

---

## Lab 5 — Chaos against yourself (safely)

In a sandbox, deliberately break your service and watch how it degrades. Use only your own toy — never a shared system.

Run these one at a time, 10–15 minutes each, logging what you observe:

1. **Kill the database/broker.** Does the API fail fast or hang forever? (Hanging is the enemy.)
2. **Saturate the box.** Fire 10x normal traffic at it (a `for` loop or any load tool). Do errors stay inside the error budget? Does the whole process fall over all at once (no graceful degradation)?
3. **Slow a dependency** (simulate +2s latency on one call). Do other features degrade too? This is how cascading failures start.
4. **Latent bug:** add a bug that only fires 1 in 50 requests. See how long it takes *your* alerting to notice. (If it never does, that's the finding.)

**After each break:** in your incident journal, write *symptom → cause → what a good fix would be*.

**Deliverable:** one page per experiment — what broke, what degraded, what the user would've felt, and one design change that would've made it less bad.

---

## Lab 6 — Incident drill + blameless postmortem(ish)

You can't rehearse a fire escape using a ladder for the first time during a fire. So drill now.

**The drill (30 min, with a timer):**
1. Two people minimum if possible (a friend is fine). One is the "on-call," one is "incident commander."
2. Break the pet service WITHOUT telling the on-call how.
3. The responder discovers it via the *alerting system only* — nothing else.
4. Run the structure: declare incident → IC coordinates → comms lead (the non-responding one posts status updates every 5 min, even "nothing new") → mitigation → recovery.
5. Time it. Compare to the Lab 4 red-button baseline.

**Then write the postmortem** (template – adapt from Appendix D of *The SRE Book*):

```
# Postmortem: <<incident name>>
Date / Duration / Incident Commander / Responders

## Summary (one paragraph)
## Impact (users, time, cost — with error-budget impact)
## Timeline (every notable event, times in UTC)
## Root cause(s) — systemic, not personal
## What went well
## What went wrong
## Action items (each: owner, description, ETA, and the test that proves it's done)
```

**Rules:** blameless — assume everyone was doing their best in good faith. The point is the *systemic* gaps.

**Deliverable:** timing from break → detection → mitigation, plus the postmortem with at least one committed action item and a way to verify it.

---

## Lab 7 — 2026: supervise the machine

You don't need real AI to learn the 2026 lesson: autonomy must be *earned* and *supervised*. Build it tiny.

**Part A — Curate the data:**
1. Take your Lab 2 SLO document, incident journal, and postmortems. You now hold what an "AI on-call" would need to learn from. List the 5 datasets a training/eval pipeline would require to safely take over your pet service's on-call. (Hint: golden examples of the right response; playbooks; dependency map; historical incident records; SLO truth. Google calls these the "Golden/Silver/Bronze" tiers.)
2. Write one golden example by hand: *"symptom → investigation steps → correct mitigation → verification."*

**Part B — Design the guardrails:**
For a hypothetical AI agent that can restart your service, everyone else's service, or worse — answer in writing:
1. **Progressive authorization:** what must be true before it earns the right to restart an instance at L2 (human approves)? At L3 (acts alone)?
2. **Least privilege:** what would you *withhold* from the agent even at L4? (Think: billing, prod credentials, deleting data.)
3. **Dry-run:** what does its "predict the outcome first" step look like for a restart?
4. **Red button:** how does a human pause *all* agent actions fleet-wide, instantly?
5. **Transparency:** what would its chain-of-thought log need to capture for you to trust it?

**Deliverable:** a one-page "agent safety charter" for your pet service. Give it a scary title — this is the document real teams are writing right now.

---

## Capstone — your reliability dossier

Finish with a folder that says, to any interviewer or team lead: *this person understands production.*

Collect:
- [ ] Your NALSD diagram + failure/red-button table (Lab 1)
- [ ] A signed-off SLO document with error budget (Lab 2)
- [ ] One alert with runbook (Lab 3)
- [ ] Canary logs + timed red button (Lab 4)
- [ ] Chaos experiment write-ups (Lab 5)
- [ ] One drill timed run + blameless postmortem (Lab 6)
- [ ] One-page agent safety charter (Lab 7)

**Final reflection (write it):** *"What is my service actually promising its users, how do I measure that I kept the promise, and what's my first move when I can't?"*

If you can answer that out loud, you have more production judgment than most people a year into the job.

---

## Reference templates quick-glance

| Need | Template |
|------|----------|
| SLO document | Lab 2 §5 |
| Error-budget policy | Appendix B, *Workbook* |
| Incident state doc | Appendix C, *SRE Book* |
| Postmortem | Lab 6 / Appendix D, *SRE Book* |
| Launch checklist | Appendix E, *SRE Book* |

All source material: **sre.google/resources** (all free).