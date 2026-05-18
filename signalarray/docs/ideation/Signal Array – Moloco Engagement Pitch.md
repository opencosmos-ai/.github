# Signal Array — Moloco engagement pitch
### A one-page proposal to Bert · Signal Array for Ads Manager NextGen

**To:** Bert (and Speedboat eng / DS leadership)
**From:** Shalom Ormsby
**Date:** 15 May 2026
**Subject:** Synthetic Growth Manager cohort for NextGen — 8 weeks to a published calibration report

---

## The ask in one sentence

I'd like to spend the next 8 weeks building Signal Array — a synthetic Growth Manager cohort — and running it against the NextGen Ads Manager prototype, producing a published calibration report at the end that we can use to make the upcoming design decisions with more evidence and less guessing.

## What Signal Array is

Twelve hand-authored synthetic Growth Managers, each one grounded in 2–4 real Moloco customer-research interviews and shaped by skill grades on the dimensions that actually predict variance in how GMs use Ads Manager (auction-theory grasp, MMP literacy, AI trust, density tolerance, drill-coherence). A User Agent drives the UI as each persona; a separate Judge Agent reviews the trace against B2B-power-user heuristics we author together. The whole cohort renders as a live WebGL constellation so the team can see, at a glance, where personas cluster and where critique themes light up. Built on the OpenCosmos design system I've been shipping in public for the last year.

## What you get at the end of 8 weeks

**A published calibration report at `opencosmos.ai/signalarray/calibration/moloco-001`.** We pick one design decision in NextGen the team is genuinely uncertain about — ideally one we've already tested with 3 real GMs — and run the same scenario through Signal Array. The report compares the synthetic findings to the real findings honestly: where we agreed, where we diverged, where Signal Array surfaced something real users missed (and vice versa). Published with Moloco named as the launch design partner; redactions on competitive specifics handled per your preferences.

This artifact lives forever. Even if Signal Array turns out to add no signal, the report itself is a publicly-shareable piece of design-leadership rigor under both brands. And if it does add signal — every other design decision in NextGen gets cheaper, faster, and more defensible from that point forward.

## What I need from Moloco

- Access to existing customer-research transcripts and Generative Research form responses (I can read them in the workspace folder — Phase 0 starts as soon as I have the green light).
- 30 minutes with you to align on whether this is on-strategy enough to spend a sprint on, plus the commercial structure.
- ~10 hours/week of one Speedboat engineer during weeks 2–5 to pair on the Browserbase / Computer Use plumbing.
- One specific NextGen design decision we want as the Phase 3 calibration scenario — somewhere the team is genuinely uncertain.
- Agreement that the calibration report publishes regardless of outcome. The credibility comes from showing the math; suppressing a bad result would defeat the purpose.

## Timeline

| Week | Milestone |
|---|---|
| 1 | Persona grounding: 12 dossiers authored from existing Moloco transcripts. |
| 2–3 | Single-persona MVP. Demo to you at end of week 3. |
| 4–5 | Full 12-persona cohort + Judge Agent. A/B comparison of two NextGen design variants. |
| 6–8 | Calibration scenario run + report published at `opencosmos.ai/signalarray/calibration/moloco-001`. |

## Commercial structure

Signal Array is the commercial application of the OpenCosmos ecosystem I've been building publicly. The open foundations (`@opencosmos/ui`, `@opencosmos/constellation`, the design tokens, the MCP server, the curated knowledge corpus) stay open and MIT-licensed. The Signal Array application — the User Agent runtime, the Judge Agent, the calibration framework, the Moloco Ads pack content — is commercial.

For this engagement specifically: Moloco gets unlimited internal use of the Ads pack and the hosted Signal Array application for the contract term. The pack content (personas, scenarios, heuristics specific to Moloco's product) is work-for-hire and stays Moloco's. The Signal Array application code itself and the methodology I'm developing remain mine. The calibration report names Moloco as originating design partner unless you prefer otherwise.

There's no kernel-rights negotiation needed because the kernel is already open. Anyone — including Moloco's engineering team — can audit how Signal Array is built; what's commercial is the methodology, the pack content, and the hosted operation.

## Why this matters now

NextGen is going to ship to a real customer base that's small, expert, and unforgiving. Real-user research is slow at this scale; the team has more design decisions to make than the calendar can support. Signal Array is the layer that lets the team triangulate faster — generating defensible hypotheses to take into real-user sessions, catching the obvious failure modes before they reach a customer, and producing audit trails for design-review meetings.

The Moloco engagement is also Signal Array's first commercial use case. Being the originating design partner positions Moloco's design leadership as the published case study for a methodology I'm developing — one that may spread organically across the B2B SaaS design community over the next 2–3 years through the calibration report and the CHI 2027 paper, which I'm planning to submit co-authored with whoever from Moloco wants to contribute.

## Three honest things

1. **Signal Array is not a replacement for real research.** It's hypothesis-generation, fast and cheap, with measured accuracy. Real expert customers still tell us the truth at the end of the day. Every Signal Array surface ships with this disclosure in plain language.

2. **The Phase 3 calibration is designed to find out where Signal Array fails.** That's a feature, not a bug. The published divergence is what makes the agreement meaningful elsewhere.

3. **This costs Moloco essentially nothing extra to do well.** The work fits inside the existing design-contract scope; the only marginal cost is a few hours of Speedboat engineer pairing and your 30 minutes upfront. The upside if calibration lands is a design-research force-multiplier that compounds across the next 12 months of NextGen launches.

---

## Next step

A 30-minute conversation. Bring the team if useful. I'll come with the Signal Array Platform Vision doc, the Phase 0 persona-grounding plan tuned to the transcripts I've already started reviewing, and a candidate list of NextGen design decisions that could anchor the Phase 3 calibration.

Times that work for me this week: [INSERT WHEN SCHEDULING].

Looking forward to it.

— Shalom

---

> **Signal Array, by OpenCosmos**
> *The signal you need before the decision you can't redo.*
> `opencosmos.ai/signalarray`

---

**Companion documents (available on request):**
- *Signal Array — Platform Vision* (strategic frame)
- *Signal Array — Technical Implementation Plan* (build detail)
- *Signal Array — Business Plan* (commercial structure including the lighthouse-customer terms)
- *Signal Array — 12-Month Roadmap* (full year context beyond the 8-week engagement)
- `opencosmos.ai` (open infrastructure Signal Array is built on)
- `github.com/shalomormsby/opencosmos-ui` (the component library shipping at npm)
