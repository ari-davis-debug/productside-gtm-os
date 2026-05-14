# Alpha 2 — Public CPO 8-K Trigger

> *Stub. Fill in step 5 (after Alpha 1 template is locked).*

## 1. The trigger

A public company appoints a new Chief Product Officer or VP of Product. By SEC rule, the appointment must be disclosed in an 8-K filing within four business days. The 8-K is the timestamp of a new buying authority arriving.

## 2. Public data sources stitched

- **SEC EDGAR** — 8-K filings, Item 5.02 (Departure / Appointment of Directors or Principal Officers)
- **LinkedIn job postings** — confirm the new hire is also scaling the team underneath them
- **EDGAR 10-K Risk Factors** *(optional)* — pulls language about "product execution risk" or "competitive product gaps" that's been admitted in the annual report

## 3. Primary key + join logic

- Key: CIK (SEC Central Index Key) → maps to company domain via lookup table
- 8-K filtered for Item 5.02 + title regex (`Chief Product Officer|VP.*Product|Head.*Product|Chief Innovation Officer`)
- Cross-ref to LinkedIn for active PM JDs at the same domain → confirms team-build motion

## 4. CLI build sketch

- EDGAR scraper (RSS feed of new filings, parse 8-K body for Item 5.02 + title regex) — 1.5 days
- Reuse LinkedIn scraper from Alpha 1
- Reuse 10-K language extractor if optional source enabled

## 5. Sample message with the verifiable claim

> **Subject**: Welcoming [New CPO name] to [Co] — quick note on the first 100 days
>
> Hey [name],
>
> Saw the 8-K on [date] — congrats on the new role.
> [Insert 1-line public observation about company's product situation from 10-K or recent earnings call.]
> Most public-co CPOs in their first 100 days walk into the same three knots: roadmap inheritance, OKR misalignment, and a PM team that's been waiting for direction. Productside's enterprise advisory engagement is built around those three. Worth 15 minutes?
> — Ari

## 6. Expected throughput + cost to build

- ~40–60 8-K CPO appointments per quarter across the Russell 3000
- Build cost: 1.5–2 days
- Decay rate: 8-K is hot for ~5 days, then the new exec is in onboarding lockdown for ~30. Best window: day 30–60 after filing.
