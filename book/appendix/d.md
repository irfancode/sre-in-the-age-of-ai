---
title: "Appendix D — The Incident-State Document (the AI-era 'Dashboard of Record')"
layout: default
---

<div class="chapter-meta"><b>Original:</b> Chapter 14's Appendix C (launch / incident docs) + the empty-page habit. <b>Verdict:</b> KEEP — now the machine's memory and the human's truth. <b>Reading time:</b> 5 minutes.</div>

# Appendix D — The Incident-State Document

This is Chapter 14's "incident dashboard" — the living, shared, single-pane-of-glass doc that says *what's broken, who's working it, what's next, what's been tried, and what the receipts are.* Its rules — open a blank page and *write* on the very first minute, never fall in love with the dashboard over the field — are the eternal law. All chapters in [Part IV[part4/ch22.html] hang on it as their spine.

## The spine: sections, in order, always

```markdown
# INCIDENT: <one-line title>   |   IC: <name>   |   SEV: <P1/P2>
## Timeline (receipts, not vibes)        ← the living Chapter 6/9 record
## What's broken (users' words)
## Current hypothesis + confidence       ← the agent drafts, human adjudicates (Ch 22-24)
## Tried / in-flight / next
## Open questions
## Autonomy state: what the agents may/may not do right now (Ch 24, 29)
## Comms: who said what to whom, when    ← the scribe owns this (Ch 30-33)
```

## Why the doc is the *machine's memory* in 2026

The 2026 twist: this document is not just read by humans — **it is the file the agents read and write** (with receipts + human gates, Chapters 22–29). Consequences:

1. **It must have receipts.** Every "we tried X" needs its artifact link (logs, traces, replay, command output). A claim without a receipt is a hypothesis, not a fact (Chapters 6, 27, 29).
2. **It must be machine-readable AND human-legible.** Structured sections (above) so the agents parse it; plain-language titles so humans skim it. Both audiences share *one* document — never two — or the two drift and that drift is a reliability bug (Chapters 22, 32, 33).
3. **It is the replay target.** After the incident, the agents replay their approved actions against the doc (Chapters 29). If the doc is complete, the replay is cheap; if it's gutted, the replay *is* the postmortem (Chapter 28).
4. **The doc gates autonomy.** In [Chapter 24[part4/ch24.html]'s autonomy ladder, the "current autonomy state" block is what the leash checks. Update it *first* when the incident changes character.

<div class="callout">
  <span class="tag"><i class="fa-solid fa-lightbulb"></i> Key insight</span>
  <p><b>The incident doc is where the human-made and machine-made reliability meet and are reconciled.</b> It does not make incidents boring — it makes them <i>rehearsable</i> [Ch 12[part3/ch12.html], and every chapter in Part IV exists to keep this one document honest at scale.</p>
</div>

<p><a href="appendix/e-postmortem/">Next: Appendix E — Postmortem: The Template That Outlives the Machines</a> →</p>