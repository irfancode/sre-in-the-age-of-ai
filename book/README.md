---
title: All Chapters — SRE in the Age of AI
layout: default
---

# The Book

**SRE in the Age of AI** keeps every idea worth keeping from Google's classic *Site Reliability Engineering* (2017), updates the ones time has changed, and adds a whole new wing for the AI era.

**Reading level:** a curious high-schooler with no IT background can follow every chapter. Analogy-first, jargon-second. When a term really can't be avoided, it's in [the glossary[appendix/glossary.html].

## The Authenticity Audit

Before writing a word, this project audited all **9 parts / 34 chapters / 6 appendices** of the original book against 2026 reality: current research, market data, vendor behavior, and a decade of production lessons from the cloud-native world. Here is the verdict per chapter.

### Original book → this book

| # | Classic chapter (2017) | Verdict for 2026 | Where it lives now |
|---|---|---|---|
| Foreword/Preface | Framing | **Updated** | [Chapter 0[00-prologue.html] |
| 1 | Introduction | **Updated** (still true, new tools) | [Chapters 1–3[part1/ch01.html] |
| 2 | Production environment at Google | **Replaced** with a cloud-agnostic tour | [Chapter 2[part1/ch02.html] |
| 3 | Embracing Risk | **KEEP — timeless** | [Chapter 4[part2/ch04.html] |
| 4 | Service Level Objectives | **KEEP — timeless**, extended for AI "judgment" | [Chapter 5[part2/ch05.html] + [Chapter 24[part4/ch24.html] |
| 5 | Eliminating Toil | **Updated** — AI is the new toil-eater (and toil-maker) | [Chapter 6[part2/ch06.html] |
| 6 | Monitoring Distributed Systems | **Updated** — anomaly detection + OTel + AI triage | [Chapter 7[part2/ch07.html] + [Chapter 25[part4/ch25.html] |
| 7 | Evolution of Automation | **Updated** — automation is now *autonomy* | [Chapter 8[part2/ch08.html] |
| 8 | Release Engineering | **Updated** — AI-assisted code at 243% velocity | [Chapter 9[part2/ch09.html] |
| 9 | Simplicity | **KEEP — more important than ever** | [Chapter 10[part2/ch10.html] |
| 10 | Practical Alerting | **Updated** — AI writes + triages alerts | [Chapter 11[part3/ch11.html] |
| 11 | Being On-Call | **Updated** — AI on the 3 a.m. shift | [Chapter 12[part3/ch12.html] |
| 12 | Effective Troubleshooting | **Updated** — AI first responders | [Chapter 13[part3/ch13.html] |
| 13 | Emergency Response | **Updated** — agentic orchestration | [Chapter 14[part3/ch14.html] |
| 14 | Managing Incidents | **KEEP** + AI layer | [Chapter 14[part3/ch14.html] |
| 15 | Postmortem Culture | **KEEP — timeless** | [Chapter 15[part3/ch15.html] |
| 16 | Tracking Outages | **Updated** | [Chapter 16[part3/ch16.html] |
| 17 | Testing for Reliability | **KEEP** + chaos for agents | [Chapter 16[part3/ch16.html] |
| 18 | Software Eng in SRE | **KEEP** — now it means AI tooling too | [Chapter 17[part3/ch17.html] |
| 19–20 | Load Balancing | **KEEP** (cloud-agnostic rewrite) | [Chapter 18[part3/ch18.html] |
| 21–22 | Overload & Cascading Failures | **KEEP** — agents add *new* cascade modes | [Chapter 18[part3/ch18.html] |
| 23 | Managing Critical State | **KEEP** — same physics, new clouds | [Chapter 19[part3/ch19.html] |
| 24 | Distributed Scheduling (Cron) | **Updated** — AI crons & agents as cron-sitters | [Chapter 19[part3/ch19.html] |
| 25 | Data Processing Pipelines | **Updated** — now GPU and token pipelines | [Chapter 20[part3/ch20.html] |
| 26 | Data Integrity | **KEEP — timeless** | [Chapter 20[part3/ch20.html] |
| 27 | Reliable Product Launches | **Updated** — LLM launches, model releases | [Chapter 21[part3/ch21.html] |
| 28 | Accelerating SREs to On-Call | **Updated** | [Chapter 31[part5/ch31.html] |
| 29 | Dealing with Interrupts | **Updated** — AI interrupts the interrupters | [Chapter 32[part5/ch32.html] |
| 30 | Embedding SRE to Recover | **KEEP** | [Chapter 34[part5/ch34.html] |
| 31 | Communication & Collaboration | **KEEP + AI teammates** | [Chapter 33[part5/ch33.html] |
| 32 | Evolving SRE Engagement Model | **Updated** — "SRE for AI" and "AI for SRE" | [Chapter 34[part5/ch34.html] |
| 33 | Lessons from Other Industries | **KEEP** — aviation's AI lesson added | [Chapter 33[part5/ch33.html] |
| 34 | Conclusion | **Updated** | [Chapter 36[part6/ch36.html] |
| Appx A–F | Tables, checklists | **Updated** | [Appendix](appendix/) |

### The verdict, summarized
- **~40% KEEP as-is** — the SRE *principles* (risk, SLOs, toil, postmortems, simplicity) are laws of physics, not fashion.
- **~40% UPDATED** — same idea, new tools: AI triages, agents sleep-wearily through on-call, models need release pipelines.
- **~20% genuinely NEW** — chapters the 2017 book couldn't have written: agent not AWS, judgment SLOs, safety SLIs, chaos for LLMs, the verification tax, and the novice roadmap.

## How to read it

| You are… | Read this path |
|---|---|
| A complete newbie | Part I (1–3) → Part II (4–10) → skim Part III → **Part IV (22–30)** → Part VI (35–36) |
| A veteran SRE | Chapter 0 → **Part IV (22–30)** → Part V (31–34) → skim the rest for fun |
| A manager / founder | Chapter 0 → Chapters 4–6, 22, 27, 28, 31, 35 |
| A student curious about careers | Chapter 0 → Chapters 1, 22–24, 35–36 |

<a class="btn primary" href="00-prologue/">Start with Chapter 0</a> <a class="btn ghost" href="../../">Back to the blog</a>