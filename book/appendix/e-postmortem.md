---
title: "Appendix E — Postmortem: The Template That Outlives the Machines"
layout: default
---

<div class="chapter-meta"><b>Original:</b> Appendix C · Postmortem template (Chapter 12). <b>Verdict:</b> KEEP — plus the AI-scribe draft columns. <b>Reading time:</b> 8 minutes (or 4 if you let the agent draft it).</div>

# Appendix E — Postmortem: The Template That Outlives the Machines

Use this with [Chapter 12[part3/ch12.html] (culture) and [Chapter 28[part4/ch28.html] (the AI-era postmortem with receipts + verification-tax accounting). The macros are the original's; the `[AI]` rows are this edition's addition — what the scribe can draft *draft* and the human must *own*.

## The template (fill it so someone who was not there can see it)

```markdown
# Postmortem: <TITLE>

**Incident:** <date, time range, Sev>     **Leads:** <human IC + AI scribe listed>
**Impact:** <real user numbers: users affected, requests/inbound lost, money/trust at risk (Ch 4, 15)>  [AI: draft from incident doc]
**Summary (TL; DR):**

## What happened (the timeline)
| Time | Event | Evidence(receipt) link | Notes |
|------|-------|------------------------|-------|
|      |       | [logs/…]                |       |
[AI: populate from receipted timeline (Ch 6, 9, 25); human corrects the "why was this a surprise" column]

## Impact & severity
- Blast radius (users, regions, dependencies) at stage 1 vs. after each containment step [Ch 9, 31]
- Error budget consumed / still burning [Ch 5, 7, 15]

## Root cause(s)
> We kept saying "root cause." There are usually several. List them, and for each: evidence + why-that-was-believed + what allowed it to slip [Ch 12, 28].

## What went well / what went wrong — *for the whole crew, human + machine* [Ch 28, 30-33]
| Aspect | Human | AI scribe / agent |
|--------|-------|-------------------|
| Detection | | [drafted dossier quality - Ch 22, 25] |
| Response | | [action correctness + approval discipline - Ch 24, 29] |
| Communication | | [draft accuracy; no hallucinations in comms - Ch 32-33] |

## The blameless close
> We did not fix blame; we fixed the *system* that made this plausible. [Ch 12]

## Action items — the receipts rule [Ch 12, 27, 28]
- [ ] VERIFIED after action (not just "done"): <owner> <due> <replay link if applicable>
- [ ] AI-relevant: was the autonomy ladder[^a] respected? [Ch 24, 29] <owner> <due>
- [ ] A15: would an agent (yours or honest) have caught this? [Ch 22, 31-33]

[^a]: nines/d tables, Appendix A.
```

## The 2026 rule to laser-cut above the template

> **The postmortem is the artifact that outlives the machine that helped draft it.** Today's agents can draft 80% of this in minutes — the other 20% is *the human judgment about "why are we like this"* — and the *receipts* (Chapters 6, 9, 28) are what prevent the draft from drifting into fiction. Keep the template, keep the receipts, keep the blamelessness. The machines improve; the discipline endures.

<div class="callout">
  <span class="tag"><i class="fa-solid fa-lightbulb"></i> Key insight</span>
  <p><b>A postmortem you can't attach a receipt to is a eulogy.</b> In the AI era the scribe drafts the evidence-first draft; the human writes the <i>learning</i> and owns the <i>verification</i> — and the replay discipline (Chapters 29, 12) turns the template from a diary into a rehearsed muscle.</p>
</div>

<p><a href="README/">← Back to the book's anchor</a> · <a href="appendix/further/">Next: Appendix F — Further Reading: The 2026 Shelf</a> →</p>