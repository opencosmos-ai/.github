# Signal Array — CHI 2027 paper outline
### Calibrated synthetic UX research for expert B2B software · paper structure & submission plan

**Author:** Shalom Ormsby (with Claude); co-authorship to be negotiated with Moloco research contact
**Date:** 15 May 2026
**Target venue:** CHI 2027 (ACM Conference on Human Factors in Computing Systems)
**Submission deadline:** September 11, 2026 (anticipated; verify exact date when CHI 2027 call opens)
**Status:** Outline. Full draft begins after the Phase 3 calibration report (early August 2026).

---

## TL;DR

A full paper (CHI Papers track, ~10–12 pages) presenting Signal Array's methodology and the Moloco calibration case study as evidence for a new approach to synthetic UX research: **two-layer interview-and-textual grounding + a separated user/judge agent architecture + published calibration discipline**, applied to expert B2B software where real-user recruitment is the bottleneck. The contribution is not the existence of synthetic users (that's been established by UXAgent, AgentA/B, Park et al.) but a methodology that makes synthetic UX research *credible enough for expert-grade B2B contexts*, with a working commercial deployment as the empirical basis. Co-authored with Moloco's design / research leadership where possible.

---

## 1 / Paper title (candidate)

**"Calibrated synthetic UX research: two-layer grounding and cohort visualization for expert B2B software"**

Alternates to consider:
- *"From skeptical to credible: methodology for synthetic UX research in expert B2B contexts."*
- *"The calibration report: making synthetic UX research auditable, vertical by vertical."*

The selected title puts the contribution (calibration + grounding) first and the application (expert B2B) second; reviewers reading the title alone understand what's novel.

---

## 2 / Abstract draft

> Recent work on LLM-agent-based synthetic UX research (UXAgent, Park et al. 2024, AgentA/B) has demonstrated that synthetic users can generate behavioral signal on prototype UIs. However, deployments in expert B2B contexts — where users have domain expertise that drives most of the variance in UI use, and where real-user recruitment is the practical bottleneck — have remained absent from the literature. We present Signal Array, a methodology and working commercial deployment of synthetic UX research designed specifically for expert B2B software. Three contributions distinguish Signal Array from prior work: (1) a two-layer persona grounding methodology combining real customer-research interview transcripts with curated public-domain texts that shape persona reasoning style; (2) an architectural separation between a User Agent (which drives the UI as a persona) and a Judge Agent (which evaluates the resulting trace against vertical-specific heuristics), enabling independent improvement of behavioral fidelity and critique quality; (3) a published calibration framework that systematically compares synthetic findings to real-user findings on the same scenarios, with results publicly available per vertical. We deployed Signal Array with Moloco, a programmatic-advertising platform, on a usability question concerning their next-generation Ads Manager interface, and report the resulting calibration delta against real Growth Manager findings. We discuss implications for synthetic UX research credibility, the role of calibration discipline in the commercial development of AI-based research tools, and what generalizes (or doesn't) when the methodology is applied to non-ads verticals.

Target abstract length for CHI: 150–250 words. Above is ~280; will trim during drafting.

---

## 3 / Contribution claims (the "what's new" section reviewers look for)

Three distinct contributions, framed for HCI reviewers:

**Contribution 1: Two-layer persona grounding.** Park et al. 2024 showed interview-grounded personas dramatically outperform demographically-derived ones on survey-response replication. We extend this with a second-order grounding in public-domain texts that shape *reasoning style*. Each persona dossier links to both real interview sources (the *who*) and curated public-domain texts (the *how they reason*). We evaluate this empirically against single-grounding controls on the Moloco scenario.

**Contribution 2: User Agent / Judge Agent architectural separation.** Most published synthetic-user systems (UXAgent, AgentA/B, commercial systems Maze and Synthetic Users) use a single agent for both behavior simulation and outcome evaluation. We argue and show that this conflation produces measurable signal degradation, and present an architecture in which the User Agent's only job is to drive the UI as a persona while the Judge Agent's only job is to evaluate the resulting trace against vertical-specific heuristics. Per-heuristic confidence scoring and cross-persona dedup are clean abstractions enabled by this separation.

**Contribution 3: Published per-pack calibration as discipline and brand.** We propose that synthetic UX research products *publish their accuracy* against real-user findings, per vertical, as a routine practice. We describe the calibration framework, the metrics computed (theme-overlap, severity-correlation, false-positive rate, false-negative rate, unique-synthetic-signal), and report initial calibration results from the Moloco deployment. We argue that this discipline addresses the well-documented "synthetic users tilt positive" critique (NN/g, Bisbee, MeasuringU) more credibly than methodology improvements alone.

A fourth, framing contribution worth surfacing in the introduction without claiming it as primary:

**Contribution 4 (framing): Cohort-as-constellation visualization.** We render synthetic cohorts as interactive WebGL knowledge graphs using `@opencosmos/constellation`, with personas as nodes and skill-grade adjacency, mental-model overlap, and grounding-source links as edges. We argue this visualization is uniquely well-suited to communicating cohort composition and run results to research-non-expert design teams, and provide design rationale. We treat this as a contribution-to-product-design rather than a methodological contribution; the CHI audience may appreciate it more in a discussion section than a primary claim.

---

## 4 / Paper structure (CHI Papers format)

**1. Introduction** (~1 page)
- Motivation: real user research bottlenecks in expert B2B; recent synthetic-user work; gap (no expert-grade, calibration-disciplined deployments published).
- Our approach in one paragraph: two-layer grounding + user/judge split + published calibration.
- Contributions summary (the three above).
- Deployment overview: Moloco Ads Manager NextGen case study.

**2. Related Work** (~1.5 pages)
- *Synthetic users in survey/marketing research.* Aaru, Synthetic Users; the polling-tilts-positive critique (Nate Silver, NN/g).
- *Generative agent simulations.* Park et al. 2024 (interview grounding); Centaur (foundation models for cognition; cite the contested 2026 follow-up honestly).
- *LLM-agent-based UX research.* UXAgent (Lu et al. 2025), AgentA/B (Wang et al. 2025); their commercial absence in expert B2B contexts.
- *Multimodal LLM evaluation of UIs.* MLLM-as-UI-Judge (2025), Synthetic Heuristic Evaluation (2025); evidence for the feasibility of agent-based critique.
- *Calibration in human-AI systems.* Citations from cognitive science and HCI on calibrated uncertainty, why we extend it to system-level credibility.

**3. Methodology** (~3 pages, the heart of the paper)
- **3.1 — Persona grounding (two-layer).** The dossier schema. The interview-grounding step. The public-domain-text grounding step with examples (Adam Smith for market-aware reasoning, Marcus Aurelius for discipline-under-uncertainty, Sun Tzu for adversarial strategy). The ethical-curation discipline that constrains us to public-domain texts.
- **3.2 — Skill-graded persona dimensions.** Why demographics fail in expert B2B. How we extract skill axes from interview corpora. Discussion of the Moloco-specific skill axes used.
- **3.3 — Architectural separation.** The User Agent runtime. The Judge Agent runtime. The trace pipeline that connects them. Why the separation matters empirically.
- **3.4 — Calibration framework.** The metrics. The publishing discipline. The per-pack accountability.

**4. Deployment & evaluation: Moloco Ads Manager NextGen** (~3 pages)
- **4.1 — Setting.** Moloco; the Ads Manager NextGen redesign; Growth Manager users; the scarcity of real expert research participants.
- **4.2 — The Moloco Ads pack.** 12 personas; the skill axes; the heuristics; the scenarios.
- **4.3 — The chosen calibration scenario.** A specific design decision Moloco tested with both Signal Array and 3 real GMs.
- **4.4 — Results.** Quantitative metrics: theme-overlap, severity-correlation, FP rate, FN rate, unique-synth signal. Qualitative analysis: which findings agreed, which diverged, where Signal Array added unexpected value, where it missed.
- **4.5 — Where Signal Array fell short.** Honest treatment. The publication discipline depends on this section being present and substantive.

**5. Discussion** (~1.5 pages)
- *What generalizes vs. what is Moloco-specific?* Discussion of the second commercial pack (anonymized if necessary).
- *The calibration discipline as commercial moat.* Argument that calibration publishing is structurally similar to the open-source movement's transparency principle.
- *Limits.* What Signal Array doesn't claim. Where real users remain irreplaceable. The bounded-utility framing.
- *Cohort-as-constellation visualization.* The product-design contribution; design rationale.
- *Ethical implications.* Two-layer grounding with attributable sources; the discipline against using copyrighted texts as grounding sources; how customer interview-transcript privacy is preserved.

**6. Conclusion** (~0.5 page)
- The three contributions restated as research community implications.
- Invitation to the community to apply the calibration-publishing discipline to other synthetic-user products.
- Future work: longitudinal calibration tracking, multi-vertical comparison, persona-grounding fidelity studies.

**Acknowledgments, References, Appendices** as standard.

---

## 5 / Authorship & co-authorship strategy

**Primary author:** Shalom Ormsby.

**Anticipated co-authors:**
- One named Moloco contact who participated in the Phase 3 calibration (Bert, or whoever from Speedboat design / research leadership is the right voice).
- Possibly one Moloco research engineer who contributed to the real-user-finding comparison data.

**Approach.**
- Pitch co-authorship to Bert as soon as the Phase 3 calibration plan is greenlit. Frame it as a low-effort credit ("we'll write the paper; you review and contribute on framing").
- Co-authorship boosts paper acceptance odds (industry-academia papers get reviewer favor for real deployment data).
- Moloco gets a tangible academic-credibility artifact; Signal Array gets co-authorship that establishes the deployment as legitimate.
- If Moloco declines or wants to remain anonymous, the paper still publishes with anonymized deployment details; the case-study framing changes from "Moloco" to "an unnamed programmatic-ads platform."

---

## 6 / Production timeline

| Date | Milestone |
|---|---|
| **Aug 10, 2026** | Calibration data finalized; published Moloco calibration report at `opencosmos.ai/signalarray/calibration/moloco-001`. The published report is the empirical basis for paper Section 4. |
| **Aug 11–17** | Draft Sections 1, 2 (intro + related work) — these are mostly literature synthesis. |
| **Aug 18–24** | Draft Section 3 (methodology). |
| **Aug 25–31** | Draft Section 4 (deployment + results), pulling content from the published report. |
| **Sep 1–4** | Draft Sections 5, 6 (discussion + conclusion). |
| **Sep 5–7** | Co-author review pass with Moloco. |
| **Sep 8–10** | Final polish, formatting, reference verification, ACM submission. |
| **Sep 11, 2026** | **Submit to CHI 2027.** |
| **Dec 2026 / Jan 2027** | Reviewer feedback received. |
| **Feb 2027** | Rebuttal phase (if reviewers ask for revisions). |
| **Mar 2027** | Final acceptance / rejection notification. |
| **May 2027** | If accepted: camera-ready version due ahead of conference. |

**Effort budget.** Approximately 60–80 total hours of writing + revision across August + early September. Allocated within the Signal Array weekly cadence as ~12 hours/week for 6 weeks, drawing from the Signal Array allocation rather than other brands.

---

## 7 / If CHI 2027 rejects

CHI is selective; rejection is normal. If the submission is rejected:

- **Publish as preprint** on arXiv (CS.HC category) immediately after rejection. The work is durable regardless of venue.
- **Re-target to a closer-fit venue.** Options ranked: DIS 2027 (June submission), CSCW 2027 (Oct submission), IUI 2027 (Oct submission), UIST 2027 (April 2027 submission). DIS particularly welcomes industry-academia design research papers.
- **Use reviewer feedback** to strengthen the methodology section before resubmission. Many CHI rejections turn into CHI 2028 acceptances after revision.
- **The artifact already exists** in the published calibration report and the OpenCosmos preprint — the paper's primary value is amplification, not the only credibility source.

Rejection doesn't change the commercial trajectory; acceptance accelerates it.

---

## 8 / If CHI 2027 accepts

Acceptance means a podium at CHI 2027 (anticipated April or May 2027). Capitalize:

- **Talk preparation.** A 15–20 minute conference talk based on the paper. Strong visuals from the Constellation cohort viz.
- **Companion blog post** at `opencosmos.ai/signalarray/blog` published the week the talk is given.
- **LinkedIn / Twitter amplification** with Moloco's design team if they're willing.
- **A second talk circuit** in the months following CHI: DesignOps Summit, Enterprise Design Summit, perhaps a research-team internal-talks slot at customer organizations.
- **Strategic press outreach** to design-trade publications (Designer News, UX Collective, Smashing Magazine) timed to the talk.

The CHI acceptance is the strongest possible academic credential for a research-tooling brand. It feeds fundraising conversations, customer-trust signals, and recruiting credibility for years.

---

## 9 / Open methodological questions to address in the paper

These are the questions a careful CHI reviewer will press on. Pre-empting them in the draft:

- **How was the calibration scenario chosen, and could it have been cherry-picked?** Answer: pre-registered with Moloco before any Signal Array run; scenario selected for genuine uncertainty by the design team, not Signal Array convenience.
- **Is the agreement metric inflated by the specific evaluation framework?** Answer: metrics are computed at the level of *theme* (deduplicated semantic clusters of findings), not narrative similarity. The dedup discipline is documented.
- **What's the sample size?** Real-user n=3 in Moloco case; synthetic-user n=12 per scenario × multiple runs. Pre-empt the sample-size critique by being explicit and framing as a methodology demonstration, not a population study.
- **Does the public-domain textual grounding actually change behavior, or is it window-dressing?** Answer: ablation study planned for the methodology section comparing personas with and without second-order textual grounding. Important empirical question to address directly.
- **Why public-domain texts and not contemporary domain literature?** Answer: ethical-curation discipline tied to the OpenCosmos corpus norms. Discussion section can explore whether contemporary texts would improve fidelity at acceptable cost to provenance discipline.

---

## 10 / Appendices for the paper

Likely appendices, included or supplemental:

- **A.** The 12 Moloco persona dossiers (anonymized; structure shown, content redacted if Moloco prefers).
- **B.** The Moloco Ads heuristic library (full prompts).
- **C.** Detailed metrics calculation methodology.
- **D.** Constellation visualization design rationale + screenshots.
- **E.** Reproducibility notes: how to author a comparable pack for a new vertical.

---

## 11 / Beyond CHI 2027

The methodology is rich enough to support a multi-paper arc over 3–5 years. Subsequent papers could explore:

- **Multi-vertical calibration comparison.** Comparing calibration metrics across packs (ads, devtools, legal, healthtech) to understand which heuristics generalize.
- **Persona-grounding fidelity studies.** Empirical investigation of how persona dossier depth affects behavioral fidelity (controlled experiment).
- **Longitudinal calibration tracking.** How calibration metrics evolve as packs mature and tools improve.
- **Cohort-as-constellation visualization studies.** The visualization itself is a research-grade contribution worthy of its own DIS/UIST paper.

Each of these is a year-or-more research project. None of them block CHI 2027 — that paper stands alone — but they provide a strategic publishing roadmap that compounds Signal Array's academic credibility over time.

---

## Companion documents

- *Signal Array — Platform Vision* — strategic frame.
- *Signal Array — Technical Implementation Plan* — methodology grounding.
- *Signal Array — 12-Month Roadmap* — CHI submission slot in Phase 5.
- *Signal Array — Marketing & GTM Plan* — content amplification post-publication.
- The published calibration report at `opencosmos.ai/signalarray/calibration/moloco-001` (after August 10, 2026) — the empirical foundation.
