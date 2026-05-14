# 02 — AI-Native Go-to-Market

> *Stub. Fills in step 2 of the build plan. The differentiator — what most "GTM Engineer" candidates won't talk about.*

## What goes here

The frame: **most GTM Engineers ship lists. The AI-native version ships the substrate where leadership becomes the GTM Engineer.**

Lists are commodity. The substrate is the moat. The substrate is what compounds.

## The four pillars of AI-native GTM (to flesh out)

Each pillar gets a sub-page in [`../ai-native/`](../ai-native/). This page is the overview.

### 1. Stakeholders in Claude Code (Mento OS Step 3)

Detail: [`../ai-native/stakeholder-queries.md`](../ai-native/stakeholder-queries.md)

The CEO, CRO, and CMO each open Claude Code and ask questions against the GTM substrate directly. Worked examples:

- **Rina** types `which alumni from 2022–2024 cohorts work at public companies that filed an 8-K appointing a new CPO this quarter?` → answer in 12 seconds with the SQL view it ran on
- **CRO** types `show me win-pattern signatures across our last 200 closed-won enterprise deals` → ranked correlate table
- **CMO** types `what content gap shows up across our top 50 lost-to-no-decision deals?` → quoted excerpts from call transcripts

No tickets to data analysts. No "let me get back to you Thursday." The query loop closes inside the meeting.

### 2. Call intelligence as a system, not a feature

Detail: [`../ai-native/call-intelligence.md`](../ai-native/call-intelligence.md)

Trellus and Avoma (named in the JD) record calls. **The system around them** is what matters:

- Transcripts ingested via Fireflies + Claude API
- Risk signals extracted (champion change, pricing concern, competitor mention, decision-criteria shift)
- CRM fields auto-updated per signal taxonomy
- Slack alerts on configurable triggers (`"@cro alert: champion at AcmeCo just used the word 'pause' three times in one call"`)
- Win/loss pattern aggregation runs weekly and feeds back into ICP refit

### 3. Funnel audit workflows

Detail: [`../ai-native/audit-workflows.md`](../ai-native/audit-workflows.md)

Quantitative GTM work the JD asked for, made AI-native:

- Daily funnel-leak detector: where is conversion dropping vs. trailing 7-day baseline, and which segment is dragging?
- Pre-committed kill/park/scale gates per campaign — automated state transitions
- Control-group A/B framework with statistical significance flags built into the dashboard
- The CMO can ask `is the 'first PM hire' alpha outperforming the 'public CPO' alpha on meeting rate this quarter?` and get the answer

### 4. Closed-loop attribution

Detail: [`../ai-native/attribution-loop.md`](../ai-native/attribution-loop.md)

Every deal closes back to a trigger. Every trigger maps to an alpha. Every alpha gets a quarterly read on pipeline contribution × win rate × ACV × time-to-close vs. cold baseline. The substrate keeps itself honest.

## The line

> *"Most GTM Engineers ship lists. I ship the substrate where your CEO can ask 'which alumni work at companies that just hired their first CPO' and get an answer in 12 seconds. That compounds. A list doesn't."*

## TODO when filling

- Open with the lists-vs-substrate distinction
- One worked example per pillar (the queries above are real — flesh out the SQL view each one runs on)
- Tie back to the JD's specific phrasing: AI-driven lead scoring, call summarization, recruiting workflow improvements
- Close with the line above
