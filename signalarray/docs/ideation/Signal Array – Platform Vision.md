# Signal Array — the platform vision
### A calibration-disciplined synthetic UX research methodology, built on OpenCosmos · `opencosmos.ai/signalarray`

**Author:** Shalom Ormsby (with Claude)
**Date:** 17 May 2026 (updated to reflect the reorientation; original 14 May 2026 draft framed Signal Array as a venture-scale commercial platform)
**Status:** Canonical document for the Signal Array thesis. Supersedes the earlier *Synthetic GM Cohort Proposal* and *Multi-Vertical Strategy* drafts.
**Audience:** internal (Shalom); a redacted variant goes to Bert as the case for the Moloco engagement.
**Read first:** *00-REORIENTATION*. Under the reorientation, Signal Array is a research methodology deployed via bursty consulting engagements (with the Moloco-001 calibration report and the CHI 2027 paper as the year's anchors), not a venture-scale SaaS platform. The methodology and four moats described in this document remain accurate; the *commercial-platform* framing in Sections 8, 9 (Phases 5–6), 10, and 13 has been pruned to match. The dormant *Business Plan* in `superseded/` retains the original venture-scale framing.

---

## TL;DR

> ***The signal you need before the decision you can't redo.***

**Signal Array, by OpenCosmos** is a calibration-disciplined methodology for expert-grade synthetic UX research, deployed via bursty consulting engagements and built on the OpenCosmos ecosystem. It runs interview-grounded, skill-graded synthetic users against a real product surface, has a separate critic agent score what happened against heuristics written for the domain, and renders the resulting cohort as a live WebGL constellation built on `@opencosmos/constellation`. It lives at `opencosmos.ai/signalarray` as a peer product surface alongside Knowledge, Studio, and Dialog. The first vertical pack — synthetic Growth Managers walking Moloco's next-gen Ads Manager — is this year's commercial use case and the source of the first published calibration report. A free public Creative Portfolios pack follows as the second.

The thesis rests on four commitments the field hasn't placed yet:

1. **Open foundations, calibrated methodology, expert-grade focus.** OpenCosmos provides the open infrastructure (UI components, Constellation visualization, MCP discovery pattern, design philosophy). Signal Array provides the methodology and the application code that consume it — the agent runtime, the calibrated judge, the heuristic libraries, the per-vertical packs. Under the reorientation (*00-REORIENTATION*), this is deployed as consulting engagements rather than as a multi-tenant SaaS; the original venture-scale framing is preserved in the dormant *Business Plan* in `superseded/`.
2. **Synthetic UX research, done well, is a wedge into expert B2B — not consumer.** The expert-skill-graded lane is empty. Every commercial competitor (Maze AI, Synthetic Users, Sprig, Uxia, Brox, Lyssna, Aaru) synthesizes consumer personas; none model how a Senior Growth DS reads a bid landscape, an SRE triages a Datadog dashboard, or an associate lawyer reviews a Harvey redline.
3. **Personas are grounded in real interviews and in public-domain wisdom traditions.** Park et al. 2024 showed interview-grounded personas hit 85% of test-retest reliability against real human responses. Signal Array's persona dossiers go further: each persona is grounded in 2–4 real interview transcripts *plus* a curated set of public-domain texts from the OpenCosmos corpus that shape its reasoning style. Nobody else in the category has the corpus to do this.
4. **The Constellation cohort visualization is a v1 hero feature, not a v2 polish item.** Every other synthetic-user product renders cohorts as a grid of cards. Signal Array renders the cohort as a WebGL constellation — skill-grade clusters, mental-model adjacencies, persona-grounding edges to source interviews and texts. The visualization is on `@opencosmos/constellation`, the same renderer that powers OpenCosmos's knowledge graph. Material differentiation, already mostly built.

What you're getting in this doc: the product in one piece, the OpenCosmos foundation it stands on, the architecture, an honest read on the 2026 competitive landscape, the build sequence, and the commercial structure. The Moloco-specific IC-mode proposal stays in its companion doc; this one is the platform-level frame.

---

## 1 / The shape of the problem

Designers of complex software keep shipping work that's been "validated" on the wrong audience. Real expert users — Growth Managers, SREs, clinicians, traders, ops leads — are scarce and expensive to recruit. The available shortcuts (Maze, Synthetic Users, Aaru, Sprig) all flatten the very thing that matters: how a person's domain expertise warps the way they use the UI. Output is design feedback that tilts confidently positive and clusters around the polling average baked into LLM training data. Signal Array exists because the gap between "we tested it with synthetic users" and "real experts can actually use it" should be small, measured, and shrinking — not assumed away.

---

## 2 / What Signal Array is, concretely

Three primitives, two agents, one console, one visualization. All of it lives at `opencosmos.ai/signalarray` and inherits the OpenCosmos design and infrastructure layer.

**The Cohort.** A library of synthetic users, each a JSON dossier grounded in 2–4 real interview transcripts from the relevant domain *and* a curated set of public-domain texts that shape its reasoning style. Each persona has identity, skill grades on the dimensions that explain variance in that domain, mental models, tools it trusts, vocabulary it uses, frustrations it has voiced, and explicit links back to both its interview grounding and its textual grounding. Skill grades — not demographics — are the heart of the design.

**The Scenario.** A task we want tested, expressed naturally ("set up a new ROAS-goaled campaign with $50K daily budget"). Scenarios have a target surface (any DOM-accessible UI — Figma export, staging build, screenshot stream), a success definition, and optional checkpoints.

**The Target.** Whatever the design team wants tested — usually a prototype variant, sometimes a live build, sometimes two versions side-by-side.

**The User Agent** picks up a persona + a scenario + a target. It thinks aloud, takes actions (click, type, scroll, read), and emits a structured trace: action stream, internal reasoning, screenshots, hesitations, completion or failure.

**The Judge Agent** is a separate multimodal LLM that reads the trace + sees what the user saw + applies a vertical-specific heuristic rubric. It produces a critique scored against criteria written for that domain — *algorithmic legibility*, *trust trajectory*, *drill-coherence*, *vocabulary alignment* — and surfaces the most frequent failure modes across the cohort. The separation between user agent and judge agent is structural: the user agent simulates behavior; the judge agent simulates the design critic. Every consumer-grade synthetic-user product conflates these and loses signal because of it.

**The Console** is where designers live. Built on `@opencosmos/ui` (the same component library shipping today). Pick a scenario, pick a slice of the cohort, hit Run. Back come: a completion rate, a confusion-cluster heatmap, the top deduped critique themes, a hesitation timeline, links to individual session traces to spot-check, and — the part nobody else has — the cohort visualized as a live WebGL constellation.

**The Constellation.** Signal Array's signature visualization, built on `@opencosmos/constellation`. The cohort is rendered as a real-time WebGL knowledge graph: each persona is a node, edges connect personas that share skill-grade clusters or mental-model adjacencies, and a separate layer of edges connects each persona to its interview-source dossier and its public-domain textual-grounding sources. Critique clusters from a run are overlaid as colored regions. The whole thing is interactive, zoomable, screenshot-worthy, and — critically — *legible at a glance* in a way that a grid of persona cards never is. Every design review where Signal Array is on screen gets a visualization moment that lands.

---

## 3 / The OpenCosmos foundation — what Signal Array inherits, and what it adds

Signal Array is a commercial product. OpenCosmos is the open infrastructure beneath it. The architectural clarity matters because it's what makes the commercial model defensible, the engineering velocity high, and the brand lineage real rather than decorative.

### What Signal Array inherits from OpenCosmos (MIT, public, already shipping)

- **`@opencosmos/ui`** — the 92+ component library, three themes (Studio for ads/enterprise, Terra for Creative Portfolios, Volt for marketing surfaces), the user-controlled motion system, the accessibility baseline. Every Signal Array console screen is built on these primitives.
- **`@opencosmos/constellation`** — the WebGL knowledge-graph renderer that powers OpenCosmos's corpus visualization. Signal Array uses it to render cohorts, critique clusters, and persona-grounding networks. The infrastructure already exists; Signal Array is the first product to apply it to a commercial use case.
- **`@opencosmos/tokens`** — design tokens (colors, typography, motion curves) that keep the Signal Array surface consistent with the rest of opencosmos.ai.
- **`@opencosmos/mcp`** — the MCP server pattern that lets AI assistants enumerate and use OpenCosmos resources. Signal Array adopts the same pattern for pack discovery and persona enumeration, so that AI tools (Claude Desktop, Cursor, others) can interact with Signal Array cohorts natively.
- **The OpenCosmos design philosophy** — emotionally resonant, user control & freedom, transparent by design, generous by design. Signal Array's product surface honors these in substance: every persona has visible grounding sources, every critique has a confidence rating, every calibration report is published rather than hidden.
- **The OpenCosmos knowledge corpus** — 109+ curated public-domain works (Plato, Marcus Aurelius, Adam Smith, Francis Bacon, the Tao Te Ching, Sun Tzu, Shakespeare, the Quaker testimonies, the Bhagavad Gita, and more). These become available as textual-grounding sources for Signal Array personas in the appropriate verticals.

### What Signal Array adds (proprietary, commercial)

- **The User Agent runtime** — browser-driving agent tuned for fidelity to skill-graded personas, with action-stream and reasoning-trace capture.
- **The Judge Agent runtime** — vertical-specific heuristic libraries, scoring rubrics, critique deduplication, confusion clustering.
- **The Persona Authoring system** — interview-transcript ingestion, skill-axis extraction, textual-grounding curation, dossier generation, grounding-source bookkeeping.
- **The Calibration framework** — the loop that compares Signal Array findings to real-user findings on the same scenarios, publishes per-pack calibration reports, and tracks divergence over time. The credibility moat.
- **The vertical packs** — content libraries per domain (personas, skill axes, heuristics, scenarios, lexicons). The Moloco Ads pack is the first. Each pack is the commercial unit.
- **The hosted SaaS surface** — multi-tenant runs, billing, design-team workspace management, integration with Figma / Browserbase / staging environments.

### The contract between them (three rules)

The kernel of the open-source/commercial split survives only if these are honored:

1. **Signal Array never modifies OpenCosmos infrastructure to suit itself.** If `@opencosmos/ui` needs a new component, it's contributed upstream and lands in OpenCosmos first, where every consumer benefits. Signal Array is downstream of OpenCosmos by design.
2. **All vertical knowledge is data, not code.** Heuristics, personas, scenarios, lexicons — these are content files loaded at runtime, not branched code paths. If Signal Array ever branches on `pack == "ads"` in its core, that's a mistake to be fixed.
3. **The Judge Agent only knows heuristics by name.** Packs supply heuristic definitions + prompt templates + scoring rubrics. The agent runtime is content-agnostic. This is what lets Signal Array add the third, fifth, and tenth vertical pack without rewriting the engine.

---

## 4 / The brand and URL architecture

Signal Array lives at **`opencosmos.ai/signalarray`** as a peer product surface alongside `/knowledge`, `/studio`, and `/dialog`. This is the canonical URL, the credibility signal, and the operational simplification all in one.

The URL itself does the brand work: a procurement-savvy B2B buyer reads `opencosmos.ai/signalarray` and understands that Signal Array comes from the same hands that ship OpenCosmos. No badge required. The "Made with OpenCosmos" lineage is structural, not decorative.

The Signal Array surface has its own chrome inside opencosmos.ai — its own product navigation, its own pricing page, its own case studies, its own calibration-report archive. It honors the OpenCosmos design philosophy in substance (transparency, accessibility, user control) but speaks in a B2B-credible voice rather than the contemplative voice of the OpenCosmos homepage. The Studio theme is the default skin for `/signalarray`; the Terra theme appears on the Creative Portfolios sub-surface.

The product app itself, when authenticated paying customers arrive, will live at **`signalarray.opencosmos.ai`** or **`app.opencosmos.ai/signalarray`** as the architecture matures. The marketing + docs + calibration-report surface at `opencosmos.ai/signalarray` is the first thing built; the app surface is the second.

The companion brand at `creativepowerup.com` (community subscription for individual creators) stays operationally and stylistically separate. Signal Array's audience and Creative Powerup's audience overlap only at the edges; the brands do not need to converge.

---

## 5 / What's changed in the field since our last pass

The earlier drafts cited UXAgent, Park et al., Centaur, and Aaru as anchors. The picture has sharpened since then.

**The synthetic-user category is no longer empty — but it's still empty where Signal Array is going.** The 2026 market scan shows real platforms now: Maze AI (consumer five-second tests), Synthetic Users (Lisbon, $2–27 per simulated user), Sprig (enterprise feedback + AI synthesis), Uxia (goal-driven AI users on live websites), Brox.ai (persona-driven walkthroughs), Lyssna, Delve AI. Aaru raised a Series A at a $1B headline valuation in December 2025 with ARR under $10M and contracts in the high six figures. Lyssna's industry survey reports 48% of UX researchers cite synthetic users as a 2026 trend they're watching. **The category is no longer speculative; it's just early.**

**The expert-user, calibration-disciplined lane is still wide open.** Every commercial platform synthesizes consumer personas. None grade for domain expertise. None publish calibration reports against real users. None render cohorts as interactive knowledge graphs. None ground personas in public-domain textual traditions. That's four distinct moats Signal Array can occupy simultaneously — and the OpenCosmos infrastructure makes the fourth one nearly free.

**The research base supporting this direction got stronger.** UXAgent is now a full system paper (arXiv 2504.09407) with an open-source GitHub repo — exactly the shape of Signal Array's user-agent runtime, validated externally. Amazon and Northeastern shipped AgentA/B (arXiv 2504.09723) — 1,000 LLM agents running between-subject A/B tests on Amazon.com with directional agreement against a parallel real-user A/B test. The paper's framing is the same as Signal Array's: "not a replacement for real user testing, but a complementary tool to mitigate traffic scarcity, slow iteration, and collaboration challenges."

**Centaur got real and then got contested.** Binz et al.'s *Nature* 2025 paper on a foundation model of human cognition was followed by a 2026 critique from Zhejiang University arguing the result is largely overfitting. **Practical read for Signal Array:** Centaur is not a foundation we bet on. Reaction-time prediction is interesting but premature; it can be a v2 pack-level signal if it ever earns trust.

**The strongest critique of the category got sharper, too.** NN/g, Bisbee, and MeasuringU continue to publish evaluations showing synthetic respondents compress variance and tilt positive. Nate Silver formally excluded "AI polls" from Silver Bulletin in April 2026. **This is fuel for Signal Array's calibration-first posture, not friction against it.**

---

## 6 / The Constellation cohort visualization — v1 hero feature

This deserves its own section because it's the most defensible piece of v1 product surface and the first thing competitors will struggle to replicate. The infrastructure already exists in `@opencosmos/constellation`.

**What the customer sees.** The Signal Array console opens on a live WebGL constellation rendering of the available cohort. Each persona is a node, sized by recency-of-use, colored by primary skill-grade cluster. Edges connect personas that share mental-model overlap or skill-grade adjacency. A separate translucent layer of edges connects each persona to its grounding sources — interview transcripts on one side, public-domain texts from the OpenCosmos corpus on the other. Hover any persona for a card; click for the full dossier. Filter by skill grade, by mental-model cluster, by domain vocabulary — the constellation updates live.

**What happens when a run completes.** The constellation re-renders with critique clusters overlaid as colored regions: which personas hit the same confusion point, where hesitation clusters landed, which heuristics fired across which personas. The completion-rate visualization is not a bar — it's a constellation lit up by completion status. The hesitation timeline is not a chart — it's a temporal play of nodes brightening in the order they paused.

**Why it matters strategically.** Every UX research tool in 2026 renders results as bars, lists, and grids. Signal Array renders them as a knowledge graph that's screenshot-worthy on a Twitter thread, demo-friendly in a sales call, and *legible* in a way that bar charts never are. The Constellation reference manual already lives in the OpenCosmos knowledge base (six-tier hierarchy, LOD settings, styling primitives all documented). Adapting it for cohort rendering is engineering, not invention.

**Critically, this is also a CHI 2027 paper waiting to happen.** "Visualizing synthetic user cohorts as interactive knowledge graphs" co-authored with Moloco lands cleanly in the research conversation and adds another credibility layer.

---

## 7 / Textually-grounded personas — the second-order grounding

Park et al. 2024 showed that grounding LLM personas in real interview transcripts dramatically improves fidelity. Signal Array adopts this as the *first-order* grounding: every persona dossier is anchored in 2–4 real customer-research interview transcripts.

**Signal Array's novel addition** — which only Signal Array can do because of OpenCosmos's curated corpus — is *second-order* grounding in public-domain texts that shape reasoning style. The corpus is already curated, ethically vetted, and structurally available.

Examples from the OpenCosmos corpus, mapped to vertical persona archetypes:

| Vertical | Persona archetype | First-order grounding | Second-order grounding (public-domain) |
|---|---|---|---|
| Ads (Moloco) | Senior Growth DS | 3 Moloco GM interviews | Adam Smith's *Wealth of Nations* (markets, competition); Marcus Aurelius' *Meditations* (discipline under uncertainty); Sun Tzu's *Art of War* (strategy) |
| Ads (Moloco) | Skeptical Junior PM | 2 Moloco PM interviews | Francis Bacon's *Novum Organum* (empiricism); Plato's *Apology* (Socratic skepticism); Hume on inductive reasoning |
| Creative Portfolios | Senior Recruiter | 3 design-recruiter interviews | Aristotle's *Nicomachean Ethics* (practical judgment); Whitman's *Leaves of Grass* (originality, voice); Emerson's *Self-Reliance* |
| Future: Devtools | Pragmatic SRE | 3 SRE interviews | Marcus Aurelius (operational stoicism); Sun Tzu (resource constraint); Bacon (systematic inquiry) |
| Future: Legal | Cautious Associate | 3 associate interviews | Aristotle's *Nicomachean Ethics*; Plato's *Crito* (legal duty); Quaker testimonies (truth-telling under pressure) |

The textual-grounding doesn't replace the interview-grounding — it complements it. The persona's *who they are* comes from real interviews; the persona's *how they reason under uncertainty* gets shaped by texts the persona's real-world archetype would credibly have absorbed across their career.

**Important discipline.** Only public-domain texts enter the corpus as grounding sources. A persona's dossier can *name* contemporary influences (a Senior Growth DS might be described as "thinks like a Kahneman reader" in plain language) without those texts entering the system. This honors the OpenCosmos ethical-curation rules already established in the knowledge base.

This is the methodology the CHI 2027 paper covers: "Two-layer grounding for high-fidelity synthetic UX personas — interview transcripts and public-domain wisdom traditions."

---

## 8 / Verticals — what's active under the reorientation

Two commitments are active; a third is preserved as a latent option.

**This year's commercial use case: Moloco's Ads pack.** First vertical, first calibration case study. Built inside the contracted Moloco engagement; deliverable is a working synthetic-Growth-Manager cohort against the NextGen Ads Manager. Companion document *Signal Array – Moloco Engagement Pitch* covers this. Theme: Studio.

**Public-demo vertical: Creative Portfolios.** Pack #2, designed as a gift to the design community rather than as a lead-gen funnel. Eight personas (Senior Recruiter, Junior Recruiter, Art Director, Brand Strategist, Hiring Designer, ECD, Startup Hiring Manager, In-House Brand Lead). Three scenarios ("90-second portfolio scan," "find the best work," "decide if you'd reach out"). Five heuristics (first-impression coherence, narrative legibility, contact clarity, originality signal, recency signal). Public web app at `opencosmos.ai/signalarray/portfolios` — submit a portfolio URL, get 50 synthetic critiques in 10 minutes. Theme: Terra. Cost: a weekend of work after the kernel exists. Upside: the kernel gets battle-tested against a domain that has nothing in common with ads, the methodology proves itself as not-Moloco-in-disguise, and it becomes publicly demonstrable for the CHI paper's discussion section.

**Third pack: latent option only.** Under the reorientation (*00-REORIENTATION*), a third pack is not on the active plan. The original framing was "access-driven, not TAM-driven" and that remains true if a reactivation trigger fires — a credible inbound from devtools / observability / fintech ops / legal tech could justify a third pack engagement on its own merits. Until one of those arrives, no third pack is pursued.

The deliberate gap between Moloco and Creative Portfolios: Moloco proves the methodology can do hard, paid, expert-grade work; Creative Portfolios proves the same kernel can do light, free, public work. Anyone who sees both knows they're looking at a coherent methodology, not a single client deliverable.

---

## 9 / Build sequence

**Phase 0 — Persona grounding (Week 1).** Pull existing Moloco user-research transcripts and Generative Research form responses. Use Claude to extract 6–10 skill axes that explain variance in how Growth Managers use the product. Curate a public-domain second-order grounding set from the OpenCosmos corpus (Smith, Aurelius, Bacon, Sun Tzu — whichever fit the archetype). Write 12 persona dossiers by hand, each grounded in 2+ interview transcripts and 2+ public-domain texts. Highest-leverage step in the entire plan.

**Phase 1 — Single-session MVP (Weeks 2–3).** One user agent, one persona, one scenario, against a Figma-Make export of NextGen. Use Claude Computer Use or Browserbase + Playwright. Capture trace + screenshots + reasoning. Render in a barebones console built on `@opencosmos/ui`. Wire the first Constellation rendering of the persona dossier — even at 1 persona, the visualization is the demo moment with Bert.

**Phase 2 — Judge agent + cohort scaling + Constellation runs (Weeks 4–5).** Add the judge agent. Author 6–8 ads-domain heuristics. Scale the cohort to 12 personas. Run 20 sessions per design variant. Render critique clusters as live overlays on the Constellation. Compare A/B designs side-by-side.

**Phase 3 — Calibration against real users (Weeks 6–8).** Pick one design decision Moloco has also tested with 3 real GMs. Run the same scenario through Signal Array. Publish the calibration report comparing synthetic findings to real findings — where they agreed, where they diverged, where Signal Array surfaced something real users missed (or vice versa). **This is the credibility-defining artifact.** Published at `opencosmos.ai/signalarray/calibration/moloco-001`. Earns trust or kills the project; either outcome is good.

**Phase 4 — Creative Portfolios public demo (Weeks 9–10).** Ship the second pack as a free public surface at `opencosmos.ai/signalarray/portfolios`. Soft-launch on design Twitter, LinkedIn, Read.cv. Cost: a weekend. The kernel proves itself against a non-ads domain.

**Phase 5 — Post-contract window: CHI paper + Moloco contract decision (Months 4–6).** Under the reorientation, this window is the CHI 2027 paper writing and submission (deadline September 11, 2026) plus the resolution of Moloco contract status post-July. A second commercial pack is a latent option only; not actively pursued. See *Signal Array — 12-Month Roadmap* for details.

**Phase 6 — Removed under the reorientation.** The original funding-posture decision is closed; default is bootstrap, solo, methodology-as-consulting. Reopen only if a reactivation trigger fires per *00-REORIENTATION*.

---

## 10 / The commercial model — open foundations, consulting-shaped engagements

Signal Array under the reorientation uses an **open-foundation / methodology-as-consulting** model. The previous draft framed this as the dbt Labs / Sentry / Vercel open-core SaaS pattern; the dormant *Business Plan* in `superseded/` preserves that framing for the latent option.

**What's open** (under OpenCosmos, MIT): the UI component library, the Constellation renderer, the MCP discovery pattern, the design tokens, the OpenCosmos knowledge corpus. Customers and competitors can see exactly what foundations Signal Array is built on. Every star, every fork, every contribution to the OpenCosmos repos is a vote of trust that compounds into Signal Array's brand.

**What's commercial and stays mine.** The User Agent runtime tuned for skill-grade fidelity, the Judge Agent with calibrated heuristic libraries, the calibration framework, the methodology I'm developing. This is what makes a commercial engagement valuable, and it stays mine even when individual pack content is work-for-hire to a specific client.

**What's work-for-hire** (per the IP split in the Moloco Engagement Pitch, lines 44–46): per-engagement pack content — personas, scenarios, heuristics specific to a client's product. These are the client's. Everything else (application code, methodology, calibration framework) remains mine.

**Engagement structure (Moloco, this year).** Priced under the existing Moloco contract; calibration report publishes by mid-July; methodology IP remains mine; pack content remains Moloco's. See *Signal Array — Moloco Engagement Pitch*.

**Engagement structure (future, if any).** Consulting-scale per-engagement pricing; no recurring license, no SaaS tier, no multi-tenant infrastructure. The dormant *Marketing & GTM Plan* in `superseded/` describes the tiered platform pricing that has been retired.

**Why this model is easier.** No kernel-rights conversation (kernel is open); no procurement complexity around a multi-tenant product (single-tenant per engagement); no recurring-revenue commitment to maintain; the methodology IP that supports the CHI paper and any future engagement stays clean.

---

## 11 / What's defensible

The category will be crowded by 2027. Honest assessment of where Signal Array's real moats live.

**The interview + textual grounding methodology** is the strongest moat. Park et al. 2024 showed grounded personas dominate demographic ones; Signal Array is the only commercial system implementing this at the pack level, with the added second-order grounding in public-domain texts that's only possible because of the OpenCosmos corpus.

**Expert-skill grading** is the second moat. Every other commercial platform's persona is "shopper" or "first-time user." Signal Array's persona is "Senior Growth DS, auction-theory grade 4, AI-trust grade 2, anchors to last-week's pace." Different product category, not a feature.

**The calibration loop is the brand-level moat.** Every pack ships with a published comparison against real-user findings. Competitors who don't publish calibration get to make claims; Signal Array shows its math. The discipline becomes the brand.

**The Constellation cohort visualization is the surface-level moat.** Built on `@opencosmos/constellation`, immediately distinctive, screenshot-friendly, demo-friendly. Competitors would need to build a comparable WebGL knowledge-graph visualization to match — that's months of work and they'd still be playing catch-up against Signal Array's compounding tuning.

**The two-agent architectural split** (user agent + judge agent) produces sharper signal than any single-agent system. UXAgent points at this; AgentA/B implicitly uses it; no commercial product has shipped it as a primitive.

**The OpenCosmos brand lineage** is the cultural moat. Signal Array is the commercial application of a publicly-documented ecosystem with its own philosophy, its own corpus, its own design system. That's a much harder thing to copy than a single product feature.

What **isn't** defensible: the underlying browser-agent infrastructure (Browserbase, Computer Use — commoditizing fast); the "AI synthetic users" category framing (already crowded); most individual heuristics (replicable by anyone reading the public research). The strategic move is to over-invest in methodology and calibration discipline, and to under-invest in things that are commoditizing.

---

## 12 / Risks, limits, and standing disclosures

The category gets damaged by overpromising. Signal Array's launch posture is the opposite. These are baked into the product surface as standing disclosures, not hidden in legal fine print:

- Signal Array is for fast, cheap, hypothesis-generation. It does not predict adoption, NPS, satisfaction, or any aggregate magnitude. Synthetic users compress variance and tilt positive.
- Signal Array cannot replicate emotional response, the misclick, the wrong mental model, or the workflow real users invent. These are why we still need real users.
- A persona without an interview behind it is a stereotype. Every dossier ships with interview grounding-source links visible to the customer.
- Public-domain second-order grounding is a heuristic for reasoning-style, not a claim of cognitive fidelity. It's stated as such in the dossier.
- Centaur and similar foundation-model claims about reaction-time prediction remain unbet on. The category watches the literature; Signal Array doesn't bet the kernel on it.
- The calibration report is the credibility document. Without it, Signal Array is a Maze competitor with marketing claims. With it, Signal Array is the only commercial platform showing where it's right and where it's wrong, by vertical.

---

## 13 / What's still open under the reorientation

**The post-July Moloco contract status.** Extension, restructuring, or conclusion — to be resolved in the July 17 – July 31 buffer window after the calibration report publishes.

**Whether any reactivation triggers fire** (per *00-REORIENTATION*). Currently not expected. If 3+ unsolicited inbound inquiries arrive within ~60 days of Moloco-001 publishing, or if a credible co-builder partner approaches, that becomes the live question.

**Whether the methodology generalizes beyond Moloco's ad-ops vertical.** Currently a theoretical claim grounded in Park et al. 2024; would be empirically tested by a second engagement (latent) or by the CHI paper reviewer feedback.

The original "What's still open" section also listed *funding posture* and *team posture*; both are closed under the reorientation. Solo indefinitely; no funding question on the calendar.

---

## 14 / What I need to start

- 30 minutes from Bert to align that the Moloco Ads pack is on-strategy enough to spend a sprint on. Open-core framing makes the conversation straightforward: Signal Array is commercial; the foundations it stands on are already public at github.com/shalomormsby/opencosmos.
- Access to existing customer-research transcripts and Generative Research form responses.
- One Speedboat engineer paired on the Browserbase / Computer Use plumbing for ~10 hours/week during Phase 1–2.
- One concrete design decision in NextGen Ads Manager that's genuinely uncertain — the Phase 3 calibration scenario.
- Two evenings reserved for the Phase 4 Creative Portfolios public demo.

With those, the single-persona MVP demos in week 2, the Moloco calibration report publishes in week 8, and the public Creative Portfolios pack lands at `opencosmos.ai/signalarray/portfolios` by week 10.

---

## Appendix A — what Signal Array explicitly does not do, and why

- Not a poll generator. Aaru's lane is crowded and stylistically incompatible.
- Not a consumer-app testing tool. Crowded competition + abundant real users + lower WTP.
- Not foundation-model training. Centaur's contested status confirms this isn't a v1 bet.
- Not synthetic users without calibration. Without it, the category will over-trust the output within a quarter. The calibration is the product.
- Not opened in v1 to non-design teams. PMs and sales will want forecasting and adoption prediction; Signal Array can't do those things and will burn trust trying.

---

## Appendix B — companion documents

**Active operational docs (`signalarray/docs/ideation/`):**
- *00-REORIENTATION* — the canonical reorientation record; read first.
- *Signal Array — Platform Vision* (this document) — the methodology thesis.
- *Signal Array — Moloco Engagement Pitch* — the customer-facing artifact for Bert.
- *Signal Array — Brand Architecture* — the OpenCosmos / Creative Powerup / Signal Array brand split and the `opencosmos.ai/signalarray` URL resolution.
- *Signal Array — Technical Implementation Plan* — what to build for the Moloco delivery.
- *Signal Array — CHI 2027 Paper Outline* — the academic track.
- *Signal Array — Operating Cadence* — bursty time allocation across three brands + family.
- *Signal Array — Risk Register* — what could go wrong, slimmed to the reorientation's actual scope.
- *Signal Array — 12-Month Roadmap* — Phases 0–4 in detail.

**Dormant (`signalarray/docs/superseded/`):**
- *Signal Array — Business Plan* — venture-scale commercial structure (reorientation supersedes).
- *Signal Array — Marketing & GTM Plan* — sales motions, funnel, content calendar (reorientation supersedes).
- *Signal Array — Financial Model.xlsx* — 3-year customer-ramp projections (reorientation supersedes).

---

## Sources & reading list

- [OpenCosmos — the platform](https://opencosmos.ai/) — the foundation Signal Array stands on.
- [OpenCosmos Knowledge Library](https://opencosmos.ai/knowledge) — the 109+ public-domain corpus that powers second-order persona grounding.
- [`@opencosmos/ui` on GitHub](https://github.com/shalomormsby/opencosmos-ui) — the component library shipping today.
- [`@opencosmos/constellation` reference manual](https://opencosmos.ai/knowledge/guides/opencosmos-constellation-cosmograph) — the WebGL knowledge-graph renderer behind Signal Array's cohort visualization.
- [OpenCosmos ecosystem repository](https://github.com/shalomormsby/opencosmos) — the consumer apps including portfolio and creative-powerup.
- [UXAgent — Lu et al., Amazon Science (arXiv 2504.09407)](https://arxiv.org/abs/2504.09407) — the user-agent runtime's intellectual ancestor.
- [UXAgent on GitHub](https://github.com/neuhai/UXAgent) — open-source reference.
- [AgentA/B — Wang et al., Amazon / Northeastern (arXiv 2504.09723)](https://arxiv.org/abs/2504.09723) — 1,000-agent A/B test that directionally agreed with a real-user A/B test.
- [Park et al. 2024 — Generative Agent Simulations of 1,000 People (arXiv 2411.10109)](https://arxiv.org/abs/2411.10109) — the case for interview-grounded personas.
- [Binz et al. 2025 — Centaur in *Nature*](https://www.nature.com/articles/s41586-025-09215-4) — original Centaur foundation-model paper.
- [Centaur overfitting critique, ScienceDaily 2026](https://www.sciencedaily.com/releases/2026/04/260429102035.htm) — the skeptical follow-up.
- [Aaru Series A coverage, TechCrunch Dec 2025](https://techcrunch.com/2025/12/05/ai-synthetic-research-startup-aaru-raised-a-series-a-at-a-1b-headline-valuation/) — competitive context.
- [Lyssna — UX research trends 2026](https://www.lyssna.com/blog/ux-research-trends/) — the "48% of researchers" stat.
- [Synthetic Heuristic Evaluation (arXiv 2507.02306)](https://arxiv.org/html/2507.02306v1) — judge-agent heuristic evaluation feasibility.
- [MLLM as a UI Judge (arXiv 2510.08783)](https://arxiv.org/html/2510.08783v1) — judge-agent reliability evidence.
- [NN/g — Evaluating AI-Simulated Behavior](https://www.nngroup.com/articles/ai-simulations-studies/) — the strongest critique of consumer synthetic-user products.
- [Nate Silver — "AI polls are fake polls"](https://www.natesilver.net/p/ai-polls-are-fake-polls) — the strongest critique of Aaru-style approaches.
- [Anthropic Computer Use documentation](https://platform.claude.com/docs/en/agents-and-tools/tool-use/computer-use-tool) — primary browser-layer option.
