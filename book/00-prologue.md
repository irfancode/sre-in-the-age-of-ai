---
title: "Chapter 0 — From Pager to Prompts"
layout: default
---

<div class="chapter-meta"><b>Status:</b> The transformation you need before anything else. <b>Reading time:</b> 15 minutes. <b>Who this is for:</b> literally everyone, including your parents.</div>

# Chapter 0 — From Pager to Prompts

## What SRE Was (2003–2017)

In 2003, a Google engineer named Ben Treynor Sloss was asked to run a "production team" of seven people who kept Google's services alive. He did what engineers do: he designed it the way he'd want to be managed, and he began hiring **software engineers** — people who get bored doing things by hand — to run production systems.

He called the result **Site Reliability Engineering**. The idea was quietly revolutionary:

> Stop hiring people to *push buttons*. Hire people who will *build machines that push the buttons for them*.

Every famous SRE idea comes from that shift. Let's walk them quickly, because they're the bones of everything that follows:

**1. SRE = an engineer designing an operations team.**
Instead of operators who run systems by hand, you get builders who make the system run itself. At Google, roughly half the SRE team were software engineers; the rest were sysadmins *close enough* to engineering hire-bar that they could build tools too. Everyone wrote code or went home.

**2. The 50% rule.**
If a team spends more than 50% of its time on "ops" (tickets, pager pages, manual fixes), it's drowning. When you drown, you can't build. So SRE set a 50% cap on ops work: the *other* half of your life belongs to engineering — building the thing that eliminates the ops work.

**3. Risk is a dial.**
Nobody at a rational company wants 100% uptime. It's brutally expensive, it slows innovation to a crawl, and — here's the kicker — *users cannot tell the difference* between 99.99% and 99.999%. Your phone, your WiFi, and your power company are each less reliable than that. The last 0.001% is money spent on noise. So SRE asked not "how do we make this never fail?" but "how much risk are we willing to *cheerfully accept*?"

**4. Error budgets.**
If your service's target is "at least 99.9% available," then you have a budget of 0.1% *unavailability* — about 8.7 hours of allowed misery per year. Here's the trick: **that budget belongs to the product team.** Spend it on features. Launch fast. If you spend your whole error budget on a disaster, launch-freeze until you've paid it back. This one idea dissolved a forever-war between "we want to ship" (devs) and "don't you dare touch it" (ops) — it turned the war into a bank account.

**5. Toil is a tax.**
"Toil" = the tiring, repetitive, manual work that doesn't get smarter with repetition: restarting pods, applying config, answering the same question forty times. SRE's rule: if you do it by hand twice, automate it. If you've automated it, make the machine repair the machine. The dream was always **systems that are automatic, not just automated.**

**6. Blameless postmortems.**
Every significant incident gets a write-up that answers: *what happened, why, and what do we change so it never hurts us again?* Notice: **nobody is asked to confess.** The system is the villain. Google found that blame-free investigation finds ten times more root causes than witch-hunting does.

**7. Monitored by machines, paged for humans.**
"Monitoring should never require a human to interpret anything." Either the system knows what to do (and does it), or it needs a human *right now* (pager), or it can wait (ticket), or it's just logged for later. Three decades later this is still under-implemented, which is why we're here.

**8. Root cause is a starting point, not the answer.**
Classic SRE framed reliability as *MTTF* (how long until it breaks) and *MTTR* (how fast we fix it). Since you can't avoid failures, your highest-leverage question is: *how fast can I get back to healthy?* Answer: pre-written playbooks (≈3x faster MTTR), and practice, practice, practice.

That was the 2017 book: forty chapters of this thinking, tuned mostly inside Google's private universe, aimed at engineers, full of acronyms, occasionally hilarious, deeply correct.

## What Happened on the Way to 2026

Now the plot twist — the years 2017–2026 shoved four spanners into that tidy machine:

### Spanner 1: The cloud stopped being Google's private meeting room.
Kubernetes, Terraform, AWS, Azure, GCP: the entire world absorbed SRE's trick. Production now is *infrastructure-as-code* — your servers, networks, and databases are defined in files that can be versioned, reviewed, and *reproduced*. Anyone with a laptop and a credit card can run systems that would have taken 2002-Google a warehouse. Good news: SRE thinking is now a normal skill, not a secret sect.

### Spanner 2: AI made software ship at a speed humans can't supervise.
By 2025, AI coding assistants were drafting the bulk of new code in many teams. **The 2025 DORA study measured incidents-per-pull-request up by 242.7%** — code velocity exploded, and operational capacity did not. Suddenly "release fast" wasn't a business preference; it was an ambient condition of building software at all. Reliability became the bottleneck *feature*.

### Spanner 3: AI grew up from "toy" to "teammate."
Three AI turns changed SRE forever:

- **Turn one — AIOps / ML detection (2017–2022):** alerting stops being "threshold > 95%" and starts being "this looks unusual *for* your system." Anomaly detection reads your patterns instead of your static config.
- **Turn two — AI SRE copilots (2023–2025):** LLMs that can read logs, metrics, and traces and *answer questions* about them: "why is checkout slow?" — the beginnings of automated root-cause analysis.
- **Turn three — Agentic SRE (2025–2026):** autonomous agents that don't just answer, they *act*: triage alerts, group incidents, run playbooks, propose fixes, open pull requests, and with approval gates, execute them. Google publicly dubbed its program **"SRE AI."** Microsoft shipped **Azure SRE Agent** generally available in March 2026. Open source grew its own: **Aurora, K8sGPT, HolmesGPT.** Gartner now projects **70% of enterprises will run agentic AI over their IT operations by 2029.**

### Spanner 4: AI added *entirely new failure modes* to the systems SREs protect.
It's not just that AI helps SRE. It's that AI products need SRE-ing themselves. Models hallucinate, agents loop, context windows flood, prompts get injected, and a system can be **technically "up" while producing confidently wrong output.** Reliability for "what the machine believes" is a brand-new discipline with a brand-new vocabulary:

- **Judgment SLOs** — targets on *decision quality*, not just uptime ("fewer than 5% of agent tasks require a human override").
- **Safety SLIs** — behavioral guardrail metrics for agents (policy compliance, hallucination rate, tool-call accuracy).
- **Autonomy as a budget** — an agent *earns* more autonomy when its safety record is clean and *loses* it when it burns budget.
- **The verification tax** — the uncomfortable new reality that every AI-generated change must be *checked*, and checking can create as much toil as it removes.

## What SRE Is Today (2026)

Here's the whole transformation in one table:

| | SRE (2017) | SRE (2026) |
|---|---|---|
| **Primary asset** | Servers, clusters, config | Servers + models + agents + *trust* |
| **Who fixes things** | A human with a playbook | An AI agent, verified by a human, sleeping with one eye open |
| **Main hazard** | A pod crashed | A model confidently hallucinating, or an agent looping on a task |
| **Reliability means** | Available, fast, correct | Available, fast, correct, *and safe to let act* |
| **Automation** | Scripts & pipelines (deterministic) | Deterministic pipelines + **probabilistic agents** with approval gates |
| **The nines** | 99.9% | 99.9% *plus* judgment SLOs and safety SLIs |
| **The pager** | A beeper you fear | Your AI first-responder does triage; the page you get comes with a diagnosis |
| **Error budget** | A quarterly allowance of downtime | Allowance of downtime *and* an autonomy budget for your agents |
| **Root-cause analysis** | Hours of grepping logs by hand | Minutes, agent-correlated, with a proposed fix |
| **Postmortem** | Written by the human who lived it | Written by an agent, reviewed by the human who was responsible |
| **Toil** | The enemy | Still the enemy — and watch out, AI can *generate* toil as fast as it kills it |
| **Cloud lock-in** | Google's way | None: this book is written to run on any cloud or your own basement |

### The honest truth about the AI SRE (with receipts)

Current research (SREGym, a 2026 high-fidelity benchmark of 90 realistic failure scenarios) put frontier AI agents through their paces. The numbers:

- **Diagnosis success: ~38–73%** and **mitigation success: ~40–79%** — strong on application-layer issues, dramatically weaker on low-level infrastructure faults (OS, hardware) and *compound* failures (several things failing at once).
- Give an agent a **brand-new failure pattern** it has never seen and its end-to-end success collapses to ~15–28%.
- Agents get **distracted by "noise"** — unrelated events in a messy production system.

Translation: the AI SRE is real, it's genuinely useful, and it is *not ready to run your night shift alone.* It's a brilliant intern with a supercomputer and no context of your ancestors. Your job in 2026 is to raise it well: give it playbooks, good telemetry, approval gates, benchmarks, and a human who signs the checks.

### So what *is* the 2026 SRE?

> **SRE in the age of AI is the discipline of keeping promises.** A system — human-run, machine-run, or agent-run — makes promises to its users: "you'll get a reply in under a second," "your money won't vanish," "this answer is true." SRE is the engineering of making and *verifying* those promises, using whatever tools exist: automation where they're boring, AI where they're smart, humans where the stakes deserve a judgment call. The tools change. The promises don't.

The beautiful consequence — and the reason this book begins the way it does — is that 2026 is the **best time in history for a total beginner to become an SRE:**

- Infrastructure-as-code means you can *read* the entire production system like a book.
- AI agents will draft your playbooks, interrogate your logs, and write your first postmortem *for you* — you just have to verify, which is exactly the skill the job trains.
- And the market needs you: at agentic speeds, there's no such thing as enough good humans to check the machines.

Now, before the machines, you need to understand what machines are running. That's Part I.

<div class="callout">
  <span class="tag"><i class="fa-solid fa-lightbulb"></i> Key insight</span>
  <p><b>Every classic SRE principle in this chapter still holds in 2026.</b> Risk dials, error budgets, toil, blameless postmortems, the 50% rule — none of them broke. What changed is <i>who and what does the work</i>, and what "reliable" must now include (judgment + safety, not just uptime). Keep the principles. Upgrade the workforce.</p>
</div>

<div class="callout hot">
  <span class="tag"><i class="fa-solid fa-question"></i> Try it — your first SRE exercise (5 minutes)</span>
  <p>Pick any app you use daily (banking, WhatsApp, your coffee order). Ask: <b>what promise does it make to me?</b> "My transfer lands today." Now guess: what would need to be true for that promise to be kept? Server up? Database consistent? A human awake? An AI model *answering correctly*? You've just written your first SLI and SLO draft. That's the whole job.</p>
</div>

<p><a href="part1/ch01/">Next: Chapter 1 — What Is SRE, Anyway?</a> →</p>