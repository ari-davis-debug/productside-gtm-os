# Alpha 4 — Glassdoor Confessional

> *Stub. Fill in step 5.*

## 1. The trigger

Engineers and PMs writing Glassdoor and Blind reviews tell on their own product organization. "No roadmap clarity." "PMs don't know what they own." "Product strategy changes monthly." These admissions are public, dated, and attributable to specific companies.

## 2. Public data sources stitched

- **Glassdoor** — reviews scoped to companies above 200 headcount
- **Blind** — same, anonymous-but-company-attributed
- **G2 / Capterra review text** *(optional)* — product reviews that mention internal PM dysfunction
- **LinkedIn headcount** — confirms company is large enough to have a real PM org

## 3. Primary key + join logic

- Key: company name → normalized → domain
- Filter: review text matches PM-pain regex (`roadmap (chaos|unclear|confusing)|PMs (don'?t|aren'?t)|product strategy (chang|shift|piv)|no clear product|PM (turnover|attrition)`)
- Score: density of PM-pain reviews / total reviews × company size × recency

## 4. CLI build sketch

- Glassdoor + Blind scrapers (rate-limit heavy, use residential proxies) — 2 days
- Regex/NLP scorer over review corpus — 0.5 day
- Quarterly refresh; output top 200 list

## 5. Sample message with the verifiable claim

> **Subject**: Three reviews at [Co] said the same thing in [quarter]
>
> Hey [name],
>
> Your engineers are leaving Glassdoor/Blind reviews that all point to the same gap. [Paraphrase, do not quote — see legal note below.] If 3 of your 12 reviewers in [quarter] independently surfaced the same friction, that's a signal, not noise.
>
> The friction they're describing maps cleanly to what Productside's Optimal PM curriculum addresses in 12 weeks. Worth a 15-minute walkthrough of which symptom matches which fix?
> — Ari

**Legal note**: Don't directly quote review text. Paraphrase, attribute to "your reviewers," and keep the message about the pattern, not the individual.

## 6. Expected throughput + cost to build

- ~100–300 companies per quarter pass the density threshold
- Build cost: 2.5 days (Glassdoor scrape is the long pole)
- Decay rate: medium — review patterns shift quarterly; refresh quarterly
- **Risk**: Glassdoor TOS prohibits scraping. Real production version should use the Glassdoor for Employers API or a licensed data partner.
