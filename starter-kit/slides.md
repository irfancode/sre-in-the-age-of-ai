---
marp: true
theme: default
paginate: true
author: Reliability First
title: Reliability First — A Beginner's Guide to SRE (2026)
description: Slide companion to the full book. Cloud-agnostic, updated for 2026.
layout: default
---

<!-- _class: lead -->

# Reliability First

**A Beginner's Guide to SRE — 2026 edition**

Cloud-agnostic. Skill-agnostic. Built for day one.

*Companion deck to the full book. All material free & open from the Google SRE library.*

---

## What you'll take away

1. The one idea SRE was built on
2. SLIs, SLOs, error budgets — the trust machine
3. Designing systems that fail gracefully
4. The everyday loop: monitor, on-call, postmortem
5. Why heroism is bad (& why everyone still does it)
6. **2026:** AI agents in the operations room
7. Your first 90 days

---

## The one idea

Software engineering and operations are the **same discipline**.

So: hire engineers to build the systems that keep systems alive.

> "Reliability is software. Reliability is negotiated. Failure is data."

- 100% uptime is a myth. Reliability is a trade.
- Fix the *system*, not just today's fire.

---

## The trust machine

| Term | Meaning |
|------|---------|
| **SLI** | What you measure (e.g. "requests that succeeded in <500ms") |
| **SLO** | The target you promise (e.g. "99.9% over 30 days") |
| **Error budget** | The allowance to take risks = **100% − SLO** |

The error budget ends the dev-vs-ops war:

- New feature? **Spend the budget.**
- Budget gone? **Stop launching. Fix things.**

---

## The nines (memorize this)

| Target | Allowed down / year |
|--------|---------------------|
| 99% | ~3.65 days |
| 99.9% | ~8.8 hours |
| 99.99% | ~52 min |
| 99.999% | ~5.3 min |

Every extra nine costs **dramatically more**. Negotiate the SLO — don't assume.

---

## Honesty check: numbers lie

> "The purpose of computing is insight, not numbers." — Hamming

- **Error budgets have error margins** (impact estimates are often off 10x)
- **SLOs assume linearity** (a few users always broken ≠ a little broken for everyone)
- **SLIs are easy data, not best data** (the angry support ticket often beats the metric)

---

## Design for failure *before* the failure

Google's 20 years of outages → 11 lessons. A few you'll live by:

- **Canary every change.** 1% first. Watch. Then roll.
- **Big red button.** A known, simple revert on everything.
- **Test your recoveries**, not just your features.
- **Risk of mitigation ≤ severity of outage.** Calm beats clever.
- **Backup comms channels** (and backups of those).
- **Degrade gracefully.**
- **Ship small & often** — each deploy becomes easy to reason about.
- **Diversity is insurance** — one model of anything = one point of failure.

---

## The daily loop

- **Monitor:** four golden signals — *latency, traffic, errors, saturation*
- **Alert on the SLO, not the symptom.** Every alert needs an actionable response
- **Toil:** manual, repetitive, automatable — cap it at ~50% of your time
- **On-call:** rotations, interrupts, clear ownership of the pager

> A busy team is often a drowning team. Busy ≠ effective.

---

## Why heroism is bad

The hero **personally fills a system gap forever** — weekends, 14-hour days.

| Costs the system | Costs the team | Costs the hero |
|------------------|----------------|----------------|
| The gap never gets fixed | Sets impossible norms | Burnout |
| No honest SLO talk | Everyone feels inadequate | No promotion (no durable work) |

**The cure: let the system break.** You have an error budget — spend some of it to *get the signal* that forces the real fix.

---

## Incidents & postmortems

- **Declare early.** "It's a blip" → outage. Escalate, then relax later.
- **Roles:** incident commander · comms lead · responders
- **Postmortems are blameless.** Punish the system, not the person — or the next one hides.
- **Action items or it's a diary entry.**
- **Track trends.** Same subsystem in every postmortem = the bug.

---

## 2026: AI moves in

The problem: AI assistants multiply code output (up to **4x**). Human review and human on-call can't scale with that.

The answer is a **maturity ladder** for AI operations:

| Level | Monitor | Investigate | Approve | Actuate |
|-------|---------|-------------|---------|---------|
| L0 | human | human | human | human |
| L1 | AI | AI suggests | human | human |
| L2 | AI | AI | human | AI* |
| L3 | AI | AI | AI* | AI (bounded) |
| L4 | AI | AI | AI | AI |

\* = still watchful human, gated by safety checks

---

## The safety trifecta (for machines that touch production)

1. **Transparency** — full chain-of-thought, auditable, replayable
2. **Real-time risk evaluation** — same action, different risk at 2am vs peak
3. **Progressive authorization** — autonomy is *earned* level-by-level, against evidence

**Guardrails that are law:**
- No ambient access — agents get their own low-privilege identities
- Mandatory **dry-run** — predict the blast radius first
- Circuit breakers + an interrupt on every action
- **Big red button for the whole fleet of agents**

---

## What AI can & can't do (2026)

**Can:**
- Enrich alerts with context (~2-min budget)
- Suggest incident hypotheses (**~10% faster** mitigation)
- Auto-build investigation dashboards (**~44% faster**)
- Hear the users' brokenness first (support tickets, forums, social)
- Mitigate *known, well-scoped* incidents autonomously

**Can't (yet):**
- Handle the *novel* — which is where the big outages live

**→ That gap is your career opportunity.**

---

## What this means for you

- **AI runs on curated data** — SLOs, dependency graphs, playbooks, incident history, "golden" answers
- **Curation is now the core job.** Come in knowing SLOs are the input format of the machine
- **Humans move UP the abstraction ladder:** review design, intent, policy — audit the machine's reasoning
- **Security = reliability.** In 2026 they're one field
- Stay skeptical: *"unusual is not automatically bad"*

---

## Your first 90 days

| Weeks | Do |
|-------|----|
| 1–3 | Read: principles chapters, *Why Heroism is Bad*, *20 Years of Lessons*. Start an incident journal. |
| 4–6 | SRE Classroom design exercises. Build a pet service; write an SLO by hand. |
| 7–9 | Shadow on-call. Read 3 real postmortems. Break your pet service on purpose. |
| 10–12 | Draw your system end-to-end (NALSD). Write: "the reliability of my thing." |

---

## The library (free)

- **Site Reliability Engineering** — the playbook
- **The Site Reliability Workbook** — exercises + SLO templates
- **Building Secure & Reliable Systems**
- **Why Heroism is Bad**
- **Twenty Years of SRE Lessons**
- **Measuring Reliability**
- **AI Engineering: Reliable Operations** (2026 direction)

→ all at **sre.google/resources**

---

<!-- _class: lead -->

# The scarce thing is still judgment under uncertainty.

**Everything else — including the machines — is tooling. Build it now.**