# Attribution Loop — The Substrate Keeps Itself Honest

> *Stub. The closed-loop measurement that makes every other piece falsifiable.*

## The worked example

Q3 wraps. The substrate emits a single page called `Q3 — Alpha Performance`:

| Alpha | Accounts touched | Meetings set | Closed-won | Pipeline | Win rate | Avg ACV | Avg time-to-close vs cold |
|---|---|---|---|---|---|---|---|
| 1 — First PM Hire | 412 | 38 (9.2%) | 6 | $890K | 16% | $148K | -41% (faster) |
| 1.5 — Public CPO 8-K | 67 | 11 (16.4%) | 3 | $620K | 27% | $207K | -22% |
| 4 — Glassdoor | 198 | 8 (4.0%) | 1 | $95K | 13% | $95K | +18% (slower) |
| 7 — PM Team Scaling | 94 | 12 (12.8%) | 4 | $720K | 33% | $180K | -33% |

**Decisions the table forces:**

- Alpha 4 (Glassdoor) is underperforming on win rate and time-to-close — park or rework the copy
- Alpha 1.5 (8-K) is the highest win rate but lowest volume — invest in scaling the source coverage
- Alpha 1 (First PM Hire) is the bread-and-butter — keep running, refine segment-by-segment

No "let me get back to you on this." The math closes the loop.

## The system

```
Every closed deal in CRM
       ↓
Mandatory field: "first-touch trigger" (alpha tag)
       ↓
Mandatory field: "verifiable claim used in first message" (URL)
       ↓
Quarterly aggregation: SUM by alpha → pipeline, win rate, ACV, cycle time
       ↓
Comparison view: each alpha vs. cold baseline + vs. other alphas
       ↓
Surfaced to CRO + CMO + me at quarter end
       ↓
Decisions logged in `bottlenecks/_synthesis.md`
       ↓
Next quarter's resource allocation reflects the decision
```

## The compounding part

After two quarters, the substrate has enough data to start refit:

- Which alpha works best for which industry?
- Which copy variant works best for which funding stage?
- Which trigger type produces deals that close faster vs. close bigger?

Those insights feed back into the alphas as scoring weights. Alpha 1 v2 looks different than Alpha 1 v1, and the difference is grounded in closed-won data, not opinion.

## What this replaces

| Today | With substrate |
|---|---|
| "Where did this deal come from?" answered by gut | Answered by required field at close |
| Marketing attribution platform with first/last-touch debates | One field, agreed upfront, enforced |
| Alpha launches that never get killed | Quarterly kill review, math-driven |
| Insights live in slide decks | Insights live in `bottlenecks/_synthesis.md` and drive next quarter's plan |

## The line

The attribution loop is what separates "I shipped a list" from "I shipped a substrate that knows whether the list worked." That difference is the entire job.
