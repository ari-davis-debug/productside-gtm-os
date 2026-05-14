# 03 — Week One

> *Stub. The concrete "what I'd ship Monday" plan.*

## What goes here

A 5-day plan. Each day has one concrete deliverable. End of the week: the first alpha is in production, the substrate is queryable, and one stakeholder has run their first query.

## The plan (to flesh out)

### Monday — Stand up the substrate

- Repo skeleton (this one, minus the case-study/ narrative)
- Supabase project (one schema, three tables: accounts, signals, plays)
- Sync Productside's existing HubSpot accounts in (read-only) so the substrate has a baseline
- One SQL view: `v_priority_queue` — empty for now, scaffolding only

### Tuesday — Stand up Alpha 1's CLI

- Go CLI scraping LinkedIn JDs (existing pattern, port from `cli-factory`)
- Crunchbase API client
- BuiltWith API client
- Run all three against a 500-company seed list. Output normalized event records to Supabase.

### Wednesday — Stitch the alpha

- SQL view joining the three sources on company domain
- Trigger logic: first PM JD posted within last 30 days × Series A/B raised within last 12 months × stack matches ICP archetypes
- Output: ranked list of hand-raise accounts with the verifiable claim per row

### Thursday — Make it AI-native

- One Claude Code slash-command (`/today`) that runs the priority-queue view and renders top 20 accounts with the suggested opener already drafted per row
- Test with Rina (or whoever): "type this question, see what you get"
- One feedback loop wired in: rep marks "not a fit" → that company drops out × ICP weights adjust

### Friday — Ship the first send

- 50 hand-raise accounts → personalized email via the existing SmartLead/Lemlist stack
- A/B: opener variant A (the verifiable JD claim) vs variant B (generic value prop)
- Measurement plan committed in writing before send (kill at <X%, scale at >Y%)

## What's NOT in week one

- The other six alphas (those land weeks 2–6, one per week)
- The call intelligence layer (week 3-4 build)
- The full attribution loop (week 5-6, once there's enough closed pipeline to attribute)
- Anything that requires touching the LMS or alumni database (those are multipliers, not prerequisites)

## TODO when filling

- Make the Monday/Tuesday/Wednesday breakdown more granular (sub-bullets per half-day)
- Add a "definition of done" per day
- Add a small risk callout per day (what could block it)
