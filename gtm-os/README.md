# `gtm-os/` — The 7-Step OS, Specialized

> The 7-step Go-To-Market Operating System pattern, adapted for Productside. The canonical version lives in [`internal/services/mento-case-study/gtm-os/`](../../mento-case-study/gtm-os/). This folder documents the deltas, not the whole framework.

## What's the same

All seven steps from the Mento case study apply unchanged in shape:

1. Stand up the repo
2. Data + playbooks ingested daily
3. Stakeholders in Claude Code
4. Capture + prioritize bottlenecks
5. Agentic dev to ship solutions
6. Roll out to the team
7. Measure → pipeline and revenue

## What's different for a training company

| Step | Productside-specific delta |
|---|---|
| 1 | Repo includes an `alumni/` folder; alumni is a first-class data type, not just a contact in CRM |
| 2 | Data plane includes LMS/cert data + alumni cohort tags + course-completion records — none of which the alphas need on day one, but all of which become multipliers post-week-one |
| 3 | Stakeholders include the Head of Curriculum + the Head of Enterprise — both query the substrate differently than CEO/CRO/CMO |
| 4 | Bottlenecks specific to training co: alumni-to-enterprise conversion, cohort-to-cohort referral, rebrand-decay capture |
| 5 | First build is one of the seven alphas (likely Alpha 1) — not a generic signal workflow |
| 6 | Enterprise reps + individual-course advisors get *different* slash-commands — one is selling private training, the other is selling courses |
| 7 | Attribution loop must distinguish LTV-by-motion: alumni who buy individual courses now → buy private training in 18 months is a real, measurable path |

## Why this folder is short

The pattern is universal. The specialization is light. If a reader wants the full 7-step explanation, they go to the Mento case study. This folder exists so the differences are explicit and locatable.

## Reference

- [`internal/services/mento-case-study/gtm-os/`](../../mento-case-study/gtm-os/) — canonical 7-step writeup
- [`../case-study/02-ai-native-gtm.md`](../case-study/02-ai-native-gtm.md) — Step 3 in detail for Productside
- [`../example-productside-gtm/`](../example-productside-gtm/) — what Steps 1, 2, 4 look like as a live scaffold
