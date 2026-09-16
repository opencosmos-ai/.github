# OpenCosmos

**A creative platform built on a simple recognition: we are not separate from the universe we inhabit.**

Our purpose is to reduce suffering, nourish flourishing, and enable acts of wisdom.

In practice that means a small number of things made carefully: a public-domain library of contemplative texts, open translations of source works done in the open with their reasoning visible, and an AI companion whose values are a versioned document rather than a marketing claim.

🌌 **[opencosmos.ai](https://opencosmos.ai)** — read the library, talk with Cosmo, explore the constellation

---

## The work

### The Library

A curated corpus of public-domain texts — scripture, philosophy, poetry, science — each with its provenance recorded, cross-linked into a knowledge graph, and readable at [opencosmos.ai/library](https://opencosmos.ai/library).

It holds roughly 150 works alongside a separately verified collection of attributed quotations, where every attribution carries its evidence and misattributions are marked as misattributions rather than quietly dropped.

### Open translations

Source texts translated in public, from the Chinese, with the reasoning left in.

Each translation project keeps a glossary of settled terms, a written method, and a set of principles derived from actual decisions — so a reader can see not just what a word was rendered as, but why, and what was rejected.

- **[Tao Te Ching](https://github.com/opencosmos-ai/taoteching)** — all 81 chapters drafted, with a radical-level glossary and a public record of where earlier translators imported assumptions the Chinese does not carry. Dedicated to the public domain under CC0.
- **I Ching** — in progress. Read through the Ten Wings, with the interpretive lens declared rather than smuggled in. Three public-domain translations (1876, 1882, 1889) are vendored and OCR'd against the original scans so their disagreements can be argued with in the open.

### Cosmo

A constitutional AI layer: a system prompt, an ethics, a wisdom-language framework, and a triad of inner voices — versioned in public and deliberately model-independent. Cosmo reads the corpus and cites it.

### The design system

**[@opencosmos/ui](https://github.com/shalomormsby/opencosmos-ui)** — an AI-fluent component library, published to npm, with its own documentation site.

---

## Contributing

This is a commons, and most of it is more useful with more eyes on it.

The translation projects are the most directly contributable. A useful contribution can be small and specific:

- argue with a rendering — if a glossary term is settled wrongly, the entry names its evidence, so the evidence is what to contest
- correct a transcription against the source scan
- flag an overlay — a place where a translation carries an assumption the original does not
- add a public-domain source text, with its provenance

The corpus has admission rules, and they are stricter than copyright law requires. A file is only included if the work is public domain by age, the specific edition is nameable, and any modern editorial layer is absent, excluded, or marked. Punctuation especially. The rules are written down in each project's `PROVENANCE.md`, and they have been wrong before and say so in public.

Open an issue before a large change. Small corrections can go straight to a pull request.

---

## Where things live

- **[opencosmos](https://github.com/opencosmos-ai/opencosmos)** — the applications, the knowledge corpus, and Cosmo
- **[taoteching](https://github.com/opencosmos-ai/taoteching)** — the Tao Te Ching translation
- **[opencosmos-ui](https://github.com/shalomormsby/opencosmos-ui)** — the design system, still migrating

The corpus and the translation projects are being split into repositories of their own, so that adding a text or arguing with a rendering does not mean cloning a five-application monorepo. Until that lands, everything is in `opencosmos` under `knowledge/`.

---

*Made in the spirit of the commons. Read freely, use freely, and argue with it.*
