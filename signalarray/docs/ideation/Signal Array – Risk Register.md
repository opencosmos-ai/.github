# Signal Array — risk register
### Risks and mitigations across product, market, commercial, operational, financial, reputational, and personal categories

**Author:** Shalom Ormsby (with Claude)
**Date:** 17 May 2026 (rewritten to reflect the reorientation; supersedes the 15 May 2026 draft)
**Status:** Living document. Reviewed quarterly; updated as new risks emerge or existing ones materialize.
**Companion to:** *00-REORIENTATION*; *Signal Array — Platform Vision*; *Signal Array — Operating Cadence*

---

## Note on the reorientation

This register has been rewritten against the reorientation in *00-REORIENTATION*. Several risks from the original draft are no longer applicable because the SaaS-business operations they were predicated on (multi-customer ramp, hiring, multi-tenant infrastructure, funding decision) have been retired. Removed risks: original 3.2 (no second commercial customer by month 6), 3.3 (procurement friction), 3.4 (customer churn higher than projected), 5.1 (Y2 break-even doesn't happen), 5.3 (tax/state nexus). One risk (4.1, solo-operator burnout) is now substantially mitigated *by the reorientation itself*. The dormant *Business Plan* in `superseded/` describes the risk profile of the venture-scale plan if the reactivation triggers in *00-REORIENTATION* are ever met.

---

## How to read this

Each risk is rated on **Likelihood** (Low / Medium / High) and **Impact** (Low / Medium / High / Critical). The combination determines priority — a Critical-impact, High-likelihood risk needs an active mitigation plan with named milestones; a Low-impact, Low-likelihood risk just gets monitored. Mitigation strategies are concrete and actionable, not aspirational.

Color shorthand at a glance:
- 🔴 **High-priority** — High likelihood × Critical/High impact. Active mitigation required.
- 🟡 **Watch** — Medium likelihood or impact. Monitor and have a mitigation ready.
- 🟢 **Background** — Low likelihood and impact. Documented but not actively managed.

---

## 1 / Product & methodology risks

### 1.1 — 🔴 The calibration report shows Signal Array doesn't add signal

**Likelihood:** Medium. **Impact:** Critical.

The Phase 3 calibration scenario could surface that Signal Array's findings on the chosen Moloco design decision diverge significantly from real-user findings, OR that Signal Array's findings are essentially the same as the obvious-first-pass design intuition (i.e., not adding meaningful signal beyond what the design team already had).

**Mitigation.**
- Pick the Phase 3 scenario carefully: somewhere the team is genuinely uncertain (not somewhere they already know the answer).
- Set expectations with Bert upfront: the publication terms include "we publish regardless of outcome." The calibration discipline IS the brand; suppressing a bad result destroys the very thing being built.
- Have the second-pack vertical decision ready to act on: if calibration on Moloco is mixed, the second pack's calibration becomes load-bearing for the platform thesis. If it's also weak, the methodology needs honest revision before the third pack.
- Plan B is real: the artifacts (the published report, the methodology paper, the Creative Portfolios demo) remain durable career-grade outputs even if the commercial trajectory pauses.

### 1.2 — 🟡 Persona grounding doesn't transfer across verticals

**Likelihood:** Medium. **Impact:** High.

The Park et al. 2024 result was on demographic survey responses, not behavioral UI traces. Signal Array's two-layer grounding methodology (interview transcripts + public-domain texts) might work brilliantly for ad ops but poorly for, say, clinician charting. Each vertical's transfer fidelity is an open empirical question.

**Mitigation.**
- The second commercial pack (Phase 5) is precisely the test. Pick a vertical that's *meaningfully different* from ads to stress-test the methodology — not another ads-adjacent domain.
- Be explicit in the second pack's calibration report about what generalized and what didn't.
- The Pack SDK supports vertical-specific persona-conditioning prompt customizations so a struggling vertical can be tuned without changing the engine.

### 1.3 — 🟡 LLM model regression breaks the kernel

**Likelihood:** Low. **Impact:** High.

Anthropic ships new Claude models regularly. A future model could behave noticeably differently in agent contexts, breaking the User Agent's behavioral fidelity or the Judge Agent's heuristic consistency.

**Mitigation.**
- Pin model versions in the kernel config; never auto-upgrade.
- Maintain a regression test suite of deterministic-input → expected-output pairs that runs on every kernel release and every model evaluation.
- Document the model version used in every published calibration report (transparency requirement).
- Maintain a relationship with Anthropic's developer relations to get early signal on model behavior changes.

### 1.4 — 🟡 Constellation visualization performance degrades at scale

**Likelihood:** Medium. **Impact:** Medium.

`@opencosmos/constellation` wraps `cosmos.gl/graph`, which is performant but has limits. At 500+ personas with critique-cluster overlays, rendering may struggle on customer hardware.

**Mitigation.**
- Profile performance during Phase 2 with the 12-persona Moloco cohort.
- Implement level-of-detail (LOD) tiers so distant nodes downsample gracefully.
- Provide a 2D fallback rendering path for low-spec hardware.
- The OpenCosmos Constellation reference manual already documents the six-tier LOD hierarchy; Signal Array inherits this discipline.

### 1.5 — 🟢 The two-agent architecture is wrong

**Likelihood:** Low. **Impact:** High.

The separation between User Agent and Judge Agent is structural. If the empirical evidence suggested that a single-agent or three-agent architecture produced better results, the kernel would need significant refactoring.

**Mitigation.**
- Watch the literature on UXAgent, AgentA/B, and other agent-architecture work; absorb improvements upstream.
- The kernel's agent runtime is abstracted enough that a third agent (e.g., a "context agent" that maintains state across runs) could be added without breaking changes.

### 1.6 — 🟡 The CHI 2027 paper doesn't ship

**Likelihood:** Low–Medium. **Impact:** High.

The CHI paper is the single most valuable Year-1 academic artifact and the durable record of the methodology. Risks to shipping: the calibration data isn't ready in time, the writing window collides with another life event, the co-authorship with Moloco stalls on review, or scope creep makes the draft unmanageable for the CHI format. Under the reorientation, the paper carries more weight than before — it is now the primary public artifact of the methodology, not one of several.

**Mitigation.**
- The Operating Cadence reserves the August–early September window specifically for paper-writing, with Signal Array hours protected accordingly.
- The Phase 3 calibration report is the empirical foundation; if it publishes on schedule (mid-July), the paper's Section 4 writes itself.
- Co-authorship pitch to Bert happens early (week 1 of the engagement), not late, so review time is built into the timeline.
- If CHI 2027 isn't ready, the paper publishes as an arXiv preprint on the same timeline and re-targets to DIS 2027 or CHI 2028. The artifact still exists; only the venue shifts.

---

## 2 / Market & competitive risks

### 2.1 — 🟡 A funded competitor ships an expert-skill-graded pack first

**Likelihood:** Medium. **Impact:** Medium *(was Critical pre-reorientation)*.

Aaru raised $50M+ at $1B in December 2025. Maze, Sprig, Synthetic Users all have capital and engineering resources Signal Array doesn't. Any of them could decide to build an expert-user product and ship it within 6–12 months.

**Why this is less acute under the reorientation.** Signal Array is no longer trying to win the SaaS-category market-share war. The Moloco delivery is a consulting engagement; the CHI paper is a methodology contribution. A funded competitor shipping a comparable expert-grade tool doesn't directly threaten either. The methodology itself stays publishable; calibration discipline stays defensible as a contribution; the OpenCosmos lineage stays distinctive.

**Mitigation.**
- The Moloco-001 calibration report and the CHI 2027 paper are the durable first-mover artifacts; both ship on the existing schedule and don't depend on competitive timing.
- If a competitor ships first, the appropriate response is intellectual engagement (cite their work; compare honestly), not panic.
- This becomes a *reactivation trigger* per *00-REORIENTATION* only if a competitor ships an expert-grade pack AND I see multiple unsolicited inbound inquiries that imply customers want the methodology as a hosted product.

### 2.2 — 🟡 The synthetic-user category collapses on the polling-tilts-positive critique

**Likelihood:** Medium. **Impact:** High.

NN/g, Bisbee, MeasuringU, and Nate Silver have collectively built a strong public case that synthetic users tilt positive and compress variance. If the broader category becomes seen as "fake research," buyers may avoid all synthetic-user tooling regardless of fidelity claims.

**Mitigation.**
- Signal Array's published calibration discipline is the strongest possible response to this critique. We're not arguing against it — we're showing our math.
- Brand voice deliberately *agrees* with the consumer-synthetic-user critique while distinguishing Signal Array's expert-grade methodology.
- Distribute the Moloco calibration report widely as the prototype of "what calibrated synthetic research looks like."

### 2.3 — 🟢 An incumbent integrates synthetic users into existing real-user platforms

**Likelihood:** High. **Impact:** Low *(was Medium pre-reorientation)*.

UserTesting, Maze, Lyssna could each add synthetic-user features to their existing platforms. Under the reorientation this is no longer a competitive threat — Signal Array isn't competing for the same buyers, and an incumbent's "good enough" features don't undermine the value of the Moloco consulting engagement or the CHI paper.

**Mitigation.** None required. Monitor as background; cite incumbent work in the CHI paper where relevant.

### 2.4 — 🟢 Anthropic deprecates Computer Use or significantly changes pricing

**Likelihood:** Low. **Impact:** Medium.

Computer Use is the primary browser-layer adapter. If Anthropic deprecates it or changes pricing significantly, Signal Array's cost structure changes.

**Mitigation.**
- The Browserbase + Playwright adapter is a maintained fallback path. Switching is a one-line config change.
- The browser-layer abstraction in `packages/browser/` is the only place that depends on Computer Use specifically.

---

## 3 / Commercial risks

### 3.1 — 🟡 The Moloco contract doesn't extend beyond July 31, 2026

**Likelihood:** Medium. **Impact:** Medium *(was Critical pre-reorientation)*.

The current Moloco contract ends July 31, 2026. If it doesn't extend, the next stretch of income depends on whatever else Shalom contracts into — design consulting, a self-arriving Signal Array engagement, or a return to the broader Moloco scope on a different basis.

**Why this is less acute under the reorientation.** The Signal Array roadmap no longer assumes the Moloco engagement continues for the rest of the year. The post-July default is non-contract weeks (per the Operating Cadence's bursty allocation), with hours reallocating to OpenCosmos / Creative Powerup / CHI paper writing. Non-extension is a contingency the reorientation is designed to handle gracefully.

**Mitigation.**
- The Moloco-001 calibration report (publishing ~2 weeks before contract end) is portable evidence; if non-extension happens, it remains a strong artifact for the next conversation, wherever it leads.
- The CHI 2027 paper continues regardless of contract status.
- Personal cash reserves (6 months operating expense) make a contract gap workable without financial stress.
- If non-extension is signaled early, surface it in the next Operating Cadence review and adjust the August–September allocation accordingly.

### 3.2 — 🟢 LLM API pricing changes affect Moloco delivery costs

**Likelihood:** Medium. **Impact:** Low *(was Medium pre-reorientation; renumbered from 3.5)*.

Claude API pricing could rise (less likely, given competitive pressure) or fall (more likely). Without recurring SaaS workloads to absorb the cost, this only matters during the Moloco engagement weeks when cohort runs are happening.

**Mitigation.**
- Prompt caching reduces per-run costs 30–50%; implement aggressively in Phase 2.
- If pricing changes meaningfully mid-engagement, the Moloco engagement's API cost is small relative to the contract value; absorb without contract renegotiation.
- Multi-provider abstraction in the kernel's LLM layer remains a future option if Signal Array is ever run in a configuration where API cost is load-bearing.

*Removed under the reorientation: original 3.2 (no second commercial customer by month 6), 3.3 (procurement friction stalls Pilot/Platform deals), 3.4 (customer churn higher than projected). All three were predicated on the multi-customer SaaS ramp that has been retired. See the dormant* Business Plan *in `superseded/` for the original analysis.*

---

## 4 / Operational risks

### 4.1 — 🟡 Solo-operator burnout *(largely mitigated by the reorientation)*

**Likelihood:** Low *(was Medium pre-reorientation)*. **Impact:** Critical.

Running three brands plus paid work plus family is still a meaningful load, but the reorientation explicitly removes the SaaS-business operations layer (sales pipeline, customer success, hiring management, funding conversations, SOC 2 compliance) that was the primary burnout vector under the original plan. The remaining load is closer to "consulting engagements + open-source maintenance + community programming + family," which is sustainable at the new bursty allocation.

**Mitigation.**
- The rewritten *Operating Cadence* enforces the bursty allocation — Signal Array drops to 6 hrs/wk between contracts; OpenCosmos and Creative Powerup get the recovered hours.
- The dormant *Business Plan* and *Marketing & GTM Plan* in `superseded/` are precisely what's been removed from the load. Reactivating them without re-evaluating the energy budget would re-introduce this risk in its original form.
- Annual time-off discipline: at minimum 4 weeks total off-grid per year, including a 2-week stretch.
- **Watch trigger:** if I find myself doing SaaS-shaped work that wasn't asked for (procurement, security questionnaires, multi-customer-support thinking, hiring conversations), that's the signal that this risk is creeping back and the reorientation needs re-internalizing — not that I should staff up to meet the load.

### 4.2 — 🟡 OpenCosmos infrastructure maintenance burden

**Likelihood:** Medium. **Impact:** Medium.

Signal Array depends on `@opencosmos/ui`, `@opencosmos/constellation`, and other packages. Maintenance of those packages is OpenCosmos work (the labor-of-love gift), but Signal Array depends on it continuing.

**Mitigation.**
- Signal Array revenue funds part-time OpenCosmos maintenance as soon as cash flow supports it. This is structural, not aspirational.
- Pin major versions of `@opencosmos/*` packages; absorb breaking changes deliberately.
- Contribute back upstream when Signal Array needs a feature — keeps the open foundation healthy.

### 4.3 — 🟡 Customer data security breach

**Likelihood:** Low. **Impact:** Critical.

Customer-uploaded interview transcripts are sensitive. A breach would be both a legal exposure and an existential brand event.

**Mitigation.**
- Encryption at rest and in transit (standard, default-on with Neon + Cloudflare R2).
- Scoped namespace isolation at the ORM layer — no cross-tenant queries possible.
- No PII in LLM prompts; persona dossiers reference grounding-source IDs, not raw transcript content.
- SOC 2 audit prep with Drata/Vanta in Y2; SOC 2 Type II by mid-Y3.
- Annual penetration test starting Y2.

### 4.4 — 🟡 Single point of failure on Shalom's institutional knowledge

**Likelihood:** Medium. **Impact:** High.

Most of the methodology, pack-authoring practice, customer relationship knowledge, and brand-voice discipline lives in Shalom's head. A health event or extended absence would be hard for any contractor to absorb cold.

**Mitigation.**
- The doc set in `/assets` is the canonical externalized knowledge base. Keep it current.
- Pack-authoring playbook becomes a written checklist starting with the second pack.
- Customer relationship notes live in a shared Notion (initially) or CRM (Y2+).
- Y2 contractor onboarding includes a 2-week pairing intensive.

### 4.5 — 🟢 Vendor lock-in surprises (Neon, Vercel, Inngest)

**Likelihood:** Low. **Impact:** Medium.

Each vendor has the usual lock-in risks (pricing changes, service degradation, acquisition).

**Mitigation.**
- All vendors are interchangeable with standard alternatives (Neon ↔ Supabase / RDS; Vercel ↔ Netlify / Cloudflare; Inngest ↔ Trigger.dev).
- Avoid proprietary features that don't have clean alternatives.
- Annual vendor review as part of Y2/Y3 ops cadence.

---

## 5 / Financial risks

Under the reorientation, the financial-risk surface compresses substantially. There's no SaaS P&L to manage, no multi-customer cash-flow forecast, no multi-state nexus complications from a multi-tenant product. The remaining financial picture is: Moloco contract income (covered by risk 3.1), standard self-employment-tax discipline (handled by the existing accountant), and a 6-month personal cash reserve outside any single engagement.

*Removed under the reorientation: original 5.1 (Y2 break-even doesn't happen on schedule), 5.3 (tax/state nexus complexity from multi-state SaaS). Both were predicated on the venture-scale revenue model and the multi-tenant SaaS structure that have been retired. See the dormant* Business Plan *in `superseded/` for the original analysis.*

### 5.1 — 🟢 Unexpected cost spikes from vendors

**Likelihood:** Low. **Impact:** Low *(renumbered from 5.2)*.

Most costs are USD-denominated and vendor cost spikes are usually graceful (LLM pricing, hosting fees).

**Mitigation.**
- Annual budget review with 15% contingency buffer baked in.
- USD-denominated contracts.

---

## 6 / Reputational risks

### 6.1 — 🔴 A published calibration report is gamed or misinterpreted

**Likelihood:** Low. **Impact:** Critical.

A competitor or critic could cherry-pick a published calibration report's worst metric to claim Signal Array doesn't work. Or — worse — Signal Array could be tempted to fudge a calibration metric to look better, destroying the discipline that's the moat.

**Mitigation.**
- Pre-publish methodology so the metrics aren't reverse-engineerable for cherry-picking — the report explains how each metric is computed.
- Internal-only review of each calibration report before publication includes an explicit "are we tempted to massage this?" check. Document if yes; publish anyway.
- The published report includes a "limitations and caveats" section that pre-empts the obvious critiques.

### 6.2 — 🟡 A customer pack's persona dossiers leak

**Likelihood:** Low. **Impact:** High.

Pack dossiers grounded in real interview transcripts could leak through a security breach, a misconfigured customer workspace, or an accidental open-source push.

**Mitigation.**
- Pack-private content storage with strict access control.
- Sanitization passes on persona dossiers: real names, company specifics, identifying details either redacted or pseudonymized in stored content.
- Customer agreements explicitly cover the data-handling discipline.

### 6.3 — 🟡 OpenCosmos brand event spills over

**Likelihood:** Low. **Impact:** Medium.

A scandal or controversy involving OpenCosmos as a brand (very unlikely given its philosophical posture, but not impossible) could spill negatively onto Signal Array.

**Mitigation.**
- OpenCosmos's existing brand discipline (transparency, generous-by-design) significantly reduces this risk.
- Signal Array's brand voice is distinct enough that customer-facing copy doesn't depend on emotional alignment with the OpenCosmos voice.

### 6.4 — 🟢 CHI 2027 paper rejected

**Likelihood:** Medium. **Impact:** Low.

CHI is highly competitive. Rejection is the norm; it doesn't represent a serious credibility hit.

**Mitigation.**
- The paper draft becomes a working artifact regardless of acceptance — published as a preprint on arXiv or the OpenCosmos blog.
- Resubmit to CHI 2028 if needed; the work continues to compound.
- Alternative venues: DIS, IUI, CSCW for HCI-adjacent submissions.

---

## 7 / Personal risks

### 7.1 — 🟡 Family / health event disrupts execution

**Likelihood:** Medium. **Impact:** High.

A solo operator's plan is inherently fragile to personal events. A serious family health issue or a personal one would derail the timeline.

**Mitigation.**
- Personal cash reserve outside the business (6 months operating expense).
- Customer agreements include reasonable force-majeure clauses.
- Contractor relationships established by Phase 5 reduce single-point-of-failure risk.
- Family-time discipline is non-negotiable; the operating cadence enforces it.

### 7.2 — 🟡 The work itself loses meaning

**Likelihood:** Low. **Impact:** Medium.

A founder who stops believing in the work produces poor work. If Signal Array's mission starts feeling mercenary rather than meaningful, that's a signal worth heeding.

**Mitigation.**
- Annual personal reflection: is this still aligned with the larger life-trajectory?
- The OpenCosmos / Creative Powerup brands as creative-meaning ballast; Signal Array's commercial focus doesn't have to be the only thing.
- Be willing to sunset Signal Array if the work truly stops resonating; the artifacts produced retain value either way.

---

## 8 / Quarterly review cadence

This document is reviewed quarterly:

- **Q3 2026 (Aug)** — after Phase 3 calibration report and Moloco contract end. First real data on product risks; first read on whether a contract extension is in play.
- **Q4 2026 (Nov)** — after CHI paper submission and Creative Portfolios demo launch. Inbound-inquiry baseline established (reactivation-trigger watch).
- **Q1 2027 (Feb)** — CHI 2027 reviewer feedback. Re-evaluate all risks for the next year of operating.
- **Q2 2027 (May)** — anniversary review; full Year-1-of-reorientation retrospective; risk register update for Year 2.

Each review:
1. Re-rate likelihood and impact based on new evidence.
2. Mark mitigations completed; document new mitigations needed.
3. Add risks that have emerged.
4. Sunset risks that are no longer relevant.
5. Check whether any of the *reactivation triggers* in *00-REORIENTATION* are visible on the horizon.

---

## Top-5 priority risks (rolled up)

If only five risks could be tracked weekly under the reorientation, these are the ones:

1. **Moloco-001 calibration doesn't add real signal** (1.1) — gates the methodology's credibility; the publishability of the CHI paper depends on this being honest, not on it being flattering.
2. **CHI 2027 paper doesn't ship** (1.6) — the single most valuable Year-1 academic artifact and the durable public record of the methodology.
3. **Family or health event disrupts execution** (7.1) — the biggest single-operator disruption risk; the reorientation's bursty allocation is built to absorb it but can't fully eliminate it.
4. **Reorientation creep / SaaS-shaped work re-accumulating** (4.1 watch trigger + Operating Cadence integrity check) — the silent erosion of the bursty allocation back toward the original 60%/15%/10% split. Hardest to detect from inside.
5. **A published calibration report is gamed or misinterpreted** (6.1) — methodology integrity is the moat that survives whatever the commercial outcome ends up being.

Items 1 and 5 are about the integrity of the methodology and its published artifacts. Items 2 and 3 are about whether the year's two anchor commitments (Moloco delivery + CHI paper) actually land. Item 4 is about whether the reorientation gets *lived*, not just written. All five are addressable; none are fatal in isolation; their interaction matters more than any one of them alone.
