---
title: SRE in the Age of AI
layout: default
---

<div class="hero">
  <span class="kicker"><i class="fa-solid fa-robot"></i> A 2026 rewrite for humans + AI teammates</span>
  <h1>Site Reliability Engineering<br>in the <span class="grad">Age of AI</span></h1>
  <p class="lede">In 2017, Google wrote the book on keeping big systems alive: a pager, a postmortem, and a love affair with automation. Then AI showed up. Code ships 240% faster. Agents curl up in your production lawn. And the person holding the pager is now… a beginner, armed with an AI coworker.</p>
  <p class="lede">This is that book — rewritten for 2026. Cloud-agnostic. Beginner-friendly. Fun on purpose.</p>
  <div class="cta">
    <a class="btn primary" href="{{ site.baseurl }}/book/00-prologue/">Read Chapter 0: From Pager to Prompts</a>
    <a class="btn ghost" href="{{ site.baseurl }}/book/README/">Browse all chapters</a>
  </div>
</div>

<div class="stats">
  <div class="stat"><b>34</b><span>classic chapters analyzed</span></div>
  <div class="stat"><b>18+</b><span>new AI-era chapters</span></div>
  <div class="stat"><b>100%</b><span>cloud-agnostic</span></div>
  <div class="stat"><b>0</b><span>pages of jargon-piling</span></div>
</div>

## Why this book exists

Google's **Site Reliability Engineering** (the "SRE Book") changed how Silicon Valley thinks about uptime. It gave the world four immortal ideas:

1. **Risk is a dial, not a switch.** 100% uptime is a money pit nobody can perceive.
2. **Error budgets.** Spend your allowed failure on what matters: speed.
3. **Toil is a tax.** If a human can do it, a machine should — now literally an AI can.
4. **Postmortems without blame.** Systems fail; learn instead of punishing.

Those ideas survive beautifully. Almost everything *else* has changed.

<div class="callout">
  <span class="tag"><i class="fa-solid fa-bolt"></i> The 2026 reality check</span>
  <p><b>AI coding assistants raised incidents-per-PR by ~243%</b> while incident-response capacity barely moved (2025 DORA study). <b>Gartner projects 70% of enterprises</b> will run agentic AI over their own IT operations by 2029. Agentic SRE tools (Google's SRE AI, Microsoft's Azure SRE Agent, open-source Aurora/K8sGPT/HolmesGPT) now triage alerts, write playbooks, and propose fixes. The new SRE job is less <em>fixing servers by hand</em> and more <em>raising trustworthy AI teammates</em>.</p>
</div>

## What you'll learn here

<div class="cards">
  <div class="card"><div class="emoji">📖</div><h3>The timeless core</h3><p>Every classic SRE idea, translated into plain English with a café-level analogy.</p></div>
  <div class="card"><div class="emoji">🤖</div><h3>The AI frontier</h3><p>AI SRE agents, judgment SLOs, safety SLIs, chaos for agents, and the verification tax.</p></div>
  <div class="card"><div class="emoji">🌥️</div><h3>Cloud-agnostic</h3><p>No Google-only confessional. Works on AWS, Azure, GCP, on-prem, or grandma's potato server.</p></div>
  <div class="card"><div class="emoji">🚀</div><h3>A real roadmap</h3><p>A 90-day, zero-experience path from "what's a server?" to running your first production service.</p></div>
</div>

## The book — chapter by chapter

> **How to read it:** Chapter 0 first. Then Parts 1–3 if you're new (the classic engine, rebuilt). Part 4 is the all-new AI frontier — the chapters that answer "okay, so what *is* SRE in 2026?". Part 5 is culture, Part 6 is your personal roadmap.

<ol class="toc">
  <li><a href="{{ site.baseurl }}/book/00-prologue/">0 · From Pager to Prompts</a><br><small>What SRE was in 2003–2017, what it became by 2026, and why a novice can do it now.</small></li>
</ol>

### Part I — Introduction: the basics for everyone
<ol class="toc" start="1">
  <li><a href="{{ site.baseurl }}/book/part1/ch01/">1 · What Is SRE, Anyway? — The Café Analogy</a><br><small>One question, one metaphor: why an 8-person coffee shop needs less babysitting than a 92% cheaper one.</small></li>
  <li><a href="{{ site.baseurl }}/book/part1/ch02/">2 · The Machine Under the Hood</a><br><small>How modern systems actually work — cloud-agnostic, in plain words, with zero gatekeeping.</small></li>
  <li><a href="{{ site.baseurl }}/book/part1/ch03/">3 · Who Runs the Show: Humans + AI</a><br><small>The 2026 operating crew: humans, deterministic robots, and reasoning agents — and who owns which button.</small></li>
</ol>

### Part II — Principles: the ideas that never get old
<ol class="toc" start="4">
  <li><a href="{{ site.baseurl }}/book/part2/ch04/">4 · Embracing Risk: 100% Reliability Is a Money Pit</a></li>
  <li><a href="{{ site.baseurl }}/book/part2/ch05/">5 · SLOs, SLIs & SLAs: The Measuring Tape of Trust</a></li>
  <li><a href="{{ site.baseurl }}/book/part2/ch06/">6 · Toil: The Soul-Sucking Work AI Should Eat</a></li>
  <li><a href="{{ site.baseurl }}/book/part2/ch07/">7 · Monitoring: Learn to See Your System</a></li>
  <li><a href="{{ site.baseurl }}/book/part2/ch08/">8 · Automation → Autonomy: From Scripts to Self-Driving Ops</a></li>
  <li><a href="{{ site.baseurl }}/book/part2/ch09/">9 · Release Engineering: Shipping Without Fear</a></li>
  <li><a href="{{ site.baseurl }}/book/part2/ch10/">10 · Simplicity: The Art of Doing Less</a></li>
</ol>

### Part III — Practices: the daily habits
<ol class="toc" start="11">
  <li><a href="{{ site.baseurl }}/book/part3/ch11/">11 · Practical Alerting: Make Your Phone Less Dramatic</a></li>
  <li><a href="{{ site.baseurl }}/book/part3/ch12/">12 · Being On-Call (With AI Doing the 3 a.m. Rounds)</a></li>
  <li><a href="{{ site.baseurl }}/book/part3/ch13/">13 · Troubleshooting: CSI for Computers</a></li>
  <li><a href="{{ site.baseurl }}/book/part3/ch14/">14 · Emergency Response & Incident Command</a></li>
  <li><a href="{{ site.baseurl }}/book/part3/ch15/">15 · The Postmortem: An Autopsy Without Blame</a></li>
  <li><a href="{{ site.baseurl }}/book/part3/ch16/">16 · Testing for Reliability & Tracking Outages</a></li>
  <li><a href="{{ site.baseurl }}/book/part3/ch17/">17 · Software Engineering in SRE: Build, Don't Burrow</a></li>
  <li><a href="{{ site.baseurl }}/book/part3/ch18/">18 · Survival Under Load: Balancing, Overload & Cascades</a></li>
  <li><a href="{{ site.baseurl }}/book/part3/ch19/">19 · State, Data & the Consistency Tightrope</a></li>
  <li><a href="{{ site.baseurl }}/book/part3/ch20/">20 · Pipelines & Data Integrity</a></li>
  <li><a href="{{ site.baseurl }}/book/part3/ch21/">21 · The 2026 Launch Checklist</a></li>
</ol>

### Part IV — The AI Frontier: what's genuinely new
<ol class="toc" start="22">
  <li><a href="{{ site.baseurl }}/book/part4/ch22/">22 · Meet Your New Teammate: The AI SRE</a><br><small>What agentic operations are, who's building them, and what they can and can't do (SREGym data included).</small></li>
  <li><a href="{{ site.baseurl }}/book/part4/ch23/">23 · Reliability for AI Systems: MLOps & LLMOps, Without Tears</a></li>
  <li><a href="{{ site.baseurl }}/book/part4/ch24/">24 · Judgment SLOs & Safety SLIs: When "Alive" Is Not Enough</a></li>
  <li><a href="{{ site.baseurl }}/book/part4/ch25/">25 · Observing AI: OTel, Traces and the Euphoria of Tokens</a></li>
  <li><a href="{{ site.baseurl }}/book/part4/ch26/">26 · Chaos for Agents: Break the AI on Purpose</a></li>
  <li><a href="{{ site.baseurl }}/book/part4/ch27/">27 · The Human-in-the-Loop: Trust, Autonomy & Approval Gates</a></li>
  <li><a href="{{ site.baseurl }}/book/part4/ch28/">28 · The Verification Tax: When AI Makes Work, Not Saves It</a></li>
  <li><a href="{{ site.baseurl }}/book/part4/ch29/">29 · Securing the AI Supply Chain & Keeping Agents Honest</a></li>
  <li><a href="{{ site.baseurl }}/book/part4/ch30/">30 · The AI Incident Runbook: Failing Forward</a></li>
</ol>

### Part V — Management & culture in the AI age
<ol class="toc" start="31">
  <li><a href="{{ site.baseurl }}/book/part5/ch31/">31 · Building & Growing an SRE Team in 2026</a></li>
  <li><a href="{{ site.baseurl }}/book/part5/ch32/">32 · Interrupts, Focus & the 50% Engineering Rule</a></li>
  <li><a href="{{ site.baseurl }}/book/part5/ch33/">33 · Communication & Collaboration</a></li>
  <li><a href="{{ site.baseurl }}/book/part5/ch34/">34 · The Evolving SRE Engagement Model</a></li>
</ol>

### Part VI — Your roadmap
<ol class="toc" start="35">
  <li><a href="{{ site.baseurl }}/book/part6/ch35/">35 · The 90-Day Novice-to-SRE Roadmap</a><br><small>Week-by-week: what to learn, what to build, and how to use your AI teammate without becoming its pet.</small></li>
  <li><a href="{{ site.baseurl }}/book/part6/ch36/">36 · Conclusion: Hope Is Not a Strategy, Verification Is</a></li>
</ol>

### Appendix
<ol class="toc" start="A">
  <li><a href="{{ site.baseurl }}/book/appendix/nines/">A · The Nines, Downtime & Budgets Quick Tables</a></li>
  <li><a href="{{ site.baseurl }}/book/appendix/glossary/">B · The Plain-English Glossary (Human & AI Terms)</a></li>
  <li><a href="{{ site.baseurl }}/book/appendix/checklist/">C · The 2026 Production Checklist</a></li>
  <li><a href="{{ site.baseurl }}/book/appendix/map/">D · Chapter Map: Original Book → This Book</a></li>
  <li><a href="{{ site.baseurl }}/book/appendix/postmortem/">E · An Example Postmortem, Written by a Novice + AI</a></li>
</ol>

## Start reading

<div class="callout hot">
  <span class="tag"><i class="fa-regular fa-star"></i> New here? Start here.</span>
  <p>If you read exactly two things: start with <a href="{{ site.baseurl }}/book/00-prologue/">Chapter 0</a> to understand the transformation, then jump to <a href="{{ site.baseurl }}/book/part6/ch35/">Chapter 35</a> to get your 90-day plan. Everything else is a deep dive you can return to.</p>
</div>

<blockquote>
  "Hope is not a strategy." — Old SRE motto (2017).<br>
  "Show me the evidence." — New SRE motto (2026).
</blockquote>