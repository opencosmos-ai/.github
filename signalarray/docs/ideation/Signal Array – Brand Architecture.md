# Signal Array — brand architecture
### How OpenCosmos, Creative Powerup, and Signal Array coexist · canonical record of the May 14 decisions

**Author:** Shalom Ormsby (with Claude)
**Date:** 17 May 2026 (light tweaks for reorientation; original 14 May 2026 draft)
**Status:** Canonical. Supersedes the earlier *Name & Feasibility Brief*.
**Companion to:** *00-REORIENTATION*; *Signal Array — Platform Vision*

---

## TL;DR

Three brand surfaces, three audiences, three commercial postures, one creative author. Signal Array is the commercial product, lives at **`opencosmos.ai/signalarray`**, built on OpenCosmos infrastructure. OpenCosmos remains the open labor-of-love gift to humanity. Creative Powerup remains the heart-led subscription community for individual creators. None of them try to be the others.

---

## 1 / The three brand surfaces

**OpenCosmos** — `opencosmos.ai`
- *What it is:* an open, philosophical creative platform built on the recognition that we are not separate from the universe we inhabit.
- *Audience:* anyone curious about AI grounded in wisdom traditions; designers and developers who want the design system; readers of the curated corpus.
- *Commercial posture:* gift. MIT licensed. Generous by design.
- *Brand voice:* contemplative, philosophical, integrative. "Our work is our love made visible."
- *Products inside it:* the Library (corpus + Cosmo dialogue agent), the Studio (component library docs), Dialog, and now Signal Array.

**Creative Powerup** — `creativepowerup.com`
- *What it is:* a heart-led creative community where AI supports (never replaces) human creativity.
- *Audience:* individual creators and purpose-driven innovators.
- *Commercial posture:* subscription. $49/month, $139/quarter, $499/year, plus lifetime.
- *Brand voice:* warm, soul-aligned, community-oriented.
- *Relationship to Signal Array:* operationally and stylistically separate. Could become a distribution channel in late-stage (a "Signal Array for solo designers" tier as a CP benefit) but not a near-term concern.

**Signal Array** — `opencosmos.ai/signalarray`
- *What it is:* a calibration-disciplined methodology for expert-grade synthetic UX research, built on the OpenCosmos ecosystem.
- *Audience:* design leads, UX research VPs, design directors at B2B companies with expert end users.
- *Commercial posture:* methodology deployed via bursty consulting engagements per *00-REORIENTATION*. Income-generating during contract weeks; methodology-curation + CHI paper writing between. Original venture-scale framing preserved in the dormant *Business Plan* in `superseded/`.
- *Brand voice:* B2B-credible, calibration-forward, technically rigorous. Plain and trustworthy. "Calibrated synthetic UX research, grounded in real interviews. Built on OpenCosmos."
- *This year's commercial use case:* Moloco's Ads pack.

---

## 2 / The URL architecture

Signal Array's canonical URL is **`opencosmos.ai/signalarray`**, a peer product surface alongside `/knowledge`, `/studio`, and `/dialog`.

Decisions captured here:

**Why `opencosmos.ai/signalarray` and not `signalarray.opencosmos.ai`.** Matches the existing pattern of opencosmos.ai (Knowledge, Studio, Dialog are all paths, not subdomains). Stronger SEO authority transfer. Reads as "Signal Array is part of OpenCosmos" rather than "Signal Array is hosted by OpenCosmos." Operationally simpler — one deploy, one SSL, one analytics property. The subdomain `signalarray.opencosmos.ai` is held in reserve for when the authenticated paying-customer product app ships.

**Why not a standalone domain.** During the original "synthR" working-title phase, standalone domains were investigated and ruled out: `synthr.io` is held by a DeFi project; `synthr.ai` is taken; `synthr.com` was unclear and likely expensive. The earlier fallback candidate "Drydock" had `.ai` / `.io` / `.com` all taken and didn't resonate stylistically. The rename to "Signal Array" reopened the standalone-domain question briefly (USPTO search came back clean for SIGNAL ARRAY in classes 9 / 35 / 42, and `signalarray.com` / `.ai` were investigated), but standing the product on its own domain would lose the structural lineage to OpenCosmos that became the chief credibility signal. `opencosmos.ai/signalarray` does the brand work without that loss, and the `signalarray.opencosmos.ai` subdomain stays in reserve for the authenticated product app surface.

**Sub-surfaces within `opencosmos.ai/signalarray`:**
- `/signalarray` — marketing landing, B2B-credible voice, pricing, case studies
- `/signalarray/portfolios` — the free public Creative Portfolios demo (Phase 4)
- `/signalarray/calibration/{pack-id}-{case-id}` — published calibration reports, the credibility moat
- `/signalarray/docs` — product documentation
- `/signalarray/app` (or future `signalarray.opencosmos.ai`) — the authenticated customer app surface

**Theming inside Signal Array's surface.** Default to the Studio theme (professional, dense, B2B-credible). Switch to Terra on the `/portfolios` sub-surface (warm, designer-friendly). Volt reserved for special marketing moments.

---

## 3 / The wordmark and tagline

**Wordmark.** **Signal Array** — two words, both capitalized in all formal usage (marketing copy, contracts, slide titles, documentation headers). Lowercase `signalarray` only in URL paths and code identifiers where the convention requires it. The brand-architecture lockup for external-facing materials is **"Signal Array, by OpenCosmos"** — the comma matters; it signals attribution without subordination, the same pattern as "Claude, by Anthropic" or "Next.js, by Vercel."

**Pronunciation.** Standard English — "SIG-nul uh-RAY." No special styling; the two-word, plainly-pronounced form is part of the brand's credibility posture (we're not asking buyers to learn how to say our name).

**Tagline (locked).** ***The signal you need before the decision you can't redo.***

The tagline is load-bearing. It compresses the entire value proposition into one sentence: "signal" carries the calibration / truth / validation thesis; "before the decision" carries the speed advantage (synthetic users surface findings while there's still time to act on them); "you can't redo" carries the expert-B2B context (these aren't five-second consumer tests — these are decisions about complex products with scarce expert users). Use it on the marketing landing page, in the email signature, in the slide deck, on the calibration-report cover sheet.

**Visual identity.** Studio theme (from `@opencosmos/ui`) is the default for `/signalarray` and the authenticated app. Terra theme for `/signalarray/portfolios` (the public Creative Portfolios demo) because the audience and tone shift to warmer designer-facing register. Volt theme reserved for high-energy marketing moments (rare; conference talk slides, product-launch announcements).

**Trademark posture.** USPTO search (May 2026) found no active or pending registrations for SIGNAL ARRAY in classes 9 (software), 35 (advertising/business services), or 42 (research/SaaS). Filing a federal trademark application is now appealing and should happen before the Phase 4 public-demo launch — likely Q3 2026. Until then, the brand operates under the OpenCosmos umbrella with common-law rights through use.

---

## 4 / The OpenCosmos lineage — subtle but structural

The relationship to OpenCosmos shows up in three places, all of them substantive rather than decorative:

**In the URL.** `opencosmos.ai/signalarray` is the credibility signal that doesn't need to be explained.

**In the infrastructure.** Signal Array runs on `@opencosmos/ui` (the component library), `@opencosmos/constellation` (the WebGL cohort visualization), `@opencosmos/tokens` (design tokens), and the `@opencosmos/mcp` discovery pattern. The Signal Array codebase imports from npm; it doesn't fork. Every component refactor in OpenCosmos benefits Signal Array for free.

**In the methodology.** Public-domain texts from the OpenCosmos corpus serve as second-order grounding sources for Signal Array personas (Adam Smith, Marcus Aurelius, Francis Bacon, Aristotle, Sun Tzu, the Quaker testimonies, depending on the vertical archetype). This is grounding methodology nobody else in the synthetic-user category can replicate because nobody else has the corpus.

Visible co-branding stays subtle: a small "Built on OpenCosmos" line in the Signal Array footer, the `opencosmos.ai/signalarray` URL doing the brand work, and the architecture documentation (which interested customers and competitors can read) showing the lineage clearly. No loud cross-promotion. No shared navigation between `/signalarray` and the rest of opencosmos.ai beyond a sensible "back to OpenCosmos" affordance.

---

## 5 / The commercial structure — open foundations, consulting-shaped engagements

Under the reorientation (*00-REORIENTATION*), the open-source/commercial split is preserved but the *commercial* side is shaped as consulting engagements rather than as multi-tenant SaaS. The original open-core SaaS framing (dbt Labs / Sentry / Sourcegraph / Vercel pattern) is preserved in the dormant *Business Plan* in `superseded/`.

**What's open** (under OpenCosmos, MIT): UI components, Constellation renderer, design tokens, MCP discovery pattern, the curated knowledge corpus.

**What's commercial and stays mine:** User Agent runtime, Judge Agent, calibration framework, methodology.

**What's work-for-hire to a client:** per-engagement pack content (personas, scenarios, heuristics specific to that client's product).

**The Moloco contract is simple under this model.** No kernel-rights negotiation is needed because the kernel is already open. The Moloco Ads pack content is work-for-hire and stays Moloco's; the Signal Array application code and methodology stay mine. See *Signal Array — Moloco Engagement Pitch* lines 44–46 for the exact IP split.

**Pricing posture under the reorientation.** Moloco engagement priced under existing contract. No SaaS pricing tiers, no recurring license model, no platform pricing. Future engagements (if a reactivation trigger fires) are consulting-scale per-engagement deals. The tiered platform pricing originally drafted is preserved in the dormant *Marketing & GTM Plan* in `superseded/`.

---

## 6 / What this decision retired

**The "synthR" working title.** The original product working title was "synthR" (synthetic Research). The rename to "Signal Array" was made for three reasons: synthR didn't carry the calibration / truth / validation thesis on its own ("synthetic" was the only dimension it evoked); a DeFi project owns the synthR brand on synthr.io with active funding and presence; and Signal Array hits at least three of the dimensions we wanted the name to evoke (rigor, multi-agent cohort behavior, signal-to-noise as a research-discipline metaphor). The earlier *Name & Feasibility Brief* (now in `/assets/superseded/`) documents the full alternative-name search.

**The standalone-brand question.** The earlier brief explored standalone brand options, DeFi-collision risk, fallback names (Drydock, Lyceum, Cohortly), and `.ai` vs `.com`. All of that became moot once the architecture landed on `opencosmos.ai/signalarray`. The brand-architecture-with-attribution lockup ("Signal Array, by OpenCosmos") is structurally stronger than any standalone-brand variant would have been.

**The kernel-rights ask.** The earlier *Multi-Vertical Strategy* doc treated the Moloco kernel-rights ask as the central commercial-structure question. Open-core resolved it: the kernel is already open. The Moloco conversation simplifies to "Moloco is paying for the Signal Array application and the Moloco-specific pack."

---

## 7 / Operating discipline

Three brands, one solo operator, finite hours. Keeping them clean requires:

- **Voice discipline.** Don't let the contemplative OpenCosmos voice creep into Signal Array's B2B copy. Don't let Signal Array's commercial register pollute Creative Powerup's heart-led community voice. Each surface gets its own writing standard.
- **Audience discipline.** Don't try to sell Signal Array to Creative Powerup members. Don't try to bring B2B procurement conversations into OpenCosmos's Dialog with Cosmo. Each audience finds its own door.
- **Time discipline.** Signal Array is the income-generating priority. OpenCosmos's curation continues at a sustainable cadence. Creative Powerup community work stays bounded. As Signal Array revenue materializes, fund part-time help on OpenCosmos curation — the virtuous loop is the goal.

---

## Sources

- [OpenCosmos](https://opencosmos.ai/)
- [OpenCosmos Knowledge Library](https://opencosmos.ai/knowledge)
- [Creative Powerup](https://creativepowerup.com/)
- [`@opencosmos/ui` on GitHub](https://github.com/shalomormsby/opencosmos-ui)
- [`@opencosmos/constellation` reference manual](https://opencosmos.ai/knowledge/guides/opencosmos-constellation-cosmograph)
- [OpenCosmos ecosystem repository](https://github.com/shalomormsby/opencosmos)
- [Companion: Signal Array — Platform Vision](computer:///Users/shalomormsby/Developer/Signal Array/assets/Signal Array%20%E2%80%93%20Platform%20Vision.md)
