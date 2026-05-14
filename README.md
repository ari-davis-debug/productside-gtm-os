# Productside GTM OS — Case Study

> A leave-behind portfolio piece for the Productside (formerly 280 Group) GTM Engineer interview. Same shape as the [Mento case study](../mento-case-study/), specialized to a B2B product-management training business. **Pure public-data alphas — zero proprietary access required.**

## 👉 If you only have 5 minutes, click these 3 files

1. **[`case-study/00-the-frame.md`](./case-study/00-the-frame.md)** — why pure-external alphas for a training company, and what changes about outbound when the buyer is a VP of Product (not a CFO)
2. **[`alphas/01-first-pm-hire-cocktail.md`](./alphas/01-first-pm-hire-cocktail.md)** — THE alpha, fully built. LinkedIn JD × Crunchbase funding × BuiltWith. ~150 hand-raise accounts per quarter from public data alone.
3. **[`case-study/02-ai-native-gtm.md`](./case-study/02-ai-native-gtm.md)** — what "AI-native go-to-market" actually means when the CEO can query her own pipeline in 12 seconds

Those three files show the pattern in 5 minutes. Everything else is supporting structure.

## Why this exists

Productside posted a GTM Engineer role. The job description reads like a list of motions (Lemlist + HubSpot integration, AI lead scoring, conversation intelligence, email infra, funnel quant). Most candidates respond with a deck.

This repo responds with **the substrate underneath those motions** — what gets built, what data feeds it, and what becomes possible when leadership can query it directly. Same architecture I've been running for the last four years; same architecture I'm scoping right now for a comp-tech client (`mento-case-study/`).

## Tour map

| Folder | What's in it |
|---|---|
| **[`case-study/`](./case-study/)** | The narrative: frame → 7 alphas → AI-native layer → week-one plan |
| **[`alphas/`](./alphas/)** | One file per alpha, each answering: trigger, sources, join logic, CLI sketch, sample message, expected throughput |
| **[`ai-native/`](./ai-native/)** | What changes when stakeholders open Claude Code against their own data — stakeholder queries, call intelligence, funnel audits, attribution |
| **[`gtm-os/`](./gtm-os/)** | The 7-step OS pattern (referencing Mento's), specialized for a training co |
| **[`example-productside-gtm/`](./example-productside-gtm/)** | Click-around scaffold of the live repo this would become — same shape as `example-mento-gtm/` |

## What this is NOT

- **Not a deck.** A deck signals "I prepared a pitch." A repo signals "I'm already a teammate."
- **Not a Productside-internal anything.** Every signal, every join, every message draws on public data. I deliberately stayed away from any speculation about Productside's CRM, LMS, or alumni database.
- **Not finished.** Status is `emergent` — the alphas are real, the AI-native layer is mapped, but the live scaffold is a sketch. The interview is the validation step.

## Related

- [`internal/ideas/productside-interview-alphas.md`](../../ideas/productside-interview-alphas.md) — the working node these files build from
- [`internal/services/mento-case-study/`](../mento-case-study/) — the shape this is patterned on
- `exports/productside-loom-reference.md` — the prior work proving the pattern ($4–5M pipeline from federal data)
