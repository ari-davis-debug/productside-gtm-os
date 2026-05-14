# Alpha 5 — SBIR Commercialization Trigger

> *Stub. Fill in step 5.*

## 1. The trigger

A company receives an SBIR Phase II award (federal commercialization grant — typically $750K–$1.5M over 2 years). Phase II means they've proven technical feasibility in Phase I and are now mandated to commercialize. Commercialization requires product management. Most Phase II awardees are deep-tech founders who have never built a product org.

## 2. Public data sources stitched

- **NSF SBIR award database** — Phase II awards across all topics
- **NIH SBIR award database** — same for biotech/healthtech
- **SAM.gov** — federal contract registrations (confirms company is set up to commercialize)
- **LinkedIn** — confirm leadership lacks product-org experience (PhD-heavy, no prior PM titles)

## 3. Primary key + join logic

- Key: company name → normalized → domain
- Filter: Phase II award date within last 18 months, award value above threshold, company size <100 employees, no current PM headcount on LinkedIn
- Score: award size × time-since-award (sweet spot: 6–12 months in)

## 4. CLI build sketch

- SBIR scraper (NSF/NIH provide bulk CSV downloads; very clean data) — 1 day
- SAM.gov API client — 0.5 day
- LinkedIn cross-ref using existing scraper

## 5. Sample message with the verifiable claim

> **Subject**: $X SBIR Phase II is great — and the hardest part starts now
>
> Hey [Founder],
>
> Saw [Co]'s SBIR Phase II announcement from [agency] back in [month]. Phase II's commercialization mandate is where most deep-tech founders hit a wall — the science is proven, the question becomes "who is this for and what do they pay." That's product management work, and it's almost always the first non-technical hire after Phase II.
>
> Productside's Optimal PM curriculum is built for that hire. Open to a 15-min on what the first 90 days of product hiring looks like for a Phase II-stage company?
> — Ari

## 6. Expected throughput + cost to build

- ~500 SBIR Phase II awards per year across NSF + NIH; ~150 fit ICP filters
- Build cost: 1.5 days
- Decay rate: slow — commercialization is a multi-quarter pressure
