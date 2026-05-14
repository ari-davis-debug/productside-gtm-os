# GTM Alphas via the 7-Step OS — Worked on Productside

> **A playbook for GTM engineers.** How to walk into any go-to-market role on day one, hook your data plane (HubSpot, LinkedIn, call transcripts) into a queryable substrate via Airbyte, run those call transcripts through the 7-step OS to derive *alphas* — public-data wedges that beat generic outbound — and ship the substrate that makes leadership query the GTM directly. Productside (formerly 280 Group) is the worked example. The methodology transfers to anywhere.

## What this repo actually is

Two things, in this order:

1. **A transferable methodology** — the 7-step OS plus the alpha-derivation pattern. A GTM engineer who reads this should be able to apply it to a comp-tech company, a fintech, a vertical SaaS, an ad agency — anything with a CRM and a pipeline.
2. **One worked example** — Productside. Seven concrete alphas, four AI-native deep-dives, all pure public data. Specific enough to be falsifiable, generic enough that the *shape* is the lesson.

If you are interviewing for a GTM Engineer role: read [`case-study/02-ai-native-gtm.md`](./case-study/02-ai-native-gtm.md) first. That's the spine.

## 👉 The 5-minute path

1. **[`case-study/00-the-frame.md`](./case-study/00-the-frame.md)** — why pure-external alphas, why a 7-step OS, why "AI-native" without the substrate is theater
2. **[`case-study/02-ai-native-gtm.md`](./case-study/02-ai-native-gtm.md)** — the 7-step OS, with worked Productside examples per step; alphas explicitly slotted into Step 5
3. **[`alphas/01-first-pm-hire-cocktail.md`](./alphas/01-first-pm-hire-cocktail.md)** — one alpha fully built (SQL, CLI sketch, sample message, throughput math) as the reference template for the other six

Those three files give you the methodology + one worked alpha in 5 minutes.

## How the methodology generalizes

The 7-step OS is the shape. Any GTM engineer onboarding to a new role should expect to:

| Step | What to do day one | What you'll need |
|---|---|---|
| 1 | Stand up a repo with `foundation/`, `sql/`, `accounts/`, `bottlenecks/`, `CLAUDE.md` | Git, Supabase, an account on Claude Code |
| 2 | Pipe HubSpot + LinkedIn + call transcripts into the lake daily | **Airbyte** (or Fivetran, or a custom CLI factory) |
| 3 | Get the CEO/CRO/CMO to open the terminal and ask their own questions | One SQL view, one Claude Code prompt, ten minutes of training |
| 4 | Surface bottlenecks from the data, not from QBRs | The lake itself |
| 5 | Build the alphas — public-data wedges specific to your buyer | A small CLI factory (per [[har-cli-alpha-factory]]) |
| 6 | Route ranked accounts back to reps in Slack daily | Slack webhook, slash-commands, two-way HubSpot sync |
| 7 | Measure every closed deal back to the trigger that opened it | One required CRM field, one quarterly view |

The Productside-specific content shows what each step *looks like* when applied to a product-management training business. Swap the buyer and the data sources and you have the same shape for any GTM role.

## Where the alphas come from (the meta-move)

This is the part most "alpha" lists skip. **Alphas aren't guessed at — they're derived from call transcripts plus public-record sources.** The derivation pattern (which lives in the AI-native section):

```
1. Pull last 200 call transcripts into the lake
2. Run a prompt: "what's the most-cited buying trigger across these calls?"
3. Find the public-record analog of that trigger
   (e.g. "they just hired their first PM" → LinkedIn JD search)
4. Add 1–2 qualifying joins (funding, stack, headcount) so the list is small
5. Write the message in the buyer's own language, drawn from the transcripts
6. Ship the CLI to harvest the signal daily
```

The seven Productside alphas in [`alphas/`](./alphas/) are what this derivation pattern produces when applied to Productside's buyer. They're not the methodology — they're an example of the methodology's output.

## Tour map

| Folder | What's in it |
|---|---|
| **[`case-study/`](./case-study/)** | The frame, the 7-step OS, the alpha-summary table |
| **[`alphas/`](./alphas/)** | Seven worked alphas, same six-question template each |
| **[`ai-native/`](./ai-native/)** | Deep dives on Steps 2, 3, 6, 7 of the OS — terminal queries, call intelligence, audit, attribution |
| **[`gtm-os/`](./gtm-os/)** | The 7-step OS pattern (references the canonical Mento version) |
| **[`example-productside-gtm/`](./example-productside-gtm/)** | Click-around scaffold sketch — what the live repo looks like |

## Related

- [`mento-gtm-case-study`](https://github.com/ari-davis-debug/mento-gtm-case-study) — the canonical 7-step OS writeup applied to a comp-tech company
- The Productside-specific working node lives at `internal/ideas/productside-interview-alphas.md` in the source repo
