# `ai-native/` — Deep Dives Into the 7-Step Heuristic

> "AI-native" isn't a feature, it's a shape — the 7-step OS in [`../case-study/02-ai-native-gtm.md`](../case-study/02-ai-native-gtm.md). This folder holds the **deep dives** for four of those steps, where the detail matters too much to live in the overview.

## How the deep dives map to the heuristic

| Step in the OS | Deep dive page |
|---|---|
| **Step 2** (data + playbooks ingested daily) + **Step 6** (roll out to team) | [`call-intelligence.md`](./call-intelligence.md) — call transcripts flow into the lake, structured signals flow back out to the rep |
| **Step 3** (stakeholders in Claude Code) | [`stakeholder-queries.md`](./stakeholder-queries.md) — three real queries from CEO/CRO/CMO with the SQL views they run on |
| **Step 5** (agentic dev ships solutions) | [`../alphas/`](../alphas/) — the seven CLI alphas the factory stands up |
| **Step 7** (measure → pipeline + revenue) | [`audit-workflows.md`](./audit-workflows.md) — daily funnel-leak detection + auto-enforced kill/park/scale gates |
| **Step 7** (measure → pipeline + revenue) | [`attribution-loop.md`](./attribution-loop.md) — every closed deal closes back to a trigger; the substrate keeps itself honest |

## Why the deep dives matter

The overview tells you "stakeholders type questions, get answers in twelve seconds." The deep dive shows you the actual SQL view it ran. That's the difference between "AI-native is the shape of the future" and "here is exactly the thing I would build on Monday."

If you're skimming, read [`../case-study/02-ai-native-gtm.md`](../case-study/02-ai-native-gtm.md). If you want to verify the claims, read these.

## What's *not* in this folder

- The alphas themselves — those are in [`../alphas/`](../alphas/) because they're the Step-5 deep dive
- Step 1 (repo) and Step 4 (bottlenecks) — those don't need a deep dive separate from what the live scaffold already shows in [`../example-productside-gtm/`](../example-productside-gtm/)
