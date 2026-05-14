# Alpha 3 — 280 Group Backlink Recovery

> *Stub. Fill in step 5.*

## 1. The trigger

Productside used to be 280 Group. Twenty-plus years of conference talks, podcast interviews, blog mentions, and partner pages link to a brand that no longer exists at that URL. Each broken backlink is a piece of authority Productside paid for and no longer captures. Each one is also a *named* person at a *known* company who once thought 280 Group was worth linking to.

## 2. Public data sources stitched

- **Ahrefs / SEMrush** — full backlink graph for `280group.com` (and historical variations)
- **Wayback Machine** — snapshots of pages that linked to 280 Group, to extract the linking content + author
- **LinkedIn** — current employer of each historical author/linker

## 3. Primary key + join logic

- Key: URL of the linking page → author/byline → LinkedIn URL → current company domain
- Filter: linking page is still live, the link is still there (broken or pointing to old domain), author still works in PM/L&D
- Score by: domain authority of linking page × seniority of author × whether their current company matches ICP

## 4. CLI build sketch

- Ahrefs API client — 0.5 day
- Wayback scraper (already a CIA pattern) — 0.5 day
- Author resolution: byline → Google → LinkedIn — 1 day (use existing entity-resolution tooling)
- Output: ranked list of "people who once cared about 280 Group, here's where they work now"

## 5. Sample message with the verifiable claim

> **Subject**: You linked to 280 Group in [date] — we're now Productside
>
> Hey [name],
>
> Came across your [article/podcast/talk] from [date] where you cited 280 Group's [specific framework / specific person]. The brand is now Productside (same team, same curriculum, refreshed). The backlink in [URL] is currently [broken / pointing to old domain].
>
> Not asking you to update it — though it'd be appreciated. Asking because you clearly thought the methodology was worth referencing then, and you're now at [Current Co]. Curious what your PM org looks like now and whether the framework you cited has held up. 15 minutes?
> — Ari

## 6. Expected throughput + cost to build

- Probably ~500–2,000 historical linkers; ~200 currently in ICP-fit roles
- Build cost: 2 days
- Decay rate: low — these are warm-because-of-history accounts, not time-sensitive triggers
- **Note**: this is the one alpha that doubles as a SEO recovery project. The same data drives a redirect plan for marketing.
