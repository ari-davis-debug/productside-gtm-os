# Alpha 7 — PM Team Scaling Signal

> *Stub. Fill in step 5.*

## 1. The trigger

A company's PM headcount has grown 20%+ YoY AND has 3+ open PM JDs simultaneously. Scaling a PM org from 5 to 10 (or 10 to 20) is when the framework gap shows up. Five PMs can wing it. Twenty cannot.

## 2. Public data sources stitched

- **LinkedIn headcount delta by department** — PM count quarter-over-quarter
- **LinkedIn job postings** — open PM JD count, by company
- **Crunchbase** — funding stage filter (companies that can afford private team training)

## 3. Primary key + join logic

- Key: company domain
- Filter: PM headcount up 20%+ YoY AND ≥3 currently-open PM JDs AND total PM headcount ≥7 (below 7, individual training is the better fit; at 7+, team training kicks in)
- Score: rate of growth × current open JDs × ACV potential (proxied by total company headcount)

## 4. CLI build sketch

- LinkedIn headcount-delta tracker (reuse existing scraper, just aggregate by department) — 1 day
- JD count aggregator (reuse Alpha 1's scraper) — 0 days marginal cost
- Quarterly refresh

## 5. Sample message with the verifiable claim

> **Subject**: [Co]'s PM team grew [N]% in the last 12 months
>
> Hey [VP Product / Head of Product],
>
> Tracking your PM headcount: up from [X] to [Y] over the last 12 months, with [Z] open PM roles currently posted. That's the inflection point where most PM orgs we work with admit "we need a shared framework" — five PMs can align around a hallway conversation, fifteen need a documented practice.
>
> Productside's private team training is built for exactly this scaling moment. Eight weeks, on-site or hybrid, curriculum tailored to your stage. Worth a 20-minute scoping call?
> — Ari

## 6. Expected throughput + cost to build

- ~80–120 companies per quarter hit all three filters
- Build cost: 1 day (everything reuses Alpha 1 components)
- Decay rate: quarterly — re-run each quarter against the same universe
