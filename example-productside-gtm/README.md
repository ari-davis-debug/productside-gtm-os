# `example-productside-gtm/` — Live Scaffold (Sketch)

> *Stub. Built in step 6 of the build plan — after the alphas and AI-native layer are locked.*

## What this folder will be

A click-around example of what `productside-gtm/` looks like once stood up. Same shape as [`example-mento-gtm/`](../../mento-case-study/example-mento-gtm/), but specialized: alphas folder maps to bottlenecks folder, ICP weights tuned for training-co buyers, sample account is a Series-B SaaS company that just posted its first PM JD.

## The 5-minute path (planned)

1. `foundation/_synthesis.md` — what wins deals at Productside (rolling belief, monthly rewrite)
2. `accounts/example-northstar-software/deal.md` — fully-filled example account, scored 87/100, every claim traceable
3. `bottlenecks/_synthesis.md` — ranked queue; top-1 is what week-one builds

## Why this is a stub

The narrative pieces (case-study/, alphas/, ai-native/) are higher leverage to ship first. They're the "argument" of the repo. The live scaffold is the "proof the argument operationalizes" — important, but only after the argument is locked.

If the interview gets to "show me what your first week looks like in repo form" — that's the cue to flesh this out. Otherwise: stub stays, link to the Mento equivalent in the README, move on.

## Files this folder will eventually have

Same tree as `example-mento-gtm/`. See that folder for the shape. Productside-specific deltas:

- `accounts/example-*` — three sample accounts, one per alpha motion (hand-raise, trigger, pain)
- `bottlenecks/` — three sample bottlenecks tied to the top three alphas
- `sql/` — three SQL views: ICP scorer, priority queue, alpha attribution
- `services/signal-workflow/spec.md` — what Alpha 1 looks like fully specced
- `foundation/playbooks/outbound.md` — one playbook per alpha motion
