# Signal Array — Reorientation
### The pivot from venture-scale SaaS to research methodology deployed as consulting · canonical record

**Author:** Shalom Ormsby (with Claude)
**Date:** 17 May 2026
**Status:** Canonical. Supersedes the venture-scale ambition embedded in the original *Business Plan*, *Marketing & GTM Plan*, *Financial Model*, and the Phase 5–6 portions of *12-Month Roadmap*. The other docs in this folder remain in force as supporting operational detail, updated against this frame.
**Read first:** this is now the entry point for the Signal Array doc set.

---

## The reorientation in one paragraph

Signal Array stops being a fledgling venture and becomes **a calibration-disciplined research methodology, deployed as bursty consulting engagements** — with the Moloco-001 calibration report and the CHI 2027 paper as the year's commercial and academic anchors, and OpenCosmos as the substrate it strengthens by being used. The methodology, the Signal Array application code, the calibration framework, and the Judge Agent remain mine. The Moloco-specific pack content remains Moloco's, per the existing engagement-pitch IP split. What changes is the time horizon and the ambition shape: no SaaS GTM, no customer ramp targets, no funding decision, no hiring. If a second engagement self-arrives from the calibration report or the CHI paper, evaluate it on its own merits at that time. Phases 5–6 of the original plan become *latent options*, not *required milestones*.

---

## The energy-budget reality

The original plan allocated 60% of weekly hours (24/40) to Signal Array indefinitely. That allocation implicitly assumed Signal Array was *product work*. In reality, B2B SaaS in solo-operator mode is 20% build and 80% operations: procurement reviews, legal-redlines, SOC 2 evidence, security questionnaires, customer-success motions, dunning, sales pipeline, content-marketing rhythms. That 80% is incompatible with the rest of my life — paid Moloco work, family commitments, OpenCosmos curation, Creative Powerup community programming.

The diagnosis is right; the prescription is the change. The pivot is *not* "give up Signal Array" and it's *not* "convert everything to work-for-hire under the Moloco contract." It's "keep the methodology, deliver Moloco-001, ship the CHI paper, decline to run a SaaS company."

---

## The IP architecture stays — this is not the work-for-hire pivot

This document records a deliberate choice *against* the alternative proposal of restructuring Signal Array as pure work-for-hire under the Moloco contract. That alternative would have:

- Forfeited the CHI 2027 paper (publication requires sign-off if the methodology belongs to Moloco)
- Erased the portable professional identity Signal Array represents
- Removed the option to ever do this work again, with any future client, under my own banner

The Moloco Engagement Pitch's commercial-structure section (lines 44–48) already implements the right architecture:

- **Moloco-specific pack content** (personas, scenarios, heuristics tuned to Moloco's product) → work-for-hire, Moloco's.
- **Signal Array application code, Judge Agent, calibration framework, methodology** → mine.
- **OpenCosmos substrate** (`@opencosmos/ui`, `@opencosmos/constellation`, the corpus) → already MIT, already public, strengthened by being used.

This is the "have your cake and eat it too" architecture. The reorientation preserves it exactly. Customer-facing copy should consistently frame Signal Array as *a research methodology I'm developing, and the Moloco delivery is its commercial use this year* — not as *a SaaS lighthouse Moloco is the launch customer for.*

---

## Strategic timing — the contract window

Today is **17 May 2026.** The current Moloco contract ends **31 July 2026** (~10–11 weeks from now). The 8-week Signal Array engagement proposed in the Moloco Engagement Pitch (running roughly May 22 – July 17) fits cleanly inside the existing contract window:

- **May 22 – July 17 (~8 weeks):** Signal Array delivery — persona authoring → MVP → cohort → published Moloco-001 calibration report.
- **July 17 – July 31 (~2 weeks):** Handoff, internal Speedboat walkthrough, and the contract-extension conversation with Bert — armed with the freshly-published calibration report as evidence.
- **August onward:** Either the contract extends (relationship continues at whatever shape makes sense to both parties) OR it doesn't, and there are ~6 weeks of moderate-intensity work to draft and submit the CHI 2027 paper before the September 11 deadline, with OpenCosmos and Creative Powerup reclaiming hours either way.

The timing is unusually clean: the keystone artifact lands two weeks before the contract end, giving both Bert and me real evidence to negotiate against rather than projections.

---

## What's still true (the through-line)

The reorientation preserves the parts of the original plan that were always load-bearing:

- **The Moloco Engagement Pitch.** 8-week scope, clean IP split, calibration report published regardless of outcome. Ships as-is, with only the lightest tweaks to soften "lighthouse application" language.
- **The CHI 2027 paper.** Single most valuable Year-1 academic artifact. Methodology stays publishable because I still own it. Submitted September 11, 2026. Co-authored with Moloco contact if Bert is willing.
- **The Creative Portfolios free demo.** Ships in Phase 4 as planned, but the framing shifts: this is a *gift to the design community demonstrating the methodology in public*, not a top-of-funnel lead-generation surface. Same artifact, different intent.
- **OpenCosmos as substrate.** Moloco delivery continues to battle-test `@opencosmos/ui` and `@opencosmos/constellation`. The open foundations strengthen for free.
- **The methodology and the four moats** (two-layer grounding, expert-skill grading, two-agent split, calibration discipline). All preserved. The CHI paper is the durable record of them.
- **The Brand Architecture decisions.** `opencosmos.ai/signalarray` URL, "Signal Array, by OpenCosmos" lockup, Studio/Terra theming, wordmark, trademark filing intent. All still right.
- **The technical kernel.** Two-agent architecture, persona schema, calibration framework, constellation adapter — exactly what gets built to deliver Moloco-001. The only deferred parts are the multi-tenant SaaS plumbing (Clerk, Stripe billing, customer workspace, SOC 2) that the reorientation makes unnecessary.

---

## What's no longer the plan

The following commitments from the original doc set are *retired*, not paused. Reactivation requires explicit re-evaluation against the *When to revisit* triggers below, not drift.

- **Customer-ramp targets.** Year 2 ($750K–1.5M, 4–8 customers) and Year 3 ($2.5–4M, 12–18 customers) goals are no longer the operational picture. The Financial Model's monthly projections are not the budget.
- **Sales motions.** The three motions (Pilot Pack / Platform / Enterprise) and their funnel KPIs (contact form submissions, discovery calls, proposals issued, CAC by tier) are retired. No outbound, no CRM, no pipeline tracking.
- **Hiring triggers.** The Phase 5 engineer contractor (~$96K/yr), the persona/research curator (~$48K/yr), and the Year 3 FTEs (engineer, pack-authoring lead, customer-success) are sunset. No hiring is contemplated.
- **Funding-posture decision.** The Phase 6 "bootstrap / raise / acquire / expand-with-Moloco" decision goes away. The default is permanently bootstrapped — the question simply doesn't get asked.
- **Multi-tenant SaaS infrastructure.** Clerk auth, Stripe billing, customer workspace management, multi-tenant isolation, SOC 2 evidence collection — all deferred indefinitely. The Moloco app runs single-tenant.
- **Second commercial pack as a required milestone.** The Phase 5 commitment to land a non-Moloco paying customer by month 6 is retired. If a customer self-arrives via the calibration report or CHI paper, evaluate. If not, no action.
- **The 60%-of-week allocation to Signal Array.** Replaced by bursty allocation — 24 hrs/wk during active contract weeks; 4–6 hrs/wk between contracts (CHI paper writing, methodology curation, occasional content). The reclaimed hours redistribute to OpenCosmos and Creative Powerup.

---

## Doc status

Recommended disposition for each doc currently in `signalarray/docs/ideation/`. Three categories: **Active** (operational plan), **Active with tweaks** (live, with edits applied to match the reorientation), **Rewrite** (live, but materially rewritten), **Dormant** (preserved in `superseded/` as historical reference; reactivation requires the triggers below).

| Doc | Status | Disposition |
|---|---|---|
| 00-REORIENTATION.md (this doc) | Active | New canonical entry point. |
| Signal Array – Moloco Engagement Pitch.md | Active with tweaks | Soften "lighthouse application" language. Customer-facing artifact; the IP split is already right. |
| Signal Array – Platform Vision.md | Rewrite | Sections 1–7 + 11 + 12 survive. Sections 8 (verticals), 9 (Phases 5–6), 10 (commercial pricing) pruned. SaaS-platform framing replaced with research-methodology framing. |
| Signal Array – Brand Architecture.md | Active with tweaks | Section 1's "high-ticket B2B contracts" → "consulting-shaped commercial engagements." Section 5's pricing tiers retired. |
| Signal Array – Technical Implementation Plan.md | Active with tweaks | Phases 0–4 preserved. Phases 5–6 deferred. SOC 2, Clerk, Stripe removed from active stack. Single-tenant for Moloco. |
| Signal Array – CHI 2027 Paper Outline.md | Active, unchanged | Year's most valuable academic artifact. No changes. |
| Signal Array – Operating Cadence.md | Rewrite | Section 1 allocation table → bursty model. Section 9 (hiring triggers) removed. Section 10 (sustainable) → simplified. Section 11 (12-month picture) → rewritten around Moloco delivery + CHI submission + healthy OpenCosmos/CP, not customer counts. |
| Signal Array – Risk Register.md | Rewrite | Removed: 3.2 (no second customer), 3.3 (procurement), 3.4 (churn), 5.1 (Y2 break-even), 5.3 (tax/nexus). 3.1 (Moloco extension) reframed. 4.1 (burnout) marked *mitigated by reorientation*. Top-5 rebuilt. |
| Signal Array – 12-Month Roadmap.md | Rewrite | Phases 0–4 preserved. Phase 5 → "latent option." Phase 6 (funding decision) removed. Year-end rubric simplified. |
| Signal Array – Business Plan.md | Dormant | The venture-scale framing being retired. Moved to `superseded/`. |
| Signal Array – Marketing & GTM Plan.md | Dormant | Three sales motions and funnel KPIs are precisely what's being retired. Moved to `superseded/`. |
| Signal Array – Financial Model.xlsx | Dormant | 3-year customer-ramp model no longer the operational picture. Moved to `superseded/`. |

---

## When to revisit (reactivation triggers)

The dormant docs are *preserved*, not deleted, because conditions could change in ways that warrant reopening the venture-scale conversation. Concrete triggers that would justify pulling the *Business Plan* and *Marketing & GTM Plan* back out of `superseded/`:

- **Three or more unsolicited inbound commercial inquiries** within ~60 days of the Moloco-001 calibration report publishing or the CHI 2027 paper submission. Not warm intros I initiated — genuine cold inbound from companies seeking the methodology. That signal would mean the market is pulling, not pushing.
- **A Moloco contract extension that explicitly funds engineering capacity beyond my own hours** (e.g., a clause that pays for a contractor to scale the kernel for multi-team Moloco use). That changes the energy math materially.
- **An academic or industry collaborator with operational capacity** (a co-founder, a credible sales partner, a research lab willing to co-build the second pack) approaches with a concrete proposal. Solo-operator constraints are the binding limit; a credible partner relaxes it.
- **A personal-life change** that meaningfully expands the time budget (kids becoming more independent, transition out of Moloco contract work, etc.). Unlikely in the next year; flagged for honesty.

None of these are forecast. If they happen, they happen. The point of preserving the dormant docs is so that *if* the conditions change, I'm not starting strategic thinking from scratch.

What does *not* qualify as a reactivation trigger: enthusiasm in the moment, a positive piece of press, a single warm conversation, my own restlessness, FOMO about a competitor raising. The discipline is to require *unsolicited external pull* — not internal push — before reopening the venture-scale ambition.

---

## How to use this doc

- **Future-me reading the doc set:** start here. Then read whichever operational doc applies to the immediate question (Operating Cadence for time-allocation questions; Moloco Engagement Pitch for customer-facing framing; CHI Paper Outline for the academic track; Technical Implementation Plan for build decisions).
- **A trusted advisor reading the doc set:** this is the brief. If the framing here doesn't make sense to them, that's the signal I'd want to hear; otherwise the supporting docs explain the operational detail.
- **Bert or a Moloco contact reading the doc set (in the unlikely case they ask for the strategic frame):** the Moloco Engagement Pitch is the customer-facing artifact and it stands alone. This doc is internal and doesn't need to be shared.

---

## Companion documents

**Active operational docs (this folder):**
- *Signal Array – Moloco Engagement Pitch* — the customer-facing artifact for Bert.
- *Signal Array – Platform Vision* — the methodology and the four moats.
- *Signal Array – Brand Architecture* — `opencosmos.ai/signalarray` URL, wordmark, theming.
- *Signal Array – Technical Implementation Plan* — what to build for the Moloco delivery.
- *Signal Array – CHI 2027 Paper Outline* — the academic track.
- *Signal Array – Operating Cadence* — bursty time allocation across three brands + family.
- *Signal Array – Risk Register* — what could go wrong, slimmed to the reorientation's actual scope.
- *Signal Array – 12-Month Roadmap* — Phases 0–4 in detail.

**Dormant (preserved in `superseded/`):**
- *Signal Array – Business Plan* — venture-scale commercial structure.
- *Signal Array – Marketing & GTM Plan* — sales motions, funnel, content calendar.
- *Signal Array – Financial Model.xlsx* — 3-year customer-ramp projections.
