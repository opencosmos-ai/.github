# Signal Array — 12-month roadmap
### Phases, milestones, dependencies, and success criteria · May 2026 – April 2027

**Author:** Shalom Ormsby (with Claude)
**Date:** 17 May 2026 (rewritten to reflect the reorientation; supersedes the 15 May 2026 draft)
**Status:** Working timeline. Iterates with the Moloco engagement and ongoing build progress.
**Companion to:** *00-REORIENTATION*; *Signal Array — Platform Vision*; *Signal Array — Technical Implementation Plan*

---

## At a glance

The 12-month plan under the reorientation is anchored around two artifacts: the **Moloco-001 calibration report** at week 8 (mid-July 2026) and the **CHI 2027 paper submission** at week 17 (September 11, 2026). Phases 0–3 are the Moloco delivery; Phase 4 is the Creative Portfolios free demo; Phase 5 is the post-contract window (CHI paper writing + Moloco contract decision). Phase 6 (funding-posture decision) has been removed under the reorientation.

```
   Phase 0       Phase 1       Phase 2       Phase 3 ★     Phase 4       Phase 5 ★
   Week 1        Wk 2-3        Wk 4-5        Wk 6-8        Wk 9-12       Mo 4-6

   Persona       Single-       Judge +       Calibration   Public demo   CHI paper +
   grounding     persona       cohort        report        + content     contract decision
                 MVP

   ↓             ↓             ↓             ↓ ★           ↓             ↓ ★
   12 dossiers   1 persona     12 personas   moloco-001    Portfolios    CHI submission
   Skill axes    1 scenario    Judge live    publishes     demo live     Contract decided
   Grounded      Browser ok    Constellation Bert demo     Content       OpenCosmos/CP up
```

★ = keystone artifacts. The original Phase 5 ("Second commercial pack signed") is now a *latent option* — see *00-REORIENTATION* for the reactivation triggers that would warrant pursuing it. Phase 6 ("Decide commercial path") was about choosing among bootstrap / raise / acquire / expand-with-Moloco; under the reorientation the answer is structurally "stay bootstrapped and solo," and the question doesn't get asked.

---

## Phase 0 — Persona grounding & scaffolding · Week 1 (May 15–22, 2026)

**Goal.** Lay the foundational persona content and stand up the engineering scaffolding so Phase 1 can sprint.

**Deliverables.**
- 12 Moloco persona dossiers, hand-authored, each grounded in 2+ Moloco user-research interview transcripts and 2+ public-domain texts from the OpenCosmos corpus.
- A documented set of 6–10 skill axes that explain variance in how Growth Managers use the product.
- The `signalarray` monorepo initialized, with Turborepo + pnpm workspaces, the `@opencosmos/*` packages installed, and the `apps/web` placeholder deployed to `opencosmos.ai/signalarray`.
- Neon Postgres provisioned with Drizzle migrations for the persona, scenario, and trace schemas.

**Dependencies.**
- Access to Moloco user-research transcripts (request from Bert in the kickoff conversation).
- Decisions on which OpenCosmos corpus texts ground which persona archetypes (Adam Smith for market-aware GMs, Marcus Aurelius for discipline-under-uncertainty, etc.).

**Success criteria.**
- 12 persona dossiers exist in `packs/moloco-ads/personas/`, each passing the grounding-source-link validator.
- `opencosmos.ai/signalarray` loads (even with placeholder copy).
- Monorepo `pnpm install && pnpm build` succeeds cleanly.

**Risks.** Persona grounding takes longer than expected; the Moloco transcript access is delayed. Mitigation: parallelize — start scaffolding work immediately while transcript access is being arranged.

---

## Phase 1 — Single-session MVP · Weeks 2–3 (May 22 – June 5, 2026)

**Goal.** Get one persona running end-to-end against a real Moloco design surface, producing a structured trace and rendering in a barebones console.

**Deliverables.**
- `packages/kernel` minimum: persona-conditioning prompt builder, Claude session orchestrator, action capture, trace emitter.
- Anthropic Computer Use integrated as the first browser adapter.
- A bare console at `signalarray.opencosmos.ai/app` (or `opencosmos.ai/signalarray/app`) with: persona picker, scenario picker, target URL field, Run button, trace viewer.
- The first Constellation render: even at 1 persona, the visualization works as a demo moment.
- One successful end-to-end run of the Priya persona against a Figma-Make export of NextGen Ads Manager.

**Dependencies.**
- Phase 0 complete: at least one persona dossier and one scenario authored.
- Anthropic Computer Use access for Signal Array's API key.
- A Figma-Make export or staging URL of a NextGen Ads Manager screen to test against.

**Success criteria.**
- Bert (or his designated representative) watches a live demo of one Priya-persona run.
- The run captures: ≥10 action events, reasoning trace, ≥3 screenshots, hesitation events, completion status.
- The Constellation visualization renders the persona node with its skill-grade cluster coloring and grounding-source edges visible.

**Risks.** Computer Use rate limits or reliability issues on a longer multi-step session. Mitigation: have a Playwright fallback path scaffolded; full Browserbase integration can wait, but a manual Playwright run should be possible in a pinch.

---

## Phase 2 — Judge agent + cohort scaling + Constellation overlays · Weeks 4–5 (June 5–19, 2026)

**Goal.** Move from one persona to a cohort. Add the Judge Agent. Compare A/B design variants.

**Deliverables.**
- `packages/judge`: heuristic loader, per-heuristic scoring rubric, multimodal Claude calls per heuristic, critique deduplication across personas.
- 6–8 Moloco-Ads-specific heuristics authored in `packs/moloco-ads/heuristics/` (algorithmic legibility, trust trajectory, drill-coherence, vocabulary alignment, confidence-to-act, backtrack cost, density tolerance, where-the-user-wanted-to-talk-to-a-Speedboat-agent).
- Inngest workflow wired for cohort runs (12 personas × 1 scenario = 12 parallel sessions).
- Cohort view in the console with Constellation critique-cluster overlays.
- A/B design variant comparison: same scenario, two target URLs, side-by-side cohort results with overlaid critique deltas.

**Dependencies.**
- Phase 1 complete (kernel and basic console working).
- Moloco design team supplies two design variants for the A/B test (one of which can become the Phase 3 calibration scenario).

**Success criteria.**
- A 12-persona × 1-scenario cohort run completes end-to-end in <60 minutes.
- The judge produces critique with ≥80% pass rate on heuristic-scoring consistency checks (same input → same critique with confidence ≥4).
- Bert and the Speedboat team can self-serve a new cohort run from the console.

**Risks.** Cohort run reliability — one persona's run failing shouldn't kill the cohort. Mitigation: durable execution via Inngest with per-persona retry logic; the cohort report should aggregate "12 personas attempted, 11 completed, 1 timed out" honestly.

---

## Phase 3 — Calibration framework + first published report ★ · Weeks 6–8 (June 19 – July 10, 2026)

**Goal.** Ship the credibility-defining artifact: the Moloco calibration report. This is the keystone of the entire year.

**Deliverables.**
- `packages/calibration`: comparison metrics (theme-overlap, severity-correlation, false-positive rate, false-negative rate, unique-Signal Array-signal), report generator producing both Markdown + HTML.
- Real-user-finding ingestion format defined; Moloco supplies findings from 3 real GMs on the chosen calibration scenario.
- The first calibration report published at `opencosmos.ai/signalarray/calibration/moloco-001`.
- Internal walkthrough with the Speedboat team confirming the methodology and the findings.
- The public-facing version with pre-approved redactions if any.

**Dependencies.**
- Phase 2 complete (cohort runs producing reliable critique).
- Moloco supplies real-user findings on the calibration scenario.
- Bert agrees to the publication terms (Signal Array brand on the report, Moloco named as design partner).

**Success criteria.**
- The calibration report publishes at the agreed URL by end of Week 8.
- The report shows quantitative agreement/divergence metrics on the chosen scenario, not just narrative.
- At least 3 design-leadership contacts agree to share the report on LinkedIn / Twitter / in their networks.
- The report is the dominant search result for "Signal Array calibration" within 14 days of publication.

**Risks.** The calibration metrics show Signal Array did poorly. *This is the correct response: publish anyway with honest analysis.* The credibility of the calibration discipline comes from showing the math; suppressing a bad result would be category-damaging. Mitigation: agree with Bert in advance that publication happens regardless of outcome, with the framing being "Signal Array's measured strengths and weaknesses on this scenario."

---

## Phase 4 — Creative Portfolios public demo · Weeks 9–12 (July 10 – August 7, 2026)

**Goal under the reorientation.** Ship the methodology in public as a gift to the design community. The demo demonstrates what calibration-disciplined synthetic UX research looks like, to anyone curious, without becoming a top-of-funnel lead-gen surface.

**Deliverables.**
- `apps/portfolios` Next.js surface at `opencosmos.ai/signalarray/portfolios`.
- 8 portfolio-vertical personas authored (Senior Recruiter, Junior Recruiter, Art Director, Brand Strategist, Hiring Designer, ECD, Startup Hiring Manager, In-House Brand Lead) with public-domain second-order grounding from the Whitman / Emerson / Aristotle corner of the OpenCosmos corpus.
- 3 scenarios ("90-second portfolio scan," "find the best work," "decide if you'd reach out").
- 5 portfolio-domain heuristics (first-impression coherence, narrative legibility, contact clarity, originality signal, recency signal).
- Terra-themed visual identity for the portfolios surface (distinct from the Studio-themed `/signalarray` main).
- A small soft-launch announcement (1–2 posts) on design Twitter / Read.cv / LinkedIn. The fuller content calendar in the dormant *Marketing & GTM Plan* (in `superseded/`) has been retired.

**Dependencies.**
- Phase 3 complete; calibration report exists as the credibility anchor.
- The Pack SDK has matured enough to support a second pack without code changes to the kernel.

**Success criteria.**
- The demo accepts a portfolio URL and returns 50 synthetic critiques in <10 minutes.
- The demo handles 100+ concurrent runs without degradation.
- The demo stays running and free to the design community indefinitely.

**Watch metric (not a success criterion):** unsolicited inbound commercial inquiries received within ~60 days of launch. Per *00-REORIENTATION*, 3+ qualifying inquiries is one of the reactivation triggers that would warrant revisiting the dormant docs. Track for awareness; don't optimize for.

**Risks.** Cost spike from public-demo traffic. Mitigation: rate limit per IP, queue runs behind a "you're in line" UI affordance, hard cap LLM spend per day with graceful degradation.

---

## Phase 5 — Post-contract window: CHI paper + Moloco contract decision · Months 4–6 (August – October 2026)

**Goal under the reorientation.** This phase, in the original plan, was about landing a second commercial customer in parallel with the CHI paper. Under *00-REORIENTATION*, the second-customer commitment is **retired as a required milestone** and becomes a latent option triggered only by self-arriving inbound. The CHI paper remains the active commitment for this window; the post-July Moloco contract status is the other live item.

**Active deliverables.**
- The CHI 2027 paper drafted and submitted by the September 11, 2026 deadline. Co-authored with Moloco contact if Bert is willing. Paper title likely *"Calibrated synthetic UX research: two-layer grounding and cohort visualization for expert B2B software."* See *Signal Array — CHI 2027 Paper Outline*.
- Moloco contract status resolved: extended, restructured, or concluded. Documented in the Operating Cadence quarterly review.
- OpenCosmos and Creative Powerup visibly recovering the hours reclaimed under the bursty allocation (more contributions to the corpus, more package improvements landing, more community programming).

**Latent deliverables** (only if a reactivation trigger fires per *00-REORIENTATION*):
- A second commercial pack scope, signed engagement, and pack-authoring start. Pull the original dormant *Business Plan* in `superseded/` for the multi-customer pricing and pack-content guidance if this happens.

**Dependencies.**
- Phase 3 complete; calibration report exists as the empirical foundation for the CHI paper's Section 4.
- Bert/Moloco's willingness to co-author the CHI paper (boosts acceptance odds; ask in week 1 of the engagement, not in August).

**Success criteria.**
- CHI 2027 paper submitted on time.
- Moloco contract status resolved with intentionality, not by drift.
- The non-contract weekly allocation actually shows up in practice (per the Operating Cadence integrity check).
- No SaaS-shaped commitments made absent a reactivation trigger.

**Risks.** The CHI paper not shipping is now Risk 1.6 in the Risk Register; see for mitigations. Reorientation creep (Signal Array hours quietly expanding back to 60% during non-contract weeks) is the watch trigger in Risk 4.1 and the integrity check in Operating Cadence Section 8.

---

## Phase 6 — *Removed under the reorientation*

The original Phase 6 was about choosing among four commercial paths (bootstrap / pre-seed raise / strategic tuck-in / expanded Moloco engagement) at month 12, using accumulated evidence from a second commercial pack and the CHI paper outcome.

Under *00-REORIENTATION*, the answer is structurally **bootstrap, solo, methodology-as-consulting**. The other three paths require external conditions that aren't expected to materialize and that the reorientation isn't pursuing. The question of funding posture doesn't get asked at month 12; it remains closed until one of the reactivation triggers in *00-REORIENTATION* is met.

The original Phase 6 deliverables — pitch deck assembly, acquisition conversations, expanded-engagement negotiations — are preserved in the dormant *Business Plan* in `superseded/`. If any of them ever become relevant again, restart strategic thinking from there.

---

## Key dependencies map

The chain of dependencies under the reorientation:

```
1. Moloco transcript access → Persona grounding → Phase 0
2. Phase 0 personas → Phase 1 MVP run
3. Phase 1 working → Phase 2 cohort
4. Phase 2 cohort + heuristics → Phase 3 calibration data
5. Phase 3 report → Phase 4 demo + CHI paper evidence
6. Phase 3 report → Bert's contract-extension conversation
7. CHI paper writing window (Phase 5) → CHI 2027 submission
```

**Critical-path items (delay these and the year compresses badly):**
- Moloco transcript access (Phase 0)
- Phase 3 calibration report publication (anchor for both Phase 4 demo and the CHI paper's empirical section)
- CHI submission deadline (September 11, 2026 — non-negotiable date)

**Items with slack (some delay is recoverable):**
- The Creative Portfolios demo can shift by 1–2 weeks if calibration takes longer.
- The CHI paper can wait for 2028 if 2027 submission isn't ready (the paper still has value as a working draft; arXiv preprint is the bridge).

---

## Year-end self-assessment

At the end of April 2027, the question to ask: did the reorientation hold, and did the methodology earn its place?

**Strong yes (reorientation is healthy):**
- Moloco-001 calibration report published with credible signal; CHI 2027 paper submitted (acceptance pending or accepted); Creative Portfolios demo live and visited; OpenCosmos visibly healthier than at the start of the year; Creative Powerup community engaged; family well; rested.

**Mixed (reorientation is partially landed):**
- Moloco-001 published but calibration showing partial signal; CHI paper submitted at an alternate venue (DIS / IUI / CSCW); OpenCosmos and Creative Powerup recovering but not yet visibly thriving. Continue at the reorientation cadence; refine the bursty allocation based on what didn't hold.

**Reconsider the methodology itself:**
- Calibration shows Signal Array doesn't add meaningful signal beyond what existing real-user practices already provide. The artifacts produced (paper, demo, calibration data) remain career-grade outputs and stay published; the methodology needs honest revision before any future engagement. The dormant *Business Plan* in `superseded/` stays dormant indefinitely.

**Reactivation triggered (not currently expected):**
- A reactivation trigger from *00-REORIENTATION* has fired — 3+ unsolicited inbound inquiries, a credible co-builder partner, a Moloco extension that funds capacity, or a personal-life change that expands the time budget. In this case, reopen the dormant docs *with intention* and re-evaluate the venture-scale plan against the year's actual evidence. Don't simply reactivate the old plan as written; rebuild against current conditions.

---

## Companion documents

- *Signal Array — Platform Vision* — strategic frame.
- *Signal Array — Technical Implementation Plan* — what to build, in what order, on what stack.
- *Signal Array — Business Plan* — commercial structure, revenue model, financial projections.
- *Signal Array — Financial Model.xlsx* — monthly projections with scenarios.
- *Signal Array — Marketing & GTM Plan* — positioning, channels, content, sales motion.
- *Signal Array — Moloco Engagement Pitch* — the customer-facing artifact for Bert.
- *Signal Array — Risk Register* — risks across categories.
- *Signal Array — Operating Cadence* — solo-operator discipline.
- *Signal Array — CHI 2027 Paper Outline* — academic credibility plan.
