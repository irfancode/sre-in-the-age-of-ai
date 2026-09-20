---
title: "Appendix A — The Nines & Error Budget Quick Tables"
layout: default
---

<div class="chapter-meta"><b>Original:</b> Appendix A · Availability Table. <b>Verdict:</b> KEEP — plus the AI-era autonomy budget rows. <b>Reading time:</b> 3 minutes.</div>

# Appendix A — The Nines & Error Budgets Quick Tables

## The classic downtime table (print it, frame it)

| Availability | Downtime / year | Downtime / quarter |
|---|---|---|
| 99% | 3.65 days | 21.9 hours |
| 99.9% | 8.77 hours | 2.19 hours |
| 99.95% | 4.38 hours | 1.10 hours |
| 99.99% | 52.6 minutes | 13.2 minutes |
| 99.999% | 5.26 minutes | 1.3 minutes |
| 99.9999% | 31.6 seconds | ~8 seconds |

**Read it as:** the last few nines cost orders of magnitude more effort for *minutes* — so pair the table with [Chapter 4](part2/ch04/)'s "which nines do we actually need?" question before you fall in love with a big number.

## The error-budget math (one line)

```
error budget = (1 − availability target)
burn rate      = error-budget consumption / time    → > 1 × for too long = fix (Ch 6)
golden window  = budget / expected burn             → pages you before the quarter dies
```

## 2026 addition — the autonomy budget ladder (the AI-era companion table)

| Rung | What the machine may do | Evidence required |
|---|---|---|
| 1 · Observe | Read, watch, summarize | scoped read access, receipts |
| 2 · Suggest | Draft hypothesis + runbook / "[Chapter 29](part4/ch29/)" | human confirms, no actions |
| 3 · Act with approval | Execute *proposed* steps, human-clicked | approval gate + ledger [Ch 8](part2/ch08/), [24](part4/ch24/) |
| 4 · Act within guardrails | Autonomous within a **[playbook](appendix/playbook/)** + **[leash](part4/ch29/)** | safety SLI green, rehearsal-proof, replay-ready [Ch 26](part4/ch26/) |
| 5 · Full autonomy | Nothing irreversible without a human-joint launch review | years of receipts; still no takedown power alone [Ch 27](part4/ch27/), [29](part4/ch29/) |

**Same physics as the nines:** define *trusted autonomy budget* like error budget — and spend it like the cash it is ([Chapters 5, 7, 24](part2/ch05/)).

<div class="callout">
  <span class="tag"><i class="fa-solid fa-lightbulb"></i> Key insight</span>
  <p><b>The nines never left; they just got a 2026 companion.</b> You would not "deploy nine 9s" without the evidence — and you should not "deploy rung-5 autonomy" without the same discipline. Budget and evidence are the shared language across both tables; trust the ledger, and the ladder stays honest.</p>
</div>

<p><a href="appendix/glossary/">Next: Appendix B — Glossary</a> →</p>