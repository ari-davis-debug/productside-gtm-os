# Audit Workflows — The Quantitative Layer

> *Stub. The "quantitative GTM" piece the JD specifically asked for, made automatic.*

## The worked example

Tuesday morning, 9:00 AM. The CMO opens Slack and sees:

> **#cmo-funnel-watch**
> Daily funnel-leak detector — 2026-05-14
>
> ⚠️ Reply rate on "First PM Hire" alpha dropped 38% vs. trailing 7-day baseline
> Segment driver: domains with Series B funding (vs. Series A) — likely subject-line fatigue at the more-mature segment
> Suggested action: pause variant A for Series B segment, A/B variant C
> Auto-action taken: none (pending CMO approval — threshold > 50% drop for auto-pause)

She approves the action with a thumbs-up react. The campaign self-corrects in 11 minutes.

## The system

Three independent monitors, all running on the same substrate:

### Monitor 1 — Funnel-leak detector

- Daily SQL job comparing each campaign's reply rate, meeting-set rate, and showed-up rate against trailing 7-day baseline
- Segments the drop by every available dimension (industry, headcount band, funding stage, source alpha, copy variant)
- Surfaces the segment driving the drop (not just the aggregate metric)

### Monitor 2 — Kill / park / scale gates

Pre-committed in writing before each campaign goes live:

| Threshold | Auto-action |
|---|---|
| Reply rate < 1% after 200 sends | Auto-pause, alert to Slack |
| Reply rate > 4% after 200 sends | Auto-scale to next segment, alert to Slack |
| Meeting-set < 0.3% after 50 replies | Park, hand back to copy review |

No emotional second-guessing. The system enforces the discipline that was agreed to upfront.

### Monitor 3 — A/B significance flags

- Every campaign runs as A/B by default
- Significance flag flips green at p<0.05 with minimum sample size
- Dashboard never lets you celebrate a winner before the math says so

## What the JD asks for vs. what this delivers

The JD says "use data to find leaks in our funnel." Yes — but the leakage finder runs *itself*, daily, with the segment driver named, with a suggested action, and (above thresholds) with the action already taken. The GTM Engineer's job becomes designing the framework, not running the reports.

## What this replaces

| Today | With substrate |
|---|---|
| Weekly funnel review meeting | Daily auto-detection |
| "Let me pull a report" | Report runs at 9 AM |
| Kill decisions made under deadline pressure | Pre-committed, auto-enforced |
| A/B "winner" called by gut | Significance flag enforces math |
