# Alpha 6 — GitHub Org Tells On Itself

> *Stub. Fill in step 5.*

## 1. The trigger

A GitHub organization has a public `ROADMAP.md`, a `CODEOWNERS` file routing product PRs through a specific handle, or a `product/` directory in their org-wide repo — but no completed governance (no PRD template, no decision log, no shipped quarterly review). They've started standardizing product practice and haven't finished. That's the moment Productside's curriculum is for.

## 2. Public data sources stitched

- **GitHub API** — repo metadata, file listings, contributor velocity
- **GitHub search** — `filename:ROADMAP.md`, `filename:PRODUCT.md`, `path:product/`, `filename:CODEOWNERS` containing PM-related routes
- **LinkedIn** — confirm headcount + presence of PM role
- **Crunchbase** *(optional)* — filter to funded companies

## 3. Primary key + join logic

- Key: GitHub org slug → primary domain (most orgs link to their site in the org profile)
- Filter: has public roadmap/product docs AND has not pushed to those files in >60 days AND has growing eng headcount on LinkedIn
- Score: signs-of-effort × completeness-gap (most have started, few have finished)

## 4. CLI build sketch

- GitHub API client (rate-limit aware, auth via PAT) — 1 day
- Repo crawler scoring "started/not finished" — 1 day
- LinkedIn cross-ref

## 5. Sample message with the verifiable claim

> **Subject**: ROADMAP.md at [github-org] hasn't been touched since [date]
>
> Hey [name],
>
> Noticed [Co]'s GitHub has a public `ROADMAP.md` and a `CODEOWNERS` routing product-PRs through @[handle] — clearly trying to standardize. The last commit to those files was [date]; the eng team has grown [N]% since then. We see this exact shape a lot: the "started standardizing, hit other priorities" pattern.
>
> Productside's 4-week PM essentials engagement is built for the "from public roadmap to internal practice" jump. Worth a walkthrough?
> — Ari

## 6. Expected throughput + cost to build

- ~300 orgs per quarter match the started-not-finished pattern
- Build cost: 2 days
- Decay rate: low — these patterns calcify over months
