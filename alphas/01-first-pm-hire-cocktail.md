# Alpha 1 — The First PM Hire Cocktail

> **Status**: reference template (fills in step 3 of the build plan — the shape that the other six alphas mirror).

## 1. The trigger

A founder publicly admits they have zero product-management maturity *and* they have the cash to fix it. The admission lives in a LinkedIn job description; the cash lives in a recent funding round.

## 2. Public data sources stitched

| Source | What it gives | Access | Refresh |
|---|---|---|---|
| **LinkedIn JD scraper** | First-ever PM JD posted by company X, with full body text | Headless scrape, throttled | Daily |
| **Crunchbase API** | Funding round: stage, amount, date, lead investor | Paid API ($/mo) — or Pitchbook trial | Daily |
| **BuiltWith** | Tech stack at the company's domain (Segment, Mixpanel, Amplitude, Linear, Jira, Productboard, etc.) | Paid API | Weekly |
| **OpenCorporates** *(optional confirm)* | Entity confirmation, alt-domain mapping | Free API, rate-limited | On-demand |

## 3. Primary key + join logic

- **Key**: company domain (normalized: lowercase, strip `www.`, strip `.com`/`.io` only for canonicalization; keep TLD in display)
- LinkedIn JD → company name → domain (one extra resolution hop; cache result)
- Crunchbase → domain (Crunchbase natively keys on domain)
- BuiltWith → domain
- **Join condition**: `domain IN (linkedin_jds.domain ∩ crunchbase.domain ∩ builtwith.domain)`
- **Trigger condition**:
  - JD posted within last 30 days AND
  - JD is the company's first-ever PM-titled posting (no prior PM titles in JD history for this domain) AND
  - Crunchbase shows Series A or Series B raised within last 12 months AND
  - BuiltWith shows ≥2 of: Segment, Mixpanel, Amplitude, Linear, Jira, Productboard

## 4. CLI build sketch

Three Go binaries, one orchestrator. All write to Supabase event tables; orchestrator runs the join in SQL.

```
cli-factory/
├── linkedin-jd-scraper/    # 2 days to build; existing pattern
├── crunchbase-puller/      # 0.5 day; pure API client
├── builtwith-puller/       # 0.5 day; pure API client
└── alpha-1-orchestrator/   # 1 day; runs the join, emits ranked list
```

```sql
-- The join, simplified
WITH first_pm_jds AS (
  SELECT domain, posted_at, job_url
  FROM linkedin_jds
  WHERE title ILIKE ANY(ARRAY['%product manager%','%pm%','%product owner%'])
    AND posted_at > now() - interval '30 days'
    AND NOT EXISTS (
      SELECT 1 FROM linkedin_jds j2
      WHERE j2.domain = linkedin_jds.domain
        AND j2.title ILIKE ANY(ARRAY['%product manager%','%pm%','%product owner%'])
        AND j2.posted_at < now() - interval '30 days'
    )
),
funded AS (
  SELECT domain, round_stage, round_amount, round_date
  FROM crunchbase_rounds
  WHERE round_stage IN ('Series A','Series B')
    AND round_date > now() - interval '12 months'
),
stacked AS (
  SELECT domain
  FROM builtwith_tech
  WHERE tech_slug = ANY(ARRAY['segment','mixpanel','amplitude','linear','jira','productboard'])
  GROUP BY domain
  HAVING count(distinct tech_slug) >= 2
)
SELECT j.domain, j.posted_at, j.job_url, f.round_stage, f.round_amount
FROM first_pm_jds j
JOIN funded f USING (domain)
JOIN stacked s USING (domain)
ORDER BY f.round_amount DESC NULLS LAST;
```

## 5. Sample message with the verifiable claim

> **Subject**: First PM hire at [Co] — three thoughts before you write the JD
>
> Hey [Founder name],
>
> Saw [Co]'s first PM JD go up [date] — congrats on the Series [A/B]. The job spec maps cleanly to where you are: shipping fast, instrumenting with [Mixpanel/Amplitude — whichever they actually use, pulled from BuiltWith], and trying to formalize the product muscle without slowing down what's working.
>
> Three things I've seen go sideways for first PM hires at companies your shape:
>
> 1. The hire owns roadmap but not metrics → ships features, can't tell which ones moved the needle
> 2. No discovery framework → engineering builds what's loudest, not what wins
> 3. Founder still owns the "why" → PM is doing tickets, not product
>
> Productside's Optimal PM curriculum solves #1 and #2 in 12 weeks. Open to a 15-min walkthrough?
>
> — Ari

**Every claim is verifiable**: the JD URL is real, the funding round is on Crunchbase, the stack is on BuiltWith. The prospect can fact-check the email in 30 seconds, which is exactly why it lands.

## 6. Expected throughput + cost to build

- **Throughput**: ~150 qualified hand-raise accounts per quarter across US Series A/B universe (back-of-envelope: ~600 Series A/B raises per quarter × ~30% post first PM JD within 12 months × ~80% pass stack filter = ~144).
- **Build cost**: 4 days of focused work — LinkedIn scraper is the long pole (2 days), the API clients are half-day each, the orchestrator is one day.
- **Decay rate**: JD postings are hot for ~14 days. After that, the role is likely filled and the buying window narrows. Refresh daily, drop accounts whose JD is >45 days old.

## Why this is THE alpha (and not just an alpha)

Three things make this the highest-leverage starting point:

1. **The buyer is the writer.** The founder wrote the JD. The JD is them describing their pain in their own words. The message can quote them back to themselves.
2. **The funding gates qualification.** Series A/B = budget. Without that filter, half the list can't afford private team training.
3. **The stack gates fit.** Companies running Linear/Jira/Productboard already think in product-management vocabulary. They're not the audience that needs convincing PM exists — they're the audience ready to formalize.

Hand-raise + qualified + warm. That's the whole job description for an account exec, handed to them on a list.
