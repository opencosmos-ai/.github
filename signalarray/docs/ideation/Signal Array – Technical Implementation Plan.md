# Signal Array — technical implementation plan
### What to build, in what order, on what stack, with what discipline

**Author:** Shalom Ormsby (with Claude)
**Date:** 17 May 2026 (light tweaks for reorientation; original 14 May 2026 draft)
**Status:** Working draft. Iterates with Phase 0 and Phase 1 build.
**Companion to:** *00-REORIENTATION*; *Signal Array — Platform Vision*

**Note on the reorientation.** Under *00-REORIENTATION*, Signal Array is deployed as a single-tenant consulting engagement for Moloco-001, not as a multi-tenant SaaS. The architecture below is preserved as designed because the kernel, judge, persona system, calibration framework, and constellation adapter are all required for the Moloco delivery. Multi-tenant SaaS infrastructure (Clerk auth, Stripe billing, customer workspace management, SOC 2 evidence collection) is **deferred indefinitely** — those Phase 5+ deliverables are preserved in the dormant *Business Plan* in `superseded/`.

---

## TL;DR

Signal Array is built as a TypeScript/Node monorepo, hosted under the OpenCosmos GitHub organization, consuming the existing `@opencosmos/*` packages from npm. The kernel runs on Next.js 16 (App Router) at `opencosmos.ai/signalarray` for marketing/docs/calibration reports and on `signalarray.opencosmos.ai` (or `opencosmos.ai/signalarray/app`) for the authenticated product app. Two agent runtimes (User Agent + Judge Agent) are orchestrated by a shared trace pipeline that writes to Postgres + object storage. The Constellation cohort visualization wraps `@opencosmos/constellation`. The browser layer is Anthropic Computer Use first, Browserbase + Playwright second. Everything is built to ship a working single-persona MVP in 2 weeks, a 12-persona cohort with the Judge Agent in 5 weeks, and a published calibration report in 8 weeks.

---

## 1 / Architecture overview

Four layers, top to bottom:

**Layer 4 — Product surfaces.** The `/signalarray` marketing site, the authenticated app, the public Creative Portfolios demo at `/signalarray/portfolios`, the calibration-report archive at `/signalarray/calibration`. All hosted on Vercel, all consuming `@opencosmos/ui`. Pack-specific theming switches the surface chrome (Studio for ads/enterprise, Terra for portfolios).

**Layer 3 — Application layer.** The Signal Array-proprietary code: User Agent runtime, Judge Agent runtime, persona authoring system, calibration framework, cohort runner, trace pipeline, Pack SDK, billing/auth integration. This is what customers pay for.

**Layer 2 — Vertical packs.** Content libraries per domain, loaded at runtime. Each pack is a versioned content bundle (personas, scenarios, heuristics, lexicon, theming hints, optional widgets). Packs depend on Layer 3; Layer 3 never imports from a pack.

**Layer 1 — OpenCosmos infrastructure.** `@opencosmos/ui`, `@opencosmos/constellation`, `@opencosmos/tokens`, `@opencosmos/mcp`. MIT, consumed from npm, contributed-to upstream when needed.

The contract between layers is enforced by import boundaries: a TypeScript ESLint rule prevents Layer 3 from importing Layer 2 specifics, and prevents Layer 2 from forking Layer 1 packages locally.

---

## 2 / Technology stack

| Layer | Technology | Why |
|---|---|---|
| Framework | Next.js 16 (App Router) | Matches OpenCosmos ecosystem; SSR + RSC available; Vercel deploy native |
| Language | TypeScript 5 (strict) | Consistency with OpenCosmos; type safety at the agent-protocol boundary |
| Component library | `@opencosmos/ui` | The whole point — leveraging existing infrastructure |
| Visualization | `@opencosmos/constellation` (wraps `@cosmos.gl/graph`) | The cohort viz hero feature |
| State (client) | Zustand 5 + localStorage | Matches OpenCosmos pattern |
| Forms | react-hook-form | Matches OpenCosmos pattern |
| Database | Postgres (Neon serverless) | Operationally simple; branch-per-PR for dev velocity |
| ORM | Drizzle | TS-native, small surface, plays nicely with serverless |
| Object storage | Cloudflare R2 or Vercel Blob | Screenshots, video traces, large artifacts |
| Background jobs | Inngest or Trigger.dev | Cohort runs are long-running multi-step workflows; durable execution |
| LLM API (agents) | Anthropic Claude (claude-opus-4-6, claude-sonnet-4-6) | Best-in-class agent reasoning; Computer Use availability |
| Browser layer (primary) | Anthropic Computer Use | Native to the Claude SDK; lowest integration cost |
| Browser layer (fallback) | Browserbase + Playwright | Headless scaling when Computer Use rate limits bite |
| Auth | *Deferred under reorientation* (was Clerk) | No multi-tenant customer accounts needed; Moloco delivery is single-tenant |
| Billing | *Deferred under reorientation* (was Stripe metered) | No recurring billing; Moloco contract is invoiced via existing accounting |
| Analytics (product) | PostHog (self-hosted or cloud) | Open, respects user privacy posture |
| Analytics (marketing) | Plausible | Aligned with OpenCosmos privacy ethos |
| Email | Resend | Operationally simple, great DX |
| Monorepo | Turborepo + pnpm workspaces | Matches OpenCosmos |
| MCP | `@opencosmos/mcp` extended for Signal Array resources | Lets AI assistants enumerate cohorts/packs |
| Testing | Vitest + Testing Library + Playwright (e2e) | Standard for the stack |
| Deployment | Vercel (apps), Neon (db), R2 (objects), Inngest (jobs) | All serverless, all pay-as-you-go, all friendly to a solo operator |
| Error tracking | Sentry | Standard |

No exotic technology. The discipline is to keep the stack boringly familiar to anyone shipping modern TypeScript SaaS in 2026, so Signal Array's complexity is in the *product*, not the *plumbing*.

---

## 3 / Repository structure

A new monorepo under the OpenCosmos GitHub org (`opencosmos-ai`): `opencosmos-ai/signalarray` (private). It consumes `@opencosmos/*` packages from npm and does not vendor them.

```
signalarray/
├── apps/
│   ├── web/                    # opencosmos.ai/signalarray marketing + docs + calibration reports
│   ├── app/                    # authenticated product app (signalarray.opencosmos.ai)
│   └── portfolios/             # /signalarray/portfolios public demo
├── packages/
│   ├── kernel/                 # @signalarray/kernel — User Agent + Judge Agent + trace pipeline
│   ├── pack-sdk/               # @signalarray/pack-sdk — types, validators, helpers for pack authors
│   ├── personas/               # @signalarray/personas — persona schema + grounding-source bookkeeping
│   ├── scenarios/              # @signalarray/scenarios — scenario schema + execution helpers
│   ├── judge/                  # @signalarray/judge — heuristic loader + scoring + critique dedup
│   ├── trace/                  # @signalarray/trace — trace capture, storage, cluster helpers
│   ├── constellation-adapter/  # Signal Array-specific wrapper around @opencosmos/constellation
│   ├── calibration/            # @signalarray/calibration — calibration-loop runner + report generator
│   ├── browser/                # browser-layer adapters (Computer Use, Browserbase)
│   └── mcp/                    # Signal Array MCP server extending @opencosmos/mcp
├── packs/                      # vertical pack content (not code)
│   ├── moloco-ads/             # Moloco Ads pack (private, proprietary)
│   ├── portfolios/             # Creative Portfolios pack (public, free)
│   └── _template/              # starter template for new packs
├── db/                         # Drizzle schema, migrations
├── infra/                      # Vercel config, Inngest functions, secrets templates
├── docs/                       # internal architecture docs, ADRs
├── scripts/                    # CLI utilities, persona ingestion, calibration runners
├── AGENTS.md                   # how Claude/Cursor/AI assistants interact with this repo
├── DESIGN-PHILOSOPHY.md        # references OpenCosmos's; states Signal Array-specific commercial discipline
├── pnpm-workspace.yaml
├── turbo.json
└── package.json
```

Pack repos can be private per pack (Moloco-ads is private; portfolios is public, MIT) without affecting the kernel's open-core posture.

---

## 4 / Core component breakdown

### 4.1 — User Agent runtime (`packages/kernel`)

**Purpose:** drive a target UI as a specific persona on a specific scenario, capture a structured trace.

**Implementation:**
- Takes inputs: `Persona`, `Scenario`, `Target` (URL + optional Figma export), `RunConfig`.
- Initializes an Anthropic Claude session with persona-conditioning prompt (built from the persona dossier — identity, skill grades, mental models, vocabulary, frustrations, second-order textual grounding summary).
- Hands control to the browser-layer adapter (Computer Use or Browserbase).
- Captures at each step: action taken, reasoning (chain-of-thought), screenshot, timestamp, target DOM state if available.
- Emits a structured `Trace` object: action stream + reasoning stream + screenshot references + completion status + total elapsed.

**Key design decisions:**
- The persona-conditioning prompt is *templated*, not free-form. The Pack SDK provides a strict template that ensures consistency across personas.
- Chain-of-thought is captured but never shown to customers as raw output — the Judge Agent processes it before the customer sees anything.
- Hesitation detection: any time-on-screen above a threshold (default 5s) is logged as a hesitation event in the trace.

### 4.2 — Judge Agent runtime (`packages/judge`)

**Purpose:** evaluate a User Agent trace against vertical-specific heuristics, produce critique themes.

**Implementation:**
- Takes inputs: `Trace`, `HeuristicSet` (loaded from the pack), `Persona` (for context).
- Loads each heuristic's prompt template, scoring rubric, and confidence-rating guide from the pack.
- Runs a multimodal Claude call per heuristic (trace JSON + screenshots).
- Produces a `Critique` per heuristic: pass/fail/partial, severity, confidence, evidence (linked back to specific trace events), narrative.
- After per-heuristic critique, runs a deduplication pass across all personas in a cohort run: groups critiques that point to the same underlying UI failure mode.
- Outputs both per-session critiques (for spot-checking) and cohort-aggregated themes (for the headline view).

**Key design decisions:**
- The Judge Agent is *stateless per heuristic* — no cross-heuristic prompt sharing in the same call. This makes critique quality more reliable and makes adding new heuristics safer.
- Confidence ratings are mandatory on every critique. The console surfaces them.
- Dedup runs over the *evidence* (trace event references), not over the *narrative*. Surface signal beats surface style.

### 4.3 — Persona authoring system (`packages/personas`)

**Purpose:** ingest research transcripts, extract skill axes, curate dossiers, link grounding sources.

**Implementation:**
- CLI + web UI for pack authors.
- Ingests interview transcripts (PDF, .docx, .txt, .md).
- Uses Claude to extract candidate skill axes and produce a draft persona dossier.
- Human-in-the-loop review surface for the pack author to refine, edit, and link grounding sources.
- Stores final dossiers as versioned YAML in the pack directory.
- Maintains an explicit `grounded_in` array linking each persona to interview-source IDs and (optionally) public-domain text IDs from the OpenCosmos corpus.

**Key design decision:** the persona dossier is always *human-authored-after-AI-draft*. No persona is shipped that hasn't been signed off by a human. This is the discipline that distinguishes Signal Array from competitors who let LLMs author personas end-to-end.

### 4.4 — Constellation cohort visualization (`packages/constellation-adapter`)

**Purpose:** render the cohort as an interactive WebGL knowledge graph.

**Implementation:**
- Thin adapter over `@opencosmos/constellation`.
- Defines Signal Array-specific node types (Persona, Heuristic, GroundingSource, CritiqueTheme) and edge types (skill-grade-adjacency, mental-model-shared, grounded-in, critique-fired-on, hesitation-occurred-at).
- Computes positions via force-directed layout (the upstream cosmos.gl renderer); persona clusters emerge from skill-grade similarity.
- Supports two modes: *cohort overview* (static, persona-only) and *run overlay* (with critique-cluster regions and hesitation timeline animation).
- Optimized for screenshot/export — every constellation view can be captured as PNG or SVG for inclusion in reports and decks.

**Key design decision:** the visualization is a *first-class product surface*, not an afterthought. It gets its own performance budget, its own accessibility audit, and its own QA pass before each release.

### 4.5 — Console UI (`apps/app`)

**Purpose:** the customer-facing product app for design teams.

**Implementation:**
- Next.js 16 App Router.
- All UI built on `@opencosmos/ui` components.
- Studio theme by default.
- Pages: Dashboard (constellation cohort overview), Scenarios, Runs, Calibration, Packs (admin), Settings.
- Auth + org/team management via Clerk.
- Billing via Stripe Customer Portal embed.

**Key design decision:** ship the Console with the same accessibility and motion-preference discipline OpenCosmos UI ships natively. Don't degrade.

### 4.6 — Calibration framework (`packages/calibration`)

**Purpose:** compare Signal Array findings against real-user findings on the same scenarios, generate published reports.

**Implementation:**
- Pack authors supply real-user research findings in a structured format (themes, severity, evidence).
- Runs the matching Signal Array cohort on the same scenarios.
- Computes agreement/divergence metrics: theme-overlap, severity-correlation, false-positive rate (Signal Array found, real didn't), false-negative rate (real found, Signal Array didn't), unique-Signal Array signal (Signal Array-only findings that the team validated as real after the fact).
- Generates a public Markdown + HTML calibration report at `opencosmos.ai/signalarray/calibration/{pack-id}-{case-id}`.

**Key design decision:** the calibration report format is standardized across all packs. Customers can compare Signal Array's track record on Ads vs. Devtools vs. Legal directly.

### 4.7 — Pack SDK (`packages/pack-sdk`)

**Purpose:** the contract authors use to build new packs.

**Implementation:**
- TypeScript types for `Persona`, `Scenario`, `Heuristic`, `Lexicon`, `Theme`, `Widget`.
- Runtime validators (Zod schemas) that the kernel uses to load packs safely.
- CLI: `signalarray pack init`, `signalarray pack validate`, `signalarray pack publish`.
- Pack template (`packs/_template/`) showing minimum-viable structure.

---

## 5 / Data model & schemas

### 5.1 — Persona

```typescript
type Persona = {
  id: string;
  pack_id: string;
  name: string;
  archetype: string;            // "Senior Growth DS"
  identity: { role: string; vertical: string; tenure_years: number };
  skill_grades: Record<string, 1|2|3|4|5>;
  mental_models: string[];
  vocab: string[];
  tools_loved: string[];
  tools_avoided: string[];
  frustrations: string[];
  grounded_in: {
    interviews: string[];       // interview transcript IDs (private to pack)
    texts: string[];            // OpenCosmos corpus IDs (public)
  };
  authored_by: string;
  authored_at: string;
  reviewed_by?: string;
  reviewed_at?: string;
};
```

### 5.2 — Scenario

```typescript
type Scenario = {
  id: string;
  pack_id: string;
  name: string;
  task: string;                 // natural language
  target: { url: string; kind: "live" | "staging" | "figma-export" | "screenshot-stream" };
  success_definition: string;
  checkpoints?: Array<{ name: string; criterion: string }>;
  estimated_duration_minutes: number;
};
```

### 5.3 — Trace

```typescript
type Trace = {
  id: string;
  run_id: string;
  persona_id: string;
  scenario_id: string;
  started_at: string;
  ended_at: string;
  completion: "completed" | "abandoned" | "blocked";
  actions: TraceAction[];       // append-only stream
  reasoning_stream: string[];   // synced to actions by timestamp
  screenshots: Array<{ ts: string; url: string }>;
  hesitations: Array<{ ts: string; duration_ms: number; context: string }>;
};
```

### 5.4 — Critique

```typescript
type Critique = {
  id: string;
  trace_id: string;
  heuristic_id: string;
  verdict: "pass" | "fail" | "partial";
  severity: 1|2|3|4|5;
  confidence: 1|2|3|4|5;
  evidence_refs: string[];      // trace action IDs
  narrative: string;
  cluster_id?: string;          // populated by dedup pass
};
```

### 5.5 — CalibrationReport

```typescript
type CalibrationReport = {
  id: string;
  pack_id: string;
  scenario_id: string;
  real_user_findings: Finding[];
  synth_findings: Finding[];
  agreement: { theme_overlap_pct: number; severity_correlation: number; };
  divergence: { false_positive_themes: string[]; false_negative_themes: string[]; unique_synth_signal: string[] };
  published_at: string;
  public_url: string;
};
```

Postgres schema mirrors these types via Drizzle. Object storage holds screenshots and full trace JSON blobs (referenced by URL from the DB row).

---

## 6 / Integration points

**Anthropic Claude API.** Primary LLM for both User Agent (claude-opus-4-6 for deeper reasoning) and Judge Agent (claude-sonnet-4-6 for cheaper multimodal critique). Authenticated via API key in env. Rate-limit handling and exponential backoff in `packages/kernel/lib/llm.ts`.

**Anthropic Computer Use.** Primary browser-layer. Spawns sandboxed VMs per run. Used for fidelity-critical scenarios.

**Browserbase + Playwright.** Fallback browser-layer for high-throughput cohort runs (e.g., 100 personas × 5 scenarios = 500 sessions in an evening). Adapter pattern means swapping is a one-line change per run.

**OpenCosmos packages.** `@opencosmos/ui` ^1.1.1, `@opencosmos/tokens` ^0.0.3, `@opencosmos/mcp` ^0.8.2, `@opencosmos/constellation` ^0.1.0. Updated via pnpm; any breaking changes get absorbed in Signal Array rather than forked.

**MCP server (`packages/mcp`).** Extends `@opencosmos/mcp` to expose Signal Array resources: `list_packs`, `list_personas`, `run_scenario`, `get_calibration_report`. Makes Signal Array accessible to Claude Desktop, Cursor, and any MCP-compliant AI assistant.

**Stripe.** Billing. Metered usage tier (per-run pricing) for high-volume customers; flat license tier for standard customers.

**Clerk.** Auth, org management, role-based access. B2B-friendly out of the box.

**Inngest (or Trigger.dev).** Long-running cohort runs are durable workflows. A typical run is 30 personas × 3 scenarios = 90 sessions, each lasting 2–10 minutes. Durable execution prevents serverless timeout limits from killing runs.

---

## 7 / Security & compliance

**Customer data isolation.** Each org/team gets a scoped namespace in DB and object storage. No cross-tenant queries possible at the ORM layer.

**Persona grounding sources.** Customer-uploaded interview transcripts are *pack-private*. They never appear in the product UI to customers outside the pack's owning org. Grounding-source-link metadata is shown to the customer in plain text; the source content itself is access-controlled.

**LLM prompt isolation.** No cross-customer prompt sharing. Each User Agent and Judge Agent session is a fresh API call with no shared state across customers.

**SOC 2 posture.** Deferred indefinitely under *00-REORIENTATION*. The original plan made SOC 2 a Phase 5 priority for multi-customer onboarding; since multi-customer onboarding is no longer pursued, SOC 2 evidence collection is not required. Continue to document the security practices that already exist (encryption at rest, scoped namespaces, no PII in LLM prompts, audit logs on admin actions); if a reactivation trigger fires and a new engagement requires SOC 2, the Drata/Vanta path remains available.

**Synthetic-account discipline.** Real customer accounts are *never* used as the test target. Every scenario uses a synthetic test account on the target system. Hard-coded as a validation in scenario authoring.

**Open-source supply chain.** Renovate or Dependabot on the Signal Array repo + the OpenCosmos repos. CVE alerts watched. The dependency on `@opencosmos/*` is reviewed at every major bump.

---

## 8 / Phased build milestones (technical detail)

**Phase 0 — Persona grounding & scaffolding (Week 1)**
- Initialize the `signalarray` monorepo; set up Turborepo + pnpm workspaces.
- Install `@opencosmos/*` packages; verify build pipeline.
- Stand up Postgres (Neon) + Drizzle migrations; deploy `apps/web` to Vercel at `opencosmos.ai/signalarray` (placeholder landing).
- Ingest existing Moloco research transcripts; run Claude-assisted skill-axis extraction.
- Hand-author 12 Moloco persona dossiers (YAML) with interview grounding + curated OpenCosmos corpus grounding.
- Commit to `packs/moloco-ads/personas/`.

**Phase 1 — Single-session MVP (Weeks 2–3)**
- Implement `packages/kernel` minimum: persona-conditioning prompt builder, Claude session orchestrator, action capture, trace emitter.
- Wire Anthropic Computer Use as the first browser adapter.
- Build the bare console: `apps/app` with a Run button, a persona picker, a target URL field, and a trace viewer.
- First Constellation render: even at 1 persona, the visualization is a demo moment.
- Run one Priya-persona session against a Figma-Make export of NextGen.
- Demo to Bert at end of Week 3.

**Phase 2 — Judge Agent + cohort scaling + Constellation overlays (Weeks 4–5)**
- Implement `packages/judge`: heuristic loader, scoring rubric runner, critique dedup.
- Author 6–8 Moloco-Ads heuristics in `packs/moloco-ads/heuristics/`.
- Wire the Inngest workflow for cohort runs (12 personas × 1 scenario = 12 sessions in parallel).
- Build the cohort view with Constellation critique overlays.
- A/B design variant comparison: same scenario, two targets, side-by-side cohort results.

**Phase 3 — Calibration framework + first published report (Weeks 6–8)**
- Implement `packages/calibration`: comparison metrics, report generator.
- Pick one design decision Moloco has tested with 3 real GMs. Run the same scenario through Signal Array.
- Generate the report at `opencosmos.ai/signalarray/calibration/moloco-001`.
- Internal walkthrough with the Speedboat team. Publish.

**Phase 4 — Creative Portfolios public demo (Weeks 9–10)**
- Build `apps/portfolios` as a separate Next.js route.
- Author 8 portfolio personas + 3 scenarios + 5 heuristics in `packs/portfolios/`.
- Soft-launch at `opencosmos.ai/signalarray/portfolios`.

**Phase 5 — Post-contract window: CHI paper + Moloco contract decision (Months 4–6)**
- CHI 2027 paper drafted and submitted by September 11, 2026.
- Moloco contract status resolved (extended, restructured, or concluded).
- Pack SDK refinements applied if a latent-option second pack engagement materializes (see *00-REORIENTATION* for reactivation triggers); otherwise the Pack SDK stays at its Moloco-shipped state.
- SOC 2 audit prep is **not pursued** unless a reactivation trigger fires.

**Phase 6 — Removed under the reorientation.** The original funding-posture decision is closed; default is bootstrap, solo, methodology-as-consulting. Reopen only if a reactivation trigger fires per *00-REORIENTATION*.

---

## 9 / Test strategy

**Unit tests** on every pure function in `packages/*`. Vitest. Coverage target 70%+ on the kernel and judge packages; lower acceptable on UI.

**Integration tests** on full cohort-run workflows using a mock browser adapter that replays deterministic action streams. Covers: "given persona P and scenario S, the judge produces critique C with confidence ≥ threshold."

**E2E tests** with Playwright against `apps/app` for the critical paths: log in, pick a pack, run a scenario, view results, view constellation. Run on every PR.

**Snapshot tests** on the Constellation visualization at known cohort configurations. Catch regressions in rendering positioning, edge styling, and critique-overlay coloring.

**Calibration-loop self-tests.** Each calibration report is itself a test artifact — divergence above threshold flags the affected heuristics or personas for review.

**Persona-grounding lint.** A pre-commit hook (in the pack repo) validates that every persona has `grounded_in.interviews.length >= 1` and that all referenced transcript IDs exist. Prevents shipping an ungrounded persona by accident.

---

## 10 / Open technical questions

These get answered during Phase 0–1, not before:

- **Computer Use vs. Browserbase as default browser layer.** Computer Use is lower-integration-cost but has tighter rate limits. Decide based on cohort-run throughput in Phase 2.
- **Trace storage size and retention.** A 5-minute trace with screenshots can be 20–50MB. At 100 personas × 5 scenarios × 4 design variants = 2,000 traces, storage costs add up. Retention policy: keep traces 90 days, archive to cold storage after.
- **Judge Agent prompt-cache strategy.** Claude prompt caching can dramatically cut costs on repeated heuristic evaluation. Investigate in Phase 2.
- **Constellation rendering performance at 200+ personas.** Acceptable on a developer laptop; needs profiling for low-spec customer machines.
- **The "interview-grounded persona" provenance UX.** How exactly do we display grounding sources to the customer without leaking transcript content from other customers' packs? Likely a "source: Moloco GM Interview #14 (private)" indicator with no content reveal.
- **Pack distribution model.** Eventually packs may be installed from a registry (`signalarray pack install @signalarray/legal-tech-v1`). For Phase 0–4 the packs live in the monorepo; the registry is a Phase 5+ decision.

---

## Appendix — solo-operator velocity discipline

The plan above assumes a solo operator with Claude in the loop most days. Three rules that keep velocity high:

1. **Ship the Phase 1 single-persona MVP before optimizing anything.** No premature abstraction in the kernel. The first persona run is allowed to be ugly.
2. **Resist scope creep on the Pack SDK.** It evolves *after* the second pack exists, not before. Designing the SDK in the abstract from one pack is a known failure mode.
3. **Use the OpenCosmos repos as upstream improvements happen.** If `@opencosmos/ui` ships a better Card component, adopt it. If Constellation ships a layout improvement, adopt it. Signal Array is not the place to fork-and-customize OpenCosmos code; it's the place to consume it.

The whole technical thesis is that Signal Array's defensibility is in the *methodology, calibration discipline, and pack content* — not in the plumbing. Keep the plumbing standard, ship the methodology fast.
