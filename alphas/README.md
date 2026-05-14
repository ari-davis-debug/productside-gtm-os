# `alphas/` — The 7 Alphas, Fleshed Out

Each alpha answers the same six questions in the same order, so the file shape is predictable. Read one to read all of them.

## The six questions

1. **What's the trigger?** — One sentence. What public event makes this account "in pain right now"?
2. **What public data sources stitch together to detect it?** — Named sources, with their refresh cadence and access pattern (API, scrape, RSS, federal filing).
3. **Primary key + join logic** — How the sources line up. Usually domain or CIK or LinkedIn URL.
4. **CLI build sketch** — The Go skeleton (per [[har-cli-alpha-factory]]). Inputs, outputs, schedule.
5. **Sample message with the verifiable claim** — The actual cold email. Every claim points to a public URL.
6. **Expected throughput + cost to build** — Accounts per quarter, days of build work, decay rate of freshness.

## Ranked by signal-to-noise

1. **[`01-first-pm-hire-cocktail.md`](./01-first-pm-hire-cocktail.md)** — THE alpha. Hand-raise motion.
2. **[`02-public-cpo-8k-trigger.md`](./02-public-cpo-8k-trigger.md)** — Federal-filing trigger. Public companies only.
3. **[`03-280-group-backlink-recovery.md`](./03-280-group-backlink-recovery.md)** — Productside-specific. Rebrand decay capture.
4. **[`04-glassdoor-confessional.md`](./04-glassdoor-confessional.md)** — Pain motion. Engineer reviews tell on their PM org.
5. **[`05-sbir-commercialization.md`](./05-sbir-commercialization.md)** — Trigger. Grant-stage to commercialization stage.
6. **[`06-github-org-tells-on-itself.md`](./06-github-org-tells-on-itself.md)** — Hand-raise. Public ROADMAP + CODEOWNERS signal.
7. **[`07-pm-team-scaling-signal.md`](./07-pm-team-scaling-signal.md)** — Trigger. Headcount delta + JD velocity.

## Why this shape

Most "data alpha" lists are decorative — they name a source without showing what it costs, what it produces, or how the join actually works. The six-question template is the minimum bar for "real alpha vs. wish." If a row can't answer all six, it doesn't belong here.

See [[bespoke-data-points-for-alphas]] for the underlying framework.
