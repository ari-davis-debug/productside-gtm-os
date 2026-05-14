# `ai-native/` — Deep Dives Into the 7-Step Heuristic

> "AI-native" isn't a feature, it's a shape — the 7-step OS in [`../case-study/02-ai-native-gtm.md`](../case-study/02-ai-native-gtm.md). This folder holds the **deep dives** for four of those steps, where the detail matters too much to live in the overview.
>
> If you're a GTM engineer reading this to apply elsewhere, **the deep dives are the part that generalizes**. The Productside-specific examples are illustrative; the system patterns are what travels.

## How the deep dives map to the heuristic

| Step in the OS | Deep dive page |
|---|---|
| **Step 2** (data + playbooks ingested daily) + **Step 6** (roll out to team) | [`call-intelligence.md`](./call-intelligence.md) — call transcripts flow into the lake, structured signals flow back out to the rep |
| **Step 3** (stakeholders in Claude Code) | [`stakeholder-queries.md`](./stakeholder-queries.md) — three real queries from CEO/CRO/CMO with the SQL views they run on |
| **Step 5** (agentic dev ships solutions) | [`../alphas/`](../alphas/) — the seven CLI alphas the factory stands up |
| **Step 7** (measure → pipeline + revenue) | [`audit-workflows.md`](./audit-workflows.md) — daily funnel-leak detection + auto-enforced kill/park/scale gates |
| **Step 7** (measure → pipeline + revenue) | [`attribution-loop.md`](./attribution-loop.md) — every closed deal closes back to a trigger; the substrate keeps itself honest |

## Why these four deep dives

Steps 1 (repo) and 4 (bottlenecks) are shape, not detail — a folder structure and a file-naming convention are enough. The other five steps are where teams stall when trying to copy this pattern:

- **Step 2** stalls because data engineers want to build the perfect ETL before the GTM team sees any value. The deep dive shows the minimum bar: Airbyte for the boring 80%, custom CLIs for the alpha 20%, ship in week one.
- **Step 3** stalls because executives don't open terminals. The deep dive shows how to land that — three real queries, written down, with the SQL view they run on, so the bar is "run this prompt" not "learn SQL."
- **Step 5** is the alphas, the most context-specific step. The deep dive (the alphas folder) shows seven worked examples; the *derivation pattern* lives at the bottom of [`../case-study/02-ai-native-gtm.md`](../case-study/02-ai-native-gtm.md).
- **Step 7** stalls because attribution is everyone's least favorite work. The two deep dives separate concerns: `audit-workflows.md` is the daily monitor, `attribution-loop.md` is the quarterly review.

## Reading order

If your bottleneck is "we have no signal flow into the company at all" → start with [`call-intelligence.md`](./call-intelligence.md).
If your bottleneck is "leadership doesn't trust the data" → start with [`stakeholder-queries.md`](./stakeholder-queries.md).
If your bottleneck is "we ship campaigns and never know if they worked" → start with [`audit-workflows.md`](./audit-workflows.md) and [`attribution-loop.md`](./attribution-loop.md).
If your bottleneck is "we have no pipeline at all" → start with [`../alphas/`](../alphas/).
