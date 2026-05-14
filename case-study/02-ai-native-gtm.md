# 02 — AI-Native Go-to-Market

> The phrase "AI-native" gets tossed around like it means something on its own. It doesn't. **AI-native is a shape, and the shape is a 7-step operating system.** Same shape used in the [Mento case study](https://github.com/ari-davis-debug/mento-gtm-case-study), retold for a product-management training company. The alphas in `../alphas/` are not the AI-native part — they're the *outlying signals* harvested inside Step 5. The rest of the substrate is what makes them compound.
>
> **If you're a GTM engineer onboarding to a new role:** this page is the map. Walk into the company, pipe the data plane into a lake (Step 2 — Airbyte is the lowest-effort path), look at the call transcripts to derive your own alphas (the derivation pattern lives at the bottom of this page), and follow the 7 steps to ship the substrate.

## The heuristic (one line per step)

| Step | What it is for Productside | AI-native flavor |
|---|---|---|
| **1** | Stand up the GTM repo | One queryable source of truth — Markdown + SQL + CLAUDE.md, version-controlled |
| **2** | Data + playbooks ingested daily | HubSpot, LinkedIn, call transcripts, alumni records — all flowing into the lake every morning |
| **3** | **Stakeholders in Claude Code** ← the wedge | Rina, CRO, CMO open the terminal and ask their own questions against the substrate |
| **4** | Capture + prioritize bottlenecks | Bottlenecks surface from the data, not from gut-feel meetings |
| **5** | **Agentic dev ships solutions** ← the alphas live here | Each alpha becomes a CLI in the factory, runs forever, feeds the queue |
| **6** | Roll out to the team | Reps see ranked accounts in Slack daily with the verifiable claim drafted |
| **7** | Measure → pipeline + revenue | Every closed deal closes back to a trigger; the substrate keeps itself honest |

If a section below has a deep-dive page, it's linked. Otherwise the section is the page.

---

## Step 1 — Stand up the GTM repo

A literal repo. Markdown files in `foundation/`, SQL files in `sql/`, playbooks in `foundation/playbooks/`. CLAUDE.md at the root defines the constitution. Git is the audit trail. This is mundane plumbing — and it is the precondition for every other step.

**For Productside specifically**: the alumni roster gets first-class treatment (it's a folder, not a CRM field). 280 Group's historical content is a folder. Course-completion data is a folder. The point isn't novelty; the point is that anything that matters has a home a human can read and a machine can query.

→ The shape lives in [`../gtm-os/`](../gtm-os/) and the live scaffold lives in [`../example-productside-gtm/`](../example-productside-gtm/).

---

## Step 2 — Data + playbooks ingested daily

Every morning, the lake pulls:

- **HubSpot** — accounts, contacts, deals, activities (read-only mirror into Supabase)
- **LinkedIn** — JD postings, headcount deltas, job-change events (scraper, feeding a table)
- **Call transcripts** — Fireflies API for Trellus/Avoma exports, dumped raw + extracted into structured fields
- **Alumni + cohort data** — LMS export, joined by domain
- **External signal feeds** — the alpha CLIs (Step 5) write their event records here

**Recommended path: Airbyte** for the standard connectors (HubSpot, Salesforce, Stripe, Snowflake, Postgres, Google Ads, etc.) and a small custom CLI factory (per [[har-cli-alpha-factory]]) for everything Airbyte doesn't cover — LinkedIn scrapes, SEC EDGAR, NIH SBIR, GitHub repo crawls. The split: **Airbyte for the boring 80%, custom CLIs for the alpha-grade 20%.** That way the engineer isn't reinventing CRM sync, they're spending their time on the sources nobody else is mining.

This is what "AI-native" actually requires under the hood: **a queryable substrate that has every fact in one place.** No tab-switching. No "let me check the dashboard." A single SQL view can join call transcripts to alumni history to LinkedIn to EDGAR filings to BuiltWith stack — because all of it landed here this morning.

→ Deep dive on the call-transcript piece: [`../ai-native/call-intelligence.md`](../ai-native/call-intelligence.md)

---

## Step 3 — Stakeholders in Claude Code (the wedge)

This is the part most "AI-native" pitches skip and the part that actually changes a company.

The CEO, CRO, and CMO each open a terminal — literally Claude Code — and ask questions of the substrate **directly**. No ticket. No analyst. No "let me get back to you Thursday."

**Rina (CEO) types:**
```
Which alumni from 2022–2024 cohorts now work at companies that filed an
8-K appointing a new CPO this quarter?
```

Twelve seconds later: 12 alumni at 9 companies, with the filing URL and new exec name per row. She forwards the list to enterprise sales with one line.

**CRO types:**
```
Across our last 200 calls, list every objection that mentioned "Reforge"
or "Pragmatic" by name, and tag which deals they came from.
```

A minute later: a ranked list of competitive losses with the actual quoted phrases, deal IDs, and the AE who took the call.

**CMO types:**
```
Show me the 50 lost-to-no-decision deals from Q3 and cluster the top
five recurring buyer objections from the call transcripts.
```

The substrate runs the SQL view it was always going to run; Claude phrases it as English. The CMO sees the gap.

**This is what "AI-native" earns the company**: the analyst bottleneck dissolves. Decisions get made in the meeting, not after it. Stakeholders are *operators* of the data plane, not consumers of dashboards built about it.

→ Worked queries with SQL: [`../ai-native/stakeholder-queries.md`](../ai-native/stakeholder-queries.md)

---

## Step 4 — Capture + prioritize bottlenecks

Bottlenecks don't surface in QBRs. They surface in the lake. A bottleneck is anywhere a measurable thing is bleeding: reply rate dropped on a segment, alumni-to-enterprise conversion is flat, a copy variant just lost significance, an alpha's throughput collapsed.

Each bottleneck gets a file in `bottlenecks/` with: what's broken, what the data says, what fixing it is worth, what builds it. The file is human-readable and machine-queryable. Quarterly, the team ranks them; the top-1 is what Step 5 builds next.

For Productside, the bottlenecks I'd expect to surface first:
- **Alumni-to-enterprise conversion is unmeasured.** No one knows if alumni inside an enterprise account predicts close rate.
- **Rebrand backlink decay is unrecaptured.** 280 Group's authority is leaking to old URLs (this is also Alpha 3).
- **First-PM-hire signal isn't covered.** Inbound from companies that publicly admit they have no PM is being missed entirely (this becomes Alpha 1).

The bottleneck file *is* the spec for the next build.

---

## Step 5 — Agentic dev ships solutions (where the alphas live)

This is where most candidates' "GTM Engineer" answer stops and where the actual job starts. The seven alphas in [`../alphas/`](../alphas/) are not standalone projects. They are **outlying-signal harvesters that the agentic-dev step stands up inside the factory**.

Each alpha is one CLI binary:

| Alpha | What it harvests | Source family |
|---|---|---|
| 1 — First PM Hire Cocktail | Founders publicly admitting zero PM maturity | LinkedIn JD × Crunchbase × BuiltWith |
| 2 — Public CPO 8-K Trigger | New buying-authority arrivals at public cos | SEC EDGAR Item 5.02 |
| 3 — 280 Group Backlink Recovery | Historical authority leaking from rebrand | Ahrefs × Wayback × LinkedIn |
| 4 — Glassdoor Confessional | Engineers admitting PM-org pain | Glassdoor × Blind |
| 5 — SBIR Commercialization | Deep-tech founders hitting commercialization wall | NSF/NIH SBIR × LinkedIn |
| 6 — GitHub Org Tells On Itself | Companies mid-standardization of product practice | GitHub API × LinkedIn |
| 7 — PM Team Scaling Signal | PM orgs past the framework-required inflection | LinkedIn headcount × JDs |

**The factory pattern**: each CLI is small (a day or two of Go), independent (one source, one purpose), composable (writes normalized events to the lake), and replaceable (if a source dies, swap the CLI without touching the rest).

The agentic dev part isn't that an LLM writes the CLI — it's that **Claude Code is the operator** writing specs, scaffolding the CLI, generating the SQL view, and wiring the rollout. The human reviews and ships.

→ Each alpha fully built: [`../alphas/`](../alphas/) (Alpha 1 is the reference template)

---

## Step 6 — Roll out to the team

Pipeline that never reaches a rep is theater. Roll-out is the part that makes the substrate matter:

- **Slack alerts**, per-rep, every morning: "Three new accounts in your queue: [name] (Alpha 1), [name] (Alpha 1.5), [name] (Alpha 4). Verifiable claim already drafted, [link]."
- **Per-alpha slash-commands** in Claude Code: `/today` shows the queue; `/draft <account>` writes the opener; `/log <account> not-fit` updates the substrate.
- **Different views for different teams**: enterprise reps see private-training prospects; individual-course advisors see different segments; CS sees alumni-at-risk signals.
- **Two-way sync to HubSpot**: every action a rep takes lands in the CRM the company already pays for.

The point: AI-native doesn't replace the rep. It removes everything that wasn't the rep's job.

→ Deep dive on the call-intel side of roll-out: [`../ai-native/call-intelligence.md`](../ai-native/call-intelligence.md)

---

## Step 7 — Measure → pipeline + revenue

Every closed deal closes back to a trigger. Every trigger maps to an alpha. Every alpha gets a quarterly read on pipeline contribution × win rate × ACV × time-to-close vs. cold baseline. The substrate keeps itself honest, and the underperforming alphas get killed.

This is also where the audit workflows live — daily funnel-leak detection, pre-committed kill/park/scale gates, statistical-significance flags on every A/B.

→ Audit side: [`../ai-native/audit-workflows.md`](../ai-native/audit-workflows.md)
→ Attribution side: [`../ai-native/attribution-loop.md`](../ai-native/attribution-loop.md)

---

## How to derive your own alphas (the part that travels)

The seven Productside alphas in [`../alphas/`](../alphas/) are not the methodology — they're an *output* of the methodology, applied to one buyer. If you're a GTM engineer onboarding to a different company, you'll derive a different seven. Here's the pattern.

```
1. Pull last 200+ call transcripts into the lake (Step 2)
2. Run a prompt over them in Claude Code (Step 3):
     "What is the most-cited buying trigger across these calls? Quote
      the exact phrases the buyers used. Cluster by trigger type."
3. Look at the top 3 clusters. Each one is a candidate alpha.
4. For each cluster, find the PUBLIC-RECORD analog of that trigger.
     Example: cluster says "they just hired their first PM" →
     public analog is "first PM-titled JD posted in last 30 days"
5. Add 1–2 qualifying joins so the list is small and high-fit.
     Funding stage. Tech stack. Headcount band. Industry.
6. Write the cold message in the buyer's own language —
     drawn directly from the transcript quotes you clustered.
7. Ship the CLI to harvest the public signal daily (Step 5).
8. Route ranked accounts to reps in Slack (Step 6).
9. Measure (Step 7). Kill the alphas that don't close. Refit.
```

**The point**: the substrate is what makes this pattern repeatable. Step 2 puts the transcripts in the lake; Step 3 lets you query them in English; Step 5 is where the alpha gets built. Without the substrate, alpha-derivation is a slide deck. With it, alpha-derivation is something you run every quarter as buyers and triggers shift.

## The one-line version

> **Most GTM engineers ship lists. The 7-step substrate is what makes lists compound — and the alphas are the outlying signals that the substrate harvests at Step 5.** Without Steps 1–4, the alphas are isolated scripts. Without Steps 6–7, they're unmeasured. The whole point of "AI-native" is that the seven steps are one system, not seven projects.

## Where each ai-native deep-dive lives

| Step | Deep dive page |
|---|---|
| 2 (data) + 6 (roll-out) | [`../ai-native/call-intelligence.md`](../ai-native/call-intelligence.md) |
| 3 (stakeholders) | [`../ai-native/stakeholder-queries.md`](../ai-native/stakeholder-queries.md) |
| 7 (audit) | [`../ai-native/audit-workflows.md`](../ai-native/audit-workflows.md) |
| 7 (attribution) | [`../ai-native/attribution-loop.md`](../ai-native/attribution-loop.md) |
| 5 (alphas as outlying signals) | [`../alphas/`](../alphas/) — seven CLIs, one factory |
