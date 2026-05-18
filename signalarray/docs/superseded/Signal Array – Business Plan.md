> ## Dormant — preserved for reference
>
> This document is **dormant** per the reorientation in [`../ideation/00-REORIENTATION.md`](../ideation/00-REORIENTATION.md). It describes the original venture-scale plan for Signal Array — three-year customer ramp to $2.5–4M ARR, FTE hiring trajectory, funding-posture decision at month 12. The operating plan now treats Signal Array as a research methodology deployed on bursty consulting engagements, with no SaaS GTM motion, customer-ramp targets, or hiring.
>
> This document is preserved as historical reference and as the baseline from which to restart strategic thinking if the reactivation triggers in *00-REORIENTATION* are ever met. **Do not act on the plans, metrics, or commitments in this document without first re-evaluating against the current reorientation.**

---

# Signal Array — business plan
### Commercial application of the OpenCosmos ecosystem, building toward a venture-grade synthetic UX research business

**Author:** Shalom Ormsby (with Claude)
**Date:** 14 May 2026
**Status:** Working draft; iterates with the first commercial pack and the first calibration report.
**Companion to:** *Signal Array — Platform Vision*; *Signal Array — Financial Model.xlsx*

---

## 1 / Executive summary

Signal Array is a synthetic UX research platform for expert-grade B2B software. It runs interview-grounded, skill-graded synthetic users against real product surfaces, has a separate critic agent score the result against vertical-specific heuristics, and renders cohorts as an interactive WebGL constellation. It lives at `opencosmos.ai/signalarray` as a commercial application of the OpenCosmos ecosystem.

The lighthouse customer is Moloco — synthetic Growth Managers walking the next-gen Ads Manager. The first paying contract is the existing Moloco design engagement. The path from there is well-defined: ship the calibration report in week 8, the free public Creative Portfolios demo in week 10, the second commercial pack in months 4–6, and a third by month 12. The thesis is that the *expert-skill-graded, calibration-disciplined* lane in synthetic UX research is empty, and the OpenCosmos foundations Shalom has already built collapse the engineering cost to enter it.

**Year 1 target: $150–300K revenue, 1–2 commercial customers, 1 published calibration report, 1 viral public demo, 1 CHI 2027 submission.**
**Year 2 target: $750K–1.5M revenue, 4–8 commercial customers, 3–4 calibration reports published, expanded engineering capacity.**
**Year 3 target: $2.5–4M revenue, 12–18 customers, decision point on funding posture (boutique, raise, acquire, or expand-with-Moloco).**

The downside is bounded: even in the worst case, the artifacts produced (a calibration case study with Moloco, a viral free demo, a CHI 2027 paper) are durable, portable, career-grade assets. The upside, if the methodology holds at scale, is a category-defining commercial platform in a market the industry currently estimates at hundreds of millions to low-billions over the next decade.

---

## 2 / Mission, vision, and operating values

**Mission.** Make expert-grade synthetic UX research credible enough that real product teams trust it for hypothesis-generation, and use it to ship better software faster — without compromising on real-user validation where it matters.

**Vision (5-year).** Signal Array is the recognized standard for synthetic UX research in expert B2B software, with packs spanning ads operations, observability, devtools, fintech, legal tech, and healthtech. The calibration report is the credibility currency of the category. OpenCosmos's open foundations are widely adopted across the design-tooling space. Shalom and a small team operate from a position of financial security, with the freedom to keep doing meaningful work indefinitely.

**Operating values.** Inherited from OpenCosmos's design philosophy and adapted for the commercial context:

- **Calibrated, not confident.** Every claim ships with its measured error rate. We publish the calibration. Customers see exactly where we're right and where we're wrong.
- **Grounded, not invented.** Every persona has a real interview behind it. Stereotypes are not personas.
- **Transparent, not opaque.** Customers see the methodology. Competitors see it too. The methodology is the moat *because* we publish the audit trail.
- **Generous in foundations, focused in commerce.** OpenCosmos infrastructure stays open. Signal Array's commercial application is what generates revenue. The split is principled and durable.
- **Sustainable, not heroic.** A solo operator with a family does not pull all-nighters. The operating cadence is designed around long-term throughput, not short-term sprint.

---

## 3 / Market analysis

### 3.1 — Market size and growth

The broader UX research and design tooling market in 2026 is roughly $4–5B globally, growing 8–12% per year. The synthetic-user research sub-segment is small but growing rapidly — Lyssna's 2026 industry survey reports 48% of UX researchers cite synthetic users as a watched trend, second only to AI-assisted analysis.

Direct comparable revenue benchmarks:
- **Aaru** — ARR <$10M at Series A in Dec 2025, $1B headline valuation, contracts in the high six figures.
- **Synthetic Users** — unfunded, Lisbon-based, estimated $1–5M ARR, $2–27 per simulated user.
- **Maze** — broader UX research platform, AI synthetic features added 2026, $40M+ ARR estimated.
- **Sprig** — $30M+ ARR estimated, enterprise feedback + AI analysis.
- **UserTesting** — public company, $190M+ ARR, slowly adding AI synthetic features.

The expert-skill-graded segment within this is empty. There is no commercial product in 2026 modeling Senior Growth Managers, SREs, ops leads, traders, clinicians, or other expert end-users. That's where Signal Array plays.

### 3.2 — Target customer profile

**Primary buyer.** Head of UX Research, Design Director, or VP Design at a B2B SaaS company whose users are scarce experts. Budget authority for $30K–150K research tooling. Frustrated by the velocity of real expert recruitment ("our users are 200 people globally and they're all busy"). Existing tools (Maze, UserTesting, Synthetic Users) feel mass-market to them.

**Top-of-funnel verticals (ranked by access × WTP × competitive whitespace):**
1. **Ad ops / programmatic / DSP/SSP** — Moloco is the lighthouse; AppLovin, Unity Ads, Criteo, The Trade Desk, IPONWEB share the same buyer profile and the same user-scarcity problem.
2. **Observability / SRE tooling** — Datadog, Honeycomb, Grafana, Chronosphere all design dense expert UIs for users that are hard to recruit.
3. **Legal tech** — Harvey, Hebbia, Even.law all target associate lawyers and partners; real-user recruitment is notoriously hard.
4. **Devtools / API consoles / agent platforms** — Vercel, Replit, Linear, Anthropic, OpenAI all design for technical experts; some self-serve, some enterprise.
5. **Fintech ops & trading UIs** — Stripe Atlas, Modern Treasury, Mercury, trading platforms.
6. **Healthtech (clinician charting)** — Highest WTP and regulatory complexity; defer until calibration credibility is established (year 2+).

### 3.3 — Competitive positioning

| Competitor | Strength | Where Signal Array wins |
|---|---|---|
| Aaru | Brand, funding, enterprise sales motion | Aaru does aggregated polling on demographic personas; Signal Array drives the UI as skill-graded experts. Different product. |
| Synthetic Users | Cheap, established, broad use | Consumer personas, no calibration discipline, no expert grading. We're priced higher and credibility is the moat. |
| Maze AI | Distribution, UX-research workflow | Five-second consumer tests + AI summarization. Doesn't model expertise; no calibration loop. |
| Sprig | Enterprise feedback + AI synthesis | Sprig is feedback-first; Signal Array is research-first. Adjacent, not directly competing. |
| Uxia, Brox | AI-driven walkthroughs | Consumer use case, single-agent architecture (no judge split), no expert focus, no calibration. |
| Lyssna, UserTesting (with AI) | Real-user panels with AI augmentation | They're real-user-first; Signal Array is synthetic-first with real-user calibration. Complementary; not directly competing. |

The deliberate moats: expert-skill-graded personas, two-layer grounding (interview transcripts + public-domain textual traditions), the two-agent split, the calibration loop, the Constellation visualization, and the OpenCosmos brand lineage. None of these are easy to replicate in 12 months.

---

## 4 / Product strategy — open-core commercial application

Signal Array is structured as an **open-core commercial product** under the OpenCosmos umbrella.

**What's open** (MIT, hosted at `github.com/shalomormsby/opencosmos-ui`): UI components, Constellation renderer, design tokens, MCP discovery pattern, the curated 109+ document public-domain knowledge corpus. Anyone can use these for any purpose, including building competing tools.

**What's commercial** (proprietary, hosted at `github.com/opencosmos-ai/signalarray` private): User Agent runtime tuned for skill-grade fidelity, Judge Agent with calibrated heuristic libraries, vertical packs (the actual content libraries — Moloco Ads, Creative Portfolios free, future packs), calibration framework, hosted SaaS infrastructure, customer workspace, billing.

**Why this works commercially.** Customers don't pay for what's open; they pay for what's proprietary plus what's hard to operate (the hosted reliability, the per-vertical pack content, the calibration credibility). This is the dbt Labs / Sentry / Sourcegraph / Vercel pattern; well-trodden.

**The customer-trust dividend.** Open foundations means customers can audit Signal Array's methodology themselves. Competitors can too. That's intentional — the methodology is published; the *operational implementation, the pack content, and the calibration discipline* are what we charge for. Open foundations earn trust; commercial application captures value.

---

## 5 / Revenue model and pricing

### 5.1 — Pricing structure

Three commercial tiers, plus the public free Creative Portfolios surface as a top-of-funnel acquisition channel.

| Tier | Audience | Pricing | Includes |
|---|---|---|---|
| **Creative Portfolios (free)** | Designers, design students | $0 | The public demo at `opencosmos.ai/signalarray/portfolios`. Submit a portfolio, get 50 synthetic critiques. No login. |
| **Pilot Pack** | Single team, one vertical, evaluation | $30K one-time + $15K/yr | One custom vertical pack (12–20 personas), one calibration case study, hosted access for one team for one year. |
| **Platform** | Multi-team enterprise | $40K/yr platform license + $40–80K one-time per custom pack + metered runs above 200/mo | All-pack access, white-glove pack authoring, customer-success support, published calibration report per pack, SLAs. |
| **Enterprise** | Large enterprises, regulated industries | Custom (estimated $150K–500K/yr) | Everything in Platform plus dedicated infrastructure, region pinning, SOC 2 evidence, custom heuristic libraries, dedicated implementation support. |

### 5.2 — Revenue mix targets

Year 1: Pilot Packs dominate ($30–60K each × 2 = $60–120K), with the Moloco engagement priced under its existing contract terms (~$80–150K depending on extension). Total target: $150–300K.

Year 2: Platform tier emerges (4 customers × $80K/yr = $320K) plus pack authoring ($40K × 3 = $120K), plus continued Pilot Packs ($90K) and continued Moloco engagement ($200K assumed extension). Total: $750K–1.5M.

Year 3: Platform tier matures (12 customers × $90K = $1.08M), Enterprise emerges (2 customers × $250K = $500K), pack authoring scales ($40K × 6 = $240K), Moloco grows ($300K). Total: $2.5–4M.

### 5.3 — Unit economics

Per Platform customer (Year 2 representative):
- Annual revenue: $80K (license) + $60K (pack authoring, amortized over 2 years) = ~$110K
- Cost of delivery: ~$15K (LLM API + hosting + ~10% of one engineer's time for pack authoring/support)
- Gross margin: ~85%
- CAC (target): ~$20K (combination of outbound, content, and Creative Portfolios funnel)
- Payback period: ~3 months at full ARR
- LTV (assuming 3-year retention): ~$240K → LTV/CAC ratio ~12x at maturity

These are healthy SaaS unit economics. The model is sensitive to LLM API pricing — see the Financial Model for sensitivity scenarios.

---

## 6 / Financial projections (3-year summary)

Full monthly projections live in `Signal Array – Financial Model.xlsx`. Summary view (base scenario):

| | **Year 1 (FY27)** | **Year 2 (FY28)** | **Year 3 (FY29)** | **3Y Total** |
|---|---|---|---|---|
| Revenue (recognized) | $221K | $578K | $1.55M | $2.35M |
| Total costs | $73K | $327K | $905K | $1.30M |
| Net contribution | $148K | $251K | $648K | $1.05M |
| Net margin | 67% | 43% | 42% | 44% |
| Customers (end of year) | 3 | 9 | 22 | — |
| Headcount (FTE-equivalent) | 1 (Shalom) | 1.5–2.0 | 4–5 | — |
| Cumulative cash EOY | $148K | $399K | $1.05M | $1.05M |
| Gross margin (avg) | 96% | 95% | 96% | 96% |

Notes on the base case:
- Year 1 revenue: Moloco engagement at $150K + 2 Pilot Packs at ~$45K each in months 6 and 11.
- Year 2 revenue: continued Moloco at $200K + 4 new Pilot Packs (one-time + hosting) + 2 Platform-tier customers (license + pack authoring) + recurring revenue from Y1 cohort.
- Year 3 revenue: Moloco at $350K + 5 new Pilot Packs + 6 new Platform customers + 2 Enterprise customers + full recurring base from previous years.
- 22 active customers by EOY3 (1 Moloco + 11 Pilot + 8 Platform + 2 Enterprise).

The financial model includes four scenarios (base / conservative / optimistic / downside) togglable by a single cell in the Assumptions sheet. The downside scenario shows what happens if calibration doesn't hold: the Moloco engagement and the free Creative Portfolios demo remain as durable artifacts; Year 2 declines significantly; strategic value lives in the artifacts (paper, free demo, calibration case study), not the cumulative revenue. **The downside is bounded.**

Note vs. earlier targets: the model's base case is more conservative than the speculative Year 2–3 targets I sketched in earlier drafts ($1.1M / $3.2M). The corrected model reflects realistic customer-acquisition pacing for a solo-operator commercial motion with a 4-month average sales cycle. The optimistic scenario (set Assumptions B61 = 3) approaches the earlier speculative targets and represents the "everything lands" upside.

---

## 7 / Cost structure

Year 1 costs (estimated $95K):
- LLM API (Claude): ~$20K. Dominant cost item. Each cohort run uses ~$5–15 in API calls; ~50 runs/month at peak.
- Hosting (Vercel + Neon + Cloudflare R2 + Inngest): ~$8K
- Tooling (Stripe, Clerk, Sentry, PostHog, Resend): ~$5K
- Legal (entity setup, contract review, trademark): ~$15K
- Accounting/tax: ~$6K
- Marketing (no paid acquisition Year 1; conference travel for one CHI submission): ~$5K
- Shalom's commercial-grade design contracting hours allocated to Signal Array: opportunity cost of ~$35K (~10–15hrs/week not allocated to other contracts)

Year 2 costs (estimated $480K) — adds:
- One part-time engineer at $80K-equivalent (contractor or fractional): $96K
- One part-time persona/research curator: $48K
- Marketing scale-up: $30K (paid acquisition tests, content production, conference presence)
- SOC 2 audit prep with Drata/Vanta: $25K
- Higher LLM API + hosting costs scaled to customer base: ~$60K
- Continued personal time at higher allocation: $200K-equivalent

Year 3 costs (estimated $1.4M) — adds:
- 3 FTEs (engineer, pack-authoring lead, customer-success): $400–500K loaded cost
- Marketing scale: $150K
- Compliance, legal, finance, ops: $80K
- Travel, events, partnerships: $60K
- Continued LLM/hosting at $200K+

---

## 8 / Funding strategy

**Phase 0–4 (months 0–10): bootstrap.** Funded by the Moloco engagement contract plus Shalom's existing income. No outside capital. Operating expenses cleared by Moloco engagement cash flow. This is the right posture because (a) cash is available, (b) outside capital would force premature commitments on commercial direction, (c) the artifacts being produced (calibration report, public demo, paper) build leverage for any future raise.

**Phase 5–6 (months 4–12): decision point.** With one calibration report, two paying customers, and one viral free demo, the question of "raise, sell, or remain bootstrapped" becomes real. Four options:

- **Stay bootstrapped.** $750K–1.5M ARR in Year 2 is enough to support Shalom + 1–2 contractors comfortably. Long-term boutique-consultancy posture. Optionality preserved.
- **Pre-seed raise.** $1–3M at $10–15M valuation if metrics support it. Investors would be focused on category emergence and methodology novelty. Aaru's Series A precedent helps; the calibration discipline differentiates. Risk: pulls focus from product to fundraising for 2–4 months.
- **Strategic acquihire.** Maze, Sprig, Synthetic Users, or UserTesting may be acquisitive in this space. Tuck-in valuations in this category have ranged from $3–20M based on team and revenue. A clean exit is plausible by month 18.
- **Expanded Moloco engagement.** Moloco brings Signal Array in-house as a Speedboat-aligned product, Shalom joins permanently or via expanded contract. Caps upside but maximizes cash flow stability.

The architecture deliberately preserves all four doors. The funding decision waits until the data is in.

---

## 9 / Team plan

**Phase 0–3 (months 0–2): solo + Claude.** Shalom is the only operator. Claude handles roughly 40% of the engineering work; persona authoring is human-driven with Claude assistance.

**Phase 4 (months 2–3): solo, public demo ships.** No team changes.

**Phase 5 (months 4–6): part-time additions.** First contractor — an engineer with TypeScript / Next.js fluency, ideally with prior experience in agent infrastructure. ~10–20 hrs/week. Concurrently, a part-time persona/research curator (could be a senior UX researcher contractor) at ~10 hrs/week for the second commercial pack.

**Phase 6 (months 6–12): decision.** Based on commercial trajectory, either hire 2–3 FTEs or remain in part-time-contractor posture. If bootstrapped, hiring is paced by cash flow; if raised, hiring accelerates.

**Year 2 EOY target:** 1.5–2.0 FTE-equivalents (Shalom + 1 engineer contractor + 1 curator contractor).

**Year 3 EOY target:** 4–5 FTEs (Shalom + 1–2 engineers + 1 pack-authoring lead + 1 customer-success + 1 part-time finance/ops).

**Cultural note.** The team posture is designed to honor OpenCosmos's "user control & freedom" principle internally as well as externally. Async-default, remote, sustainable hours, no heroic-overtime culture. Compensation is competitive but not Silicon-Valley-extreme; the trade is meaningful work and equity participation.

---

## 10 / Key milestones (12-month horizon)

| Month | Milestone | Why it matters |
|---|---|---|
| 1 | 12 Moloco personas authored and grounded | The persona-grounding foundation; nothing else works without it |
| 2 | Single-persona MVP demoed to Bert | First proof the methodology runs end-to-end |
| 3 | Cohort of 12 personas running, Judge Agent live | First headline cohort run; first design A/B comparison |
| 4 | Phase 3 calibration report published at `opencosmos.ai/signalarray/calibration/moloco-001` | The credibility-defining artifact |
| 5 | Creative Portfolios public demo live | First external proof of platform-not-Moloco-tool |
| 6 | CHI 2027 paper submission complete | Academic credibility track engaged |
| 7 | First non-Moloco commercial pack signed (Pilot Pack tier) | First commercial validation beyond lighthouse |
| 9 | Second non-Moloco commercial pack delivered | Pattern repeats; pack-authoring playbook proven |
| 10 | First Platform-tier customer signed | Recurring revenue motion begins |
| 12 | $300K+ recognized revenue; 3 customers; 2 calibration reports; CHI paper accepted or rejected | Decision point on funding posture |

---

## 11 / Exit scenarios

**Most likely outcomes, ranked:**

1. **Sustainable bootstrap (probability ~40%).** Year 2 ARR of $750K–1.5M supports Shalom + 1–2 contractors. Continues as a high-margin boutique. Optionality preserved indefinitely.
2. **Pre-seed raise (probability ~25%).** Aaru's precedent and the calibration-discipline differentiator land with the right investor. $1.5–3M at $10–15M, Shalom retains majority control. Hires accelerate, marketing scales, year 3 ARR $4M+.
3. **Strategic tuck-in (probability ~20%).** Maze, Sprig, Synthetic Users, or UserTesting acquires Signal Array for $5–15M, Shalom either joins or stays part-time to oversee transition. Clean exit by month 18–24.
4. **Expanded Moloco engagement (probability ~10%).** Moloco offers a long-term contract or full-time role to keep Signal Array in-house. Caps upside but maximizes stability.
5. **Methodology doesn't hold (probability ~5%).** The calibration report shows Signal Array adds insufficient signal. The artifacts (the paper, the free demo) are still valuable career-grade outputs; the commercial application winds down gracefully. Bounded downside.

The aggregate expected value across these scenarios — given the bounded downside and the meaningful upside — is strongly positive for a project of this scope. The plan is to maximize the time spent in scenarios 1–3 by executing the calibration discipline and the pack-velocity playbook well.

---

## 12 / What success looks like — beyond revenue

The financial picture matters, but a Signal Array that hits $4M ARR but compromises on calibration discipline is a failure. The success criteria that take precedence over revenue targets:

- **Every calibration report ships honest.** No fudged metrics, no hidden divergence. The discipline IS the brand.
- **The OpenCosmos foundations stay open and well-maintained.** Signal Array funds part-time OpenCosmos curation as revenue allows; this is structural, not aspirational.
- **The CHI 2027 paper lands.** Academic credibility compounds over years.
- **The Creative Portfolios demo stays free and high-quality.** It is the most efficient marketing the category will ever produce and it costs essentially nothing to maintain.
- **Shalom and family are well.** Solo-operator businesses that compromise on this rarely produce great work.

If those five hold, the revenue follows. If revenue comes but they don't, the project hasn't succeeded.

---

## Companion documents

- *Signal Array — Platform Vision* — the strategic frame.
- *Signal Array — Technical Implementation Plan* — the build detail.
- *Signal Array — Financial Model.xlsx* — monthly projections, scenarios, unit economics, KPIs.
- *Signal Array — Marketing & GTM Plan* — buyer personas, channels, content calendar.
- *Signal Array — 12-Month Roadmap* — phase-by-phase timeline.
- *Signal Array — Risk Register* — risks and mitigations across categories.
- *Signal Array — Operating Cadence* — solo-operator discipline.
- *Signal Array — CHI 2027 Paper Outline* — academic credibility plan.
