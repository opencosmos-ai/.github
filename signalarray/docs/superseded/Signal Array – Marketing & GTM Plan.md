> ## Dormant — preserved for reference
>
> This document is **dormant** per the reorientation in [`../ideation/00-REORIENTATION.md`](../ideation/00-REORIENTATION.md). It describes the original go-to-market plan for Signal Array — three sales motions (Pilot Pack / Platform / Enterprise), funnel KPIs (contact form submissions, discovery calls, CAC by tier), a 12-month content calendar oriented around lead generation, and a launch sequence assuming a SaaS ramp. The operating plan now treats Signal Array as a research methodology deployed on bursty consulting engagements; there is no active sales motion, no outbound, no pipeline tracking, no CRM.
>
> The Creative Portfolios free demo still ships per the *12-Month Roadmap*, but as a gift to the design community rather than a top-of-funnel acquisition surface. The CHI 2027 paper and the Moloco calibration report are the live "content" outputs.
>
> This document is preserved as historical reference and as the baseline from which to restart GTM thinking if the reactivation triggers in *00-REORIENTATION* are ever met. **Do not act on the plans, metrics, or commitments in this document without first re-evaluating against the current reorientation.**

---

# Signal Array — marketing & go-to-market plan
### Positioning, buyer journey, channels, content, sales motion, and the launch sequence

**Author:** Shalom Ormsby (with Claude)
**Date:** 15 May 2026
**Status:** Working draft. Iterates with first commercial signups and the Phase 4 public-demo launch.
**Companion to:** *Signal Array — Platform Vision*; *Signal Array — Business Plan*

---

## TL;DR

Signal Array's GTM motion is **credibility-first, not scale-first**. The product earns trust through one published calibration report at a time, distributed through three channels: (1) the OpenCosmos halo (built-on lineage, design-community trust), (2) the Creative Portfolios public demo as the top-of-funnel acquisition surface, (3) a CHI 2027 paper as the academic credibility track. Outbound sales lives between Shalom and a small number of warm enterprise design-leadership contacts. Inbound funnel grows from content (case studies, calibration reports, the demo) over the first 12 months. No paid acquisition until Y2. The launch sequence is built around the Moloco calibration report as the anchor moment — every piece of marketing radiates from that artifact.

---

## 1 / Positioning

**Category framing.** Signal Array is in the synthetic UX research category, but the lane it occupies is *expert-grade calibrated synthetic research* — explicitly distinct from consumer-flavored competitors (Maze, Synthetic Users) and polling-flavored competitors (Aaru).

**One-line positioning.** *Calibrated synthetic UX research for expert B2B software. Personas grounded in real interviews. Findings calibrated against real users. Built on OpenCosmos.*

**Three-line elevator pitch.** *Signal Array runs skill-graded synthetic users against your product surface — Senior Growth Managers, SREs, clinicians, ops leads, whoever your real users are. Each persona is grounded in real customer-research interviews. Each cohort run ships with a calibration delta against findings from real users on the same scenarios. You see exactly where Signal Array is right and where it's wrong, by vertical.*

**Tagline (locked).** ***The signal you need before the decision you can't redo.***

The tagline compresses the entire value proposition into one sentence. *"Signal"* carries the calibration / truth / validation thesis. *"Before the decision"* carries the speed advantage — synthetic users surface findings while there's still time to act on them. *"You can't redo"* carries the expert-B2B context — these aren't five-second consumer tests; they're decisions about complex products with scarce expert users and high consequences. Use it on the marketing landing page, in email signatures, on the calibration-report cover sheet, and on every slide deck.

Three alternate framings to deploy in different contexts (not replacements for the locked tagline, but supporting copy):
- *"Calibrated synthetic UX research."* — short-form B2B-credible variant for headlines.
- *"Synthetic users you can trust, because we publish the math."* — competitor-differentiating variant for sales decks.
- *"Expert UX research, before real experts can show up."* — emotional sell to a design lead in a hurry.

**What we are not.** Not a survey tool. Not a polling platform. Not a five-second-test platform. Not a real-user recruitment service. Not a consumer-personas-at-scale service. Each of these is occupied by stronger incumbents and conflating them with Signal Array loses signal.

---

## 2 / Target buyer personas (the real ones, ironically)

Three buyer personas, ranked by likelihood of being the first commercial signal.

### 2.1 — The Design VP at an expert-B2B SaaS

**Title:** VP Design / Head of Design / Chief Design Officer at a B2B SaaS serving expert users.
**Examples:** Bert at Moloco; equivalents at Datadog, Honeycomb, Vercel, Harvey, Hebbia, AppLovin, Stripe Atlas, Mercury, Modern Treasury.
**Context:** owns a design org of 10–50 people; reports to CEO or CPO; design is treated as a strategic function; recruitment of real expert users is acknowledged-painful internally.
**Pain points:**
- "Our users are 200 people globally and they're all busy."
- "Real research takes 6 weeks and we ship every 2."
- "Our existing tooling treats every user as a generic consumer."
**Buying triggers:**
- A major redesign about to launch with uncertainty about expert reception.
- A new product line targeting expert users where customer-research depth is thin.
- A design-org maturity push: they've adopted modern AI tooling internally and are looking for the next force-multiplier.
**Decision criteria (in order):**
1. Calibration credibility — "show me you've measured your own accuracy."
2. Domain fit — "do you understand my users' expertise, or are you generic?"
3. Speed — "can I have findings in a week, not a quarter?"
4. Price — "is it cheaper than recruiting 20 real experts?"
5. Integration — "does it work with our existing prototype tooling?"

This is Bert. Signal Array's lighthouse sale targets exactly this buyer.

### 2.2 — The Head of UX Research at an enterprise

**Title:** Head of UX Research / Senior UX Research Manager / Research Operations Lead.
**Examples:** at Notion, Linear, Atlassian, Salesforce, Workday, Ramp.
**Context:** owns a small UX research team (3–10 people); manages the research-as-a-service intake for product teams; pulled in many directions by competing demands.
**Pain points:**
- "We have a 4-month backlog and product teams are shipping anyway."
- "We can't get enough expert participants to call findings statistically meaningful."
- "Synthetic users we've tried (Maze, Synthetic Users) feel too consumer-grade."
**Buying triggers:**
- Annual research-tooling budget review.
- A product-team escalation demanding "any signal" before launch.
- A successful internal pitch about AI-augmented research practices.
**Decision criteria:**
1. Triangulation story — "does this complement our real-user practice, not replace it?"
2. Methodological rigor — "can my research team defend this in a debrief?"
3. Calibration evidence — "show me you've validated against real users."
4. Tooling integration — "does this slot into our existing repo, our existing analysis pipeline?"

This is the warmer second-wave buyer once the Moloco calibration report exists. Likely the Y2 Pilot Pack flow.

### 2.3 — The Design Director at a category-defining startup

**Title:** Design Director / Head of Design / Founding Designer.
**Examples:** at Anthropic, OpenAI, Replit, Cursor, Granola, Raycast, Linear, Inkeep, Harvey.
**Context:** small team (1–5 designers), no dedicated research function, ships fast, expert users.
**Pain points:**
- "We don't have a research team and we ship every week."
- "Our users are technical experts but we're often guessing at their workflows."
- "I personally don't have time to recruit users; I need a signal in hours, not weeks."
**Buying triggers:**
- A funded growth stage where research-velocity becomes the bottleneck.
- A redesign push.
- Word-of-mouth from a respected peer in the design community.
**Decision criteria:**
1. Speed of insight — "can I run this overnight?"
2. Brand legitimacy — "is this taken seriously in the design community?"
3. Pricing for a small team — "can I expense this without procurement?"
4. The Creative Portfolios demo as a credibility signal — "I tried the free thing and it was sharper than I expected."

This is the lighter-touch buyer who's likely to find Signal Array through the Creative Portfolios demo and convert to a Pilot Pack tier in Y2 or Y3.

---

## 3 / Messaging architecture

The same core message, told three ways for the three buyers.

### To the Design VP (enterprise, lighthouse)

> "Most synthetic UX research treats every user as a generic consumer. Signal Array is different: every persona is a skill-graded expert grounded in real customer-research interviews, every cohort run ships with a calibration delta showing where we agreed with real users and where we didn't. Moloco published their first calibration report at opencosmos.ai/signalarray/calibration/moloco-001. That's the kind of evidence your team can present in a debrief."

Emphasis: rigor, calibration, defensibility, real-world precedent.

### To the Head of UX Research (enterprise research function)

> "Signal Array is the synthetic-research tool your researchers actually trust. We publish our calibration data publicly, by vertical, so you can see exactly where we add signal and where we don't. We're not a replacement for real users — we're the layer that lets you triangulate faster, ship hypotheses to real-user sessions that already filter out the obvious confusion clusters, and stretch your research team's bandwidth without compromising on methodology."

Emphasis: triangulation, methodology, complement (not replace), velocity.

### To the Design Director (small team, fast-shipping)

> "Run your prototype past 50 synthetic expert users in an evening. Each persona is grounded in real interviews. Findings come back with a confidence rating and a heat-map of where they got stuck. Built on OpenCosmos. Pricing starts at $30K for a custom pack of personas tuned to your product."

Emphasis: speed, simplicity, distinctive visual artifact (the Constellation), accessible price point.

### Cross-cutting themes for all three

- **Calibration is the brand.** Every page surfaces it. Every demo references the public calibration archive.
- **Built on OpenCosmos.** Mentioned in the footer or via the URL itself; the lineage is structural.
- **Real interviews behind every persona.** "A persona without an interview behind it is a stereotype." This single line clarifies the difference from competitors.
- **For experts, not consumers.** The category positioning is restated in every marketing surface.

---

## 4 / Channels

Five channels, weighted by phase.

### 4.1 — The Creative Portfolios public demo (Phase 4+, dominant)

The free demo at `opencosmos.ai/signalarray/portfolios` is the most efficient marketing surface Signal Array will ever have. Every designer who tries it experiences the product directly and forms an opinion about whether it's useful. Word-of-mouth flows through design Twitter, LinkedIn, Read.cv, and design Slack communities.

**Cost:** essentially zero after the Phase 4 build (a weekend of work).
**Yield model:** assume 5% of visitors share it; assume 2% of B2B-buyer visitors who try it consider it for a commercial use case; assume 0.5% of that subset becomes a commercial inquiry. At 10,000 visitors in Year 1 (achievable from a few good shares on design Twitter), that's ~10 commercial inquiries; at 100,000 in Year 2 (achievable after CHI submission and continued sharing), ~100 inquiries.

### 4.2 — Calibration reports as content (Phase 3+, dominant)

Each calibration report at `opencosmos.ai/signalarray/calibration/{case-id}` is a piece of content that compounds. It's the artifact that gets shared in design-leadership Slack groups, quoted in newsletters, cited in talks. The first one (Moloco's) is the launch moment for the entire commercial motion.

**Production rhythm:** one per commercial pack, published within 60 days of the pack going live. Year 1 target: 1 (Moloco). Year 2: 4–5. Year 3: 6–8.

**Distribution:**
- Post to the Signal Array landing page and the dedicated calibration archive.
- Share on LinkedIn (Shalom's account, plus invited shares from Bert / Moloco's design leadership).
- Submit to design newsletters (Design Disciplin, UX Collective, Designer News, Sidebar.io).
- Mention in CHI submission and any conference talk.

### 4.3 — The OpenCosmos halo (constant)

The opencosmos.ai parent brand provides authority, trust signals, and discoverability:
- The OpenCosmos GitHub orgs and repos rank in search results for synthetic-user research and AI design tooling.
- The Knowledge corpus brings inbound traffic from philosophy / wisdom / AI-grounding searches.
- The Studio docs surface Signal Array through its component library — developers exploring `@opencosmos/ui` encounter Signal Array as a built-on application.
- The Creative Powerup community brand provides cross-promotional opportunities to individual creators who may evangelize Signal Array to their B2B employers.

This isn't a campaign; it's the structural advantage of having shipped the open foundation before the commercial product.

### 4.4 — Direct outbound to warm enterprise contacts (Phase 4+)

Shalom has a Silicon Valley B2B design network from the Autodesk / Arm / Moloco / startup contracting work. After the Moloco calibration report publishes, the Signal Array pitch becomes credible enough to warm-intro to 10–20 design leaders directly. Conversion is on the order of 1–2 paying customers per quarter from this channel in Year 1–2.

**Outbound playbook:**
- Send the Moloco calibration report as the opening artifact, not a sales deck.
- Ask the question: "Are you working on expert-user research where this kind of methodology would help?"
- Offer a 30-minute conversation, not a demo, in the first message.
- Follow up with a one-pager (see *Signal Array — Moloco Engagement Pitch*) tailored to their vertical.

### 4.5 — CHI 2027 paper (academic credibility track, Phase 5+)

A paper co-authored with Moloco, submitted to CHI 2027, becomes a durable credibility artifact. Two angles for the paper:
- **Methodological:** "Two-layer grounding for high-fidelity synthetic UX personas: interview transcripts and public-domain wisdom traditions."
- **Empirical:** "Cohort-as-constellation: visualizing synthetic user behavior as interactive knowledge graphs."

The paper feeds three downstream marketing efforts: a talk circuit (CHI itself, then DesignOps conferences, then enterprise design summits), citation-driven inbound from researchers studying synthetic users, and a credibility floor for any future fundraising conversation.

### 4.6 — Channels we are NOT pursuing in Year 1

- **Paid acquisition** (LinkedIn Ads, Google Ads, retargeting). Unhealthy at Signal Array's deal sizes until repeatable customer-acquisition signal exists. Revisit Year 2.
- **Cold outbound at volume** (BDR/SDR). Pollutes the credibility-first brand voice; bad ROI at Signal Array's deal sizes. Never (or only with a dedicated and trained partner).
- **Conference sponsorships** at scale. Selective conference *talks* yes; sponsored booths no.
- **Influencer partnerships.** Out of register for B2B research tooling.

---

## 5 / Content calendar (12 months)

Twelve months of substantive content, organized around the Moloco calibration report as the anchor moment.

| Month | Content piece | Channel | Notes |
|---|---|---|---|
| 1 | "Why synthetic UX research keeps failing experts" — essay framing the gap Signal Array fills | LinkedIn + opencosmos.ai blog | Establishes the category positioning before the product exists publicly |
| 2 | "What we mean by skill-graded personas" — methodology explainer with examples | LinkedIn + blog | Builds intellectual credibility for the methodology |
| 3 | "The two-agent split: why we separate user and judge" — technical post | Hacker News + LinkedIn + blog | Technical credibility; AgentA/B / UXAgent citations |
| 4 | **Moloco calibration report v1 publishes** at `opencosmos.ai/signalarray/calibration/moloco-001` | Site + LinkedIn + design newsletters | The single most important marketing event of Year 1 |
| 5 | "Introducing Creative Portfolios: 50 synthetic recruiters review your work" | Twitter/X + Read.cv + design Slack groups | Distribution-grade public demo launch |
| 6 | "The CHI 2027 paper we're writing about Signal Array" — methodology preview | Blog + Twitter | Builds anticipation for the academic credential |
| 7 | First commercial Pilot Pack case study (anonymized if needed) | Blog + LinkedIn | Second piece of customer-validation evidence |
| 8 | "Calibration as the brand: why we publish the math" | Blog | Positioning content that distinguishes from competitors |
| 9 | "Public-domain grounding: how Marcus Aurelius shows up in a Growth Manager persona" | Blog | The unique-to-Signal Array methodology angle |
| 10 | Second calibration report publishes (second commercial pack) | Site + LinkedIn | Pattern repeats; calibration archive grows |
| 11 | "Cohort-as-constellation: rendering synthetic users as interactive knowledge graphs" | Blog + maybe a Hacker News submission | Visual moat; screenshots go viral on Twitter |
| 12 | Year-1-in-review with publicly-shared metrics | Blog + LinkedIn | Anniversary content + transparency play |

**Production discipline.** One substantive piece per month, ~1500–2500 words, with one visual asset. Quality over volume. Most pieces have a Twitter/LinkedIn short version and a long-form post on the blog. Shalom writes; Claude assists with research, drafts, and editing.

**Voice.** Plain, technically credible, calibration-forward, slightly playful when appropriate (the Constellation visualization piece, the Marcus Aurelius piece). Never mercenary, never hype. Voice should resonate with both Bert-tier design leaders and design-Twitter-savvy designers.

---

## 6 / Sales playbook

Three motions, scaled by deal size.

### 6.1 — Inbound Pilot Pack (motion: self-serve + light-touch)

**Source:** Creative Portfolios demo → contact form → Shalom email.
**Funnel:**
1. Visitor on `/portfolios` runs the demo, sees the Signal Array brand and gets curious.
2. Visitor clicks "Signal Array for your team →" → lands on `/signalarray` with the calibration report and the pricing page.
3. Visitor submits a contact form: "Tell us about your vertical and your timeline."
4. Shalom responds within 24 hours with a tailored Loom video (5 minutes) walking through what a Pilot Pack would look like for them.
5. 30-minute discovery call → custom Pilot Pack proposal → contract → onboarding.
**Target cycle:** 30–45 days from form submission to signed contract.
**CAC:** ~$5K (mostly Shalom time + a portion of the demo-channel attribution).

### 6.2 — Platform tier (motion: warm intro + custom workshop)

**Source:** Shalom's network or referrals from Pilot customers.
**Funnel:**
1. Warm intro from existing connection or LinkedIn message referencing a published calibration report.
2. 60-minute discovery call: their vertical, their team, their tooling, their research-velocity pain.
3. Custom workshop (half-day, paid or unpaid depending on customer profile): Signal Array demo + walkthrough of what a Platform engagement would look like.
4. Proposal: platform license + custom pack authoring scope + calibration commitment.
5. Procurement + legal review (the dominant time sink).
6. Signed contract.
**Target cycle:** 90–120 days.
**CAC:** ~$20K (Shalom time + occasional travel + workshop production).

### 6.3 — Enterprise (motion: founder-led, high-touch, year 3+)

**Source:** inbound from CHI paper authors, conference talks, or large-org procurement teams.
**Funnel:**
1. Multi-stakeholder discovery: usually a Head of Research + a Design VP + a Procurement lead + sometimes a Security lead.
2. Security review (SOC 2 evidence required by year 3).
3. Custom proposal with multi-pack scope, dedicated infrastructure terms, and SLA commitments.
4. Legal + procurement loop (typically 90–180 days).
5. Signed contract with a 12-month minimum.
**Target cycle:** 180–240 days.
**CAC:** ~$50K (Shalom time + travel + occasional legal cost on customer-specific terms).

### 6.4 — Sales tooling

Year 1: just Shalom, plus a shared Notion or Linear board for pipeline tracking. No CRM.
Year 2: lightweight CRM (HubSpot Starter or Pipedrive) once pipeline exceeds 10 active opportunities.
Year 3: real CRM, possibly a part-time sales hire or a fractional CRO depending on funding posture.

---

## 7 / Pricing & packaging (canonical)

Three tiers, plus the free public demo (covered in the Business Plan).

| Tier | Anchor Price | Includes |
|---|---|---|
| Creative Portfolios (free) | $0 | The public demo. Top-of-funnel acquisition. |
| Pilot Pack | $30K one-time + $15K Y1 hosting (renewals at $25K/yr) | One custom vertical pack, one calibration case study, hosted access for one team for one year. |
| Platform | $40K/yr license + $40–80K one-time per custom pack + metered runs above 200/mo | All-pack access, white-glove pack authoring, customer-success support, published calibration report per pack, SLAs. |
| Enterprise | Custom ($150K–$500K/yr) | Everything in Platform plus dedicated infrastructure, region pinning, SOC 2 evidence, custom heuristic libraries, dedicated implementation support. |

**Pricing principles.**
- One-time pack-authoring fees are a deliberate signal that pack content has real human labor behind it.
- Recurring license is the operational right-to-run; pack content is the value layer.
- Per-run metering protects gross margin without becoming a barrier for high-engagement customers (200 runs/month is generous; most customers stay below).
- Enterprise pricing is custom because regulatory, security, and integration requirements vary enormously.

**Discount discipline.** Avoid discounting below 20% off list. Synthetic-user category is going to commoditize on price for consumer-flavored competitors; Signal Array's differentiation is the calibration-trust moat, not the lowest price.

---

## 8 / Launch sequence (12 months)

Six moments that define the GTM motion's narrative arc.

**Moment 1 — Phase 0 stealth, content seeding.** No public Signal Array brand yet. Shalom writes 2 essays establishing the category critique (Marketing piece #1, #2 above) under his own byline.

**Moment 2 — Phase 1 demo to Bert.** Internal moment, not external. Builds the customer relationship that anchors everything else.

**Moment 3 — Phase 3 calibration report publishes.** Public launch of Signal Array.
- Pre-published the day before to Bert, Moloco Speedboat team, and ~20 design-leadership contacts for fact-checking.
- Public post at `opencosmos.ai/signalarray/calibration/moloco-001` with cross-link from the Signal Array landing page.
- Tweet thread, LinkedIn long-form post, and submission to design newsletters.
- Bert and Moloco design team co-share if they're willing.
- Target: 5,000+ unique visitors to the report in first 14 days; 3+ inbound commercial inquiries.

**Moment 4 — Phase 4 Creative Portfolios demo launches.** Distribution moment for the broader design community.
- Twitter announcement with a screencap of a real synthetic critique on a known portfolio.
- LinkedIn post targeting design recruiters and design-community leaders.
- Soft-share via Sidebar.io, Designer News, design Twitter.
- Target: 10,000+ unique visitors in first 30 days; 100+ portfolios run through the demo; 5+ inbound commercial inquiries from B2B-buyer-personas who tried the demo.

**Moment 5 — Phase 5 second commercial pack signed.** Internal celebration; public via the second calibration report (~6 months later).

**Moment 6 — CHI 2027 paper submission.** Pre-publication: blog post explaining the paper's framing, methodology, and findings. Post-acceptance (or rejection): the artifact becomes part of Signal Array's documentation and a recruiting / fundraising asset.

---

## 9 / KPIs and what we track

**Top-of-funnel:**
- Unique visitors to `opencosmos.ai/signalarray` (target: 500/mo by month 6; 2,500/mo by month 12)
- Unique visitors to `/portfolios` (target: 1,000/mo by month 6; 8,000/mo by month 12)
- Calibration report page views (target: 1,500 cumulative for moloco-001 by month 12)

**Funnel conversion:**
- Contact form submissions per month (target: 5/mo by month 6; 15/mo by month 12)
- Discovery calls held (target: 3/mo by month 6; 10/mo by month 12)
- Pilot Pack proposals issued / signed (target: signed contracts 2 in Y1, 4 in Y2, 5 in Y3)

**Brand & credibility:**
- Inbound mentions in design newsletters / blogs / podcasts (target: 5 in Y1, 15 in Y2)
- LinkedIn followers for Shalom + the Signal Array account (combined target: +1,000 in Y1)
- CHI submission completed (Y1); accepted (decision Y2)

**Product engagement:**
- Cohort runs per active customer per month (target: 30 avg)
- Calibration reports published per quarter (target: 1 in Q4 of Y1; ramps from there)

**Financial (from the financial model):**
- Recognized revenue per quarter
- Customer count by tier
- LTV/CAC by tier
- Cash position end of quarter

Reviewed monthly by Shalom. Reported on the public Signal Array blog at the Year 1 anniversary (the year-in-review content piece, with deliberate transparency as a brand signal).

---

## 10 / What good looks like in 12 months

By month 12, a healthy GTM motion shows:

- The Moloco calibration report is the second result on Google for "synthetic UX research" (behind only Wikipedia or analogous high-authority pages).
- The Creative Portfolios demo has been shared by 3+ recognized design voices and has a self-sustaining word-of-mouth flow.
- Signal Array has 3 paying commercial customers (1 lighthouse + 2 Pilot Pack).
- A second calibration report has published, showing the methodology generalizes beyond ads.
- The CHI 2027 paper is submitted; acceptance pending.
- Shalom is a recognized voice in the synthetic-UX-research conversation, with at least one keynote-grade conference invitation in the pipeline.

If those six are true at month 12, the commercial motion has earned the right to scale into Year 2.
