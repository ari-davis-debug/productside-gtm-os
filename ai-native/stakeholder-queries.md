# Stakeholder Queries — Mento OS Step 3 Applied

> *Stub. Fill with concrete SQL view + prompt pairs.*

## What this is

Three named stakeholders. Three real questions. Each question shipped end-to-end: what they type, the SQL view that runs, the answer they get, the follow-up action.

## Rina (CEO) — Alumni-to-pipeline question

**She types:**
```
Which alumni from 2022–2024 cohorts work at companies that filed an 8-K
appointing a new CPO this quarter?
```

**Claude Code translates to:**
```sql
SELECT a.alumni_name, a.cohort, a.current_company, e.filing_date, e.new_exec_name
FROM v_alumni a
JOIN v_edgar_8k_cpo_appointments e
  ON a.current_company_domain = e.company_domain
WHERE a.cohort_year IN (2022,2023,2024)
  AND e.filing_date > now() - interval '90 days';
```

**Answer:** 12 alumni at 9 companies, with the filing URL and new exec name per row.

**Next action she takes**: forward the list to the enterprise sales lead with a one-line note. The substrate did the analyst's work in 12 seconds.

## CRO — Win-pattern question

**Types:**
```
Show me win-pattern signatures across our last 200 closed-won enterprise deals.
Cluster by: industry, team size at close, presence of a prior alumni inside,
trigger event that opened the opportunity.
```

**Output**: ranked correlate table with statistical significance flags.

**Insight surfaced**: alumni-inside is the #1 predictor; trigger-event-type ranks third behind ACV-band.

**Next action**: redirect 30% of outbound capacity toward the alumni-trigger crossover (which is Alpha 1.5 territory).

## CMO — Content-gap question

**Types:**
```
What content gap shows up across our top 50 lost-to-no-decision deals?
Quote the most-repeated buyer objections from the call transcripts.
```

**Output**: clustered objection themes with anonymized quoted excerpts.

**Insight surfaced**: 18 of 50 lost deals raised the "what's different from Reforge" question; current content doesn't address it head-on.

**Next action**: commission a comparison page that week.

## The system around it

- All three queries hit the same Supabase substrate
- Claude Code runs the same SQL views — version-controlled in `sql/` — no one writes ad-hoc SQL
- Every query is logged → over time, the most-asked questions become canonical dashboards
- New stakeholders onboard by reading the prior queries

## What this replaces

| Today | With substrate |
|---|---|
| "Can you pull this for me by Thursday?" | Answer in 12 seconds, in the meeting |
| Dashboards built once, drift forever | Live views, version-controlled, audit-able |
| Each exec siloed in their tool (CEO in HubSpot, CRO in Gong, CMO in GA) | One substrate, three viewports |
| Analyst bottleneck | Analyst becomes the substrate maintainer, not the substrate operator |
