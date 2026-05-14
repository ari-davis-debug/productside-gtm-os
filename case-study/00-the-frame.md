# 00 — The Frame

> Three ideas in this page, in this order: **why pure-external alphas**, **why a 7-step OS**, and **why "AI-native" without the substrate is theater**. If you're a GTM engineer onboarding to a new role, this page is the argument you'll be making to the leadership team in your first 30 days.

## Why pure-external alphas

A GTM engineer joining any company has the same problem on day one: the company's first-party data is messy, incomplete, and often locked behind a tool the team has been complaining about for 18 months. Waiting for that data to be clean before you can ship anything is how the first 90 days disappear.

**The move**: build the first wave of pipeline on *purely external* data. Public signals — federal filings, LinkedIn job postings, GitHub repo metadata, conference speaker lists, OSHA citations, EPA violations — that don't need a single integration with the existing CRM to produce a ranked list. Layer the first-party data in later as a multiplier.

In this case study, the worked example is Productside. The seven alphas in [`../alphas/`](../alphas/) are all built on public data — no Productside CRM, no LMS, no alumni database required. That's deliberate. It demonstrates the day-one motion.

The transferable claim: **for any buyer, there exists a public-record signal that fires the moment they're in pain.** The GTM engineer's first job is to find that signal, build the CLI that harvests it, and feed the rep team a list of accounts where the message is already half-written.

## Why a 7-step OS

A list is not a moat. A working list this quarter goes stale next quarter when the source decays or the buyer mix shifts. What compounds is the **substrate** the list runs on:

1. The repo where the playbooks live
2. The data lake the signals land in
3. The terminal where stakeholders ask their own questions
4. The bottleneck file that documents what's broken
5. The agentic dev that ships the next alpha
6. The Slack alert that puts the account in the rep's queue
7. The attribution loop that proves it worked

Skip any one of those steps and the others stop compounding. Build all seven and the company stops being run on dashboards and starts being run on queries.

The 7-step OS is a shape, not a script — but it is a *very specific* shape. The next page ([`02-ai-native-gtm.md`](./02-ai-native-gtm.md)) walks each step in detail, with Productside-specific examples.

## Why "AI-native" without the substrate is theater

"AI-native" gets used to mean: we added a chatbot. Or: we put GPT in front of one workflow. Or: we use Cursor.

That's not AI-native — that's AI-decorated.

**AI-native** means: the data plane is one queryable substrate, and the stakeholders who run the company can query it directly. Not through an analyst, not through a dashboard the analyst built six months ago, not through a Slack thread asking the data team for help. *Directly.* In a terminal. Through Claude Code or any LLM with database access.

That single architectural choice — substrate over silos — is the entire difference. Everything else (call intelligence, alpha harvesting, attribution loops) follows from it. Strip it away and the rest collapses into a pile of automation scripts.

The 7-step OS *is* the AI-native architecture. The deep dives in [`../ai-native/`](../ai-native/) show what changes about specific motions — call intelligence, audit workflows, attribution — once the substrate is in place.

## How to read this repo

If you're a GTM engineer:
- Read this page → [`02-ai-native-gtm.md`](./02-ai-native-gtm.md) → [`../alphas/01-first-pm-hire-cocktail.md`](../alphas/01-first-pm-hire-cocktail.md)
- Then skim the other six alphas to see the pattern repeated
- Then read whichever of the [`../ai-native/`](../ai-native/) deep dives is closest to your current bottleneck

If you're a leader evaluating whether this approach fits your company:
- Read this page for the argument
- Read [`02-ai-native-gtm.md`](./02-ai-native-gtm.md) for the system
- Pick one alpha in [`../alphas/`](../alphas/) and stress-test the data sources for your own buyer

## What this repo deliberately is *not*

- **Not a Productside-internal anything.** Every signal draws on public data. The repo is what a GTM engineer *outside* the company could build, by reading what's public.
- **Not a "Monday plan."** Implementation-specific timelines depend on the existing stack at each company; the methodology is portable, the day-by-day is not.
- **Not finished.** The methodology is the stable part. The alphas evolve quarterly as sources change.
