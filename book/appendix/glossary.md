---
title: "Appendix B — Glossary: The Language of Reliability in the AI Age"
layout: default
---

<div class="chapter-meta"><b>Original:</b> Appendix B · Glossary (Google Cloud Intro). <b>Verdict:</b> KEEP + the AI-era coinages. <b>Reading time:</b> 6 minutes. Keep it on the desk; the machines keep a machine-readable copy that is the source of truth, and note: in 2026 most *teams* read this glossary via their agent, which is why every term is written to be unambiguous — markdown the LLM can shake hands with.</div>

# Appendix B — Glossary: The Language of Reliability in the AI Age

The SRE lexicon, 2026 edition. A `*` means the term is newly coined or significantly reloaded for the AI era — read those especially, because the machines you hire now speak this dialect natively. Terms marked **heading-only** are in the book proper.

- **Agent** — a program that plans, acts, observes, and learns — an LLM as reasoning engine + your tools as its hands (Ch 22–24).
- **AI SRE / AI first-responder** — the agent that answers your pages and drafts dossiers (Ch 22, 26).
- **AI scribe** — the agent that keeps the living timeline and minutes in incidents (Ch 33).
- **Autonomy budget** — the error-budget twin for machines: how much *irreversible* action an agent may take per unit time, funded by verification evidence (Ch 24).
- **Autonomy ladder** — the 5-rung gate: observe → suggest → act-with-approval → act-within-guardrails → full autonomy. Autonomy is earned, never installed (Ch 27).
- **Blameless postmortem** — review that names system/process causes, not people, so signals survive (Ch 12, 28).
- **Capacity planning** — estimating when you run out; 2026: *tokens, agents*, and GPUs are now capacity (Ch 14).
- **Cascade / cascading failure** — one failure that fans out through shared dependencies (Ch 21).
- **Dossier** — the agent's evidence-backed incident brief: what broke, what it hit, hypotheses with confidence, proposed steps, receipts (Ch 22, 26).
- **Error budget** — 100% − availability target; the allowed-unreliability ledger (Ch 4–5, 7).
- **Evals / evaluation suite** — the automated tests for your agents (Ch 23, 25; Appendix C & D).
- **Gap** — the quality/safety gap between too strict and too loose; the agent-metrology ideal (Ch 26).
- **Golden signals** — latency, traffic, errors, saturation (Ch 4).
- **Incident commander (IC)** — coordinates, doesn't hero; owns process, forever (Ch 30).
- **Judgment SLI** — the 2026 sensor that measures your *team's* review-override behavior and trust thresholds (Ch 22, 26).
- **LLM/SRE crew** — the humans + machines that co-run production (Ch 21–22, 31).
- **Model (reliability = context)** — your error budget *is* the window in which you can model the future (Ch 15).
- **On-call** — the rotated responsibility for protecting the user (Ch 11, 32).
- **Playbook / runbook** — the rehearsed steps that are the machine's train and the human's rental (Ch 9, 22).
- **Postmortem** — evidence-based review after an incident (Ch 28).
- **Pre-mortem** — rehearse failure before it happens (Ch 1, 30).
- **Receipts** — the artifact-everything evidence layer: logs, traces, replay videos, citations (Ch 9, 28).
- **Rollback** — machine-fast, rehearsed, and the 2026 "roll forward or roll back" decision is your cleanest autonomy question (Ch 29).
- **Root cause** — what must change so this won't happen again; 2026: machine-crafted, human-adjudicated (Ch 28).
- **Runbook** — see **Playbook**.
- **Shadowing** — the trainee follows an experienced SRE (or now, an authorized agent) before flying (Ch 31, 36).
- **SLO / SLI / SLA** — Service-Level Objective / Indicator / Agreement (Ch 4–6, 15).
- **SRE (Site / Systems / Service Reliability Engineering)** — engineering aimed at reliability *as a product feature*; the discipline this whole book is about (Ch 1).
- **Toil** — the manual, repetitive, automatable work that scales linearly with load, slightly faster (Ch 6, 28-white: see also **verification tax**).
- **Verification tax** — the new toil created when humans must verify machine output at scale (Ch 26, 28).
- **Window (of reliability)** — the classic "very much intended and all the better": the human-judgment description of what your error budget buys you (Ch 15).

## The one-liner to memorize

> **SRE is what happens when you treat reliability as a feature that you can budget, engineer, and — now — *verily co-engineer with machines.***

<p><a href="c-map/">Next: Appendix C — Map of the Book (Original Chapter → This Edition)</a> →</p>