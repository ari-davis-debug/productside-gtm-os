# Call Intelligence — Trellus / Avoma, Systematized

> *Stub. The JD named Trellus and Avoma. This page shows what the system around them looks like.*

## The worked example

A discovery call ends. 30 minutes after the recording stops, the CRM looks like this:

- **Account record**: Risk score updated from 2.3 → 3.8 (red zone)
- **Reason field auto-populated**: "Champion used 'pause' 3× in last 10 minutes; mentioned 'budget review' once."
- **Slack alert in #cro-room**: "@cro alert: champion at [Co] just used 'pause' three times — recording: [link]"
- **Comparison field**: "Reforge" mentioned twice (not in prior calls) → competitive intel flagged
- **Next-step suggestion** drafted in HubSpot: "Pre-empt the pause: send the ROI worksheet before EoW. Reference [prior call quote]."

The rep sees all of this in their morning queue. They didn't write any of it.

## The system

```
Trellus / Avoma  →  raw transcript
       ↓
Fireflies + Claude API  (replicable on either stack, named for stack alignment)
       ↓
Extractor pipeline (Trigger.dev, parallel agents):
  - Risk signal extractor (champion change, pause-language, decision-criteria shift)
  - Competitive mention extractor
  - Pricing concern extractor
  - Champion sentiment scorer
       ↓
CRM field writer (HubSpot/Salesforce API)
       ↓
Slack alert router (per-signal channel routing)
       ↓
Weekly aggregator → win-pattern delta dashboard
```

## The four extractors (to flesh out)

1. **Risk signals** — taxonomy of 12 risk patterns, scored 0–1 per call, threshold-triggered
2. **Competitive mentions** — named-entity extraction tuned to PM-training space (Reforge, Pragmatic, Product School, internal L&D)
3. **Pricing concerns** — quote-level capture, attached to deal record
4. **Champion change** — speaker-diarization aware; new attendee + senior title = potential champion shift

## Weekly aggregation

Every Friday, the system runs a query: "Across all calls this week, what's the delta vs. trailing 8 weeks in each signal category?" Answer goes to the CRO + CMO as a 5-bullet email. Patterns become product feedback (CMO acts on competitive mentions; CRO acts on champion changes).

## What this replaces

| Today | With substrate |
|---|---|
| Rep listens to own calls, maybe | Auto-extracted, auto-routed |
| Manager listens to 1 in 20, randomly | Weekly delta surfaces what to listen to |
| Competitive intel lives in someone's head | Quantified, dashboard-tracked |
| Champion change discovered at the deal-loss debrief | Discovered the day it happens |

## What the JD asks for vs. what this delivers

JD says "AI-driven call summarization." That's the table-stakes version. This page is the version that closes the feedback loop into pipeline.
