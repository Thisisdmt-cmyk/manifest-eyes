# manifest-eyes

A public-eligible methodology pattern for AI-native delivery: three independent assessor models evaluate every output stage, four-floor quality numbers gate ship/no-ship, and a manifest pipeline locks stages so AI cannot shortcut the work.

**Status**: v0.1, methodology-only release (no executable code in this drop; schemas + docs + worked example).
**License**: Apache-2.0
**Author**: David Mantalios-Thompson (independent practice; foundry of one)

## What this is

Three patterns, abstracted to PATTERN level, that together make AI-native delivery defensible to a board:

1. **Multi-Eye Consensus** - three independent assessor models (one EU, one Canadian, one open-weights on Western infrastructure) evaluate every output stage. 2-of-3 consensus required to advance. Two dissents block until a human reviewer rules. Beats single-model assessment because it survives any one provider's calibration drift, training-data overlap, or jurisdictional substrate concentration.

2. **Quality Floors** - four named constants on every output: TRUTH 100 / USER 95 / FORM 95 / RESONANCE 80. Each is a floor, not a target. TRUTH at 100 means zero factual errors; USER at 95 means the output measurably serves the named user; FORM at 95 means it is structurally sound; RESONANCE at 80 means it is voiced consistent with the brand or the operator. The floors are public-eligible; the rubric internals are not.

3. **Manifest Pipeline** - every output stage (research / generate / evaluate / refine / build / verify) gets a manifest packet declaring its model tier, inputs, outputs, and dependencies. Stages must complete in order. Manifest-claim prevents double-claim. Manifest-complete validates that the output type matches the packet declaration. Orphan artefacts cannot be certified. The pipeline is a lock, not a ledger.

## What this is NOT

- Not a code framework. There is no library to import. The patterns are language-agnostic; reference implementations may follow under separate repositories.
- Not an Eye registry. The three assessors named in this drop (Mistral, Cohere, DeepSeek-via-HuggingFace) are illustrative; the pattern is provider-substitutable. Any three independent diverse-jurisdiction models qualify.
- Not the substrate that produced it. The closed substrate David built this pattern from is deliberately out of scope. What ships here is the pattern, anonymised.

## How to adopt

A team adopting these patterns ships a small assessment harness that:

1. Routes every output stage through three named external assessors before merging.
2. Stamps every output with the four-floor numbers as named constants in the artefact metadata.
3. Records every claim against a manifest packet in a write-once ledger; rejects orphan artefacts at certification time.

Reference shapes:

- `schemas/manifest.schema.json` - manifest packet structure
- `schemas/claim.schema.json` - claim ledger entry structure
- `schemas/eyes-config.example.json` - assessor configuration example
- `examples/example-run.md` - end-to-end worked example (anonymised)
- `docs/multi-eye-consensus.md` - methodology essay
- `docs/quality-floors.md` - methodology essay
- `docs/manifest-pipeline.md` - methodology essay

## Why three assessors

Single-model assessment fails three ways and the failures are well-documented:

- **Calibration drift**: a model rated as a strong evaluator at point-in-time can quietly degrade across a quarter, and the user does not see the drift.
- **Training-data overlap**: a model assessing an output it generated, or an output produced by a sibling model, has shared substrate; the assessor's "yes" is not independent.
- **Jurisdictional substrate concentration**: if one provider's substrate goes offline (or its terms change, or its export controls bite), every assessment is affected.

Three diverse-jurisdiction assessors fail in different ways at different points. 2-of-3 consensus survives any one assessor's failure. Two dissents force escalation to a human, which is the correct outcome when assessor disagreement is real signal.

## Why public-eligible matters

The underlying substrate that produced these patterns has commercial value the author does not give away. The patterns themselves do not. Publishing the patterns at PATTERN level means:

- Buyers can adopt without licensing.
- Auditors can evaluate without an NDA.
- Regulators can read without back-and-forth.
- Competitors can compete on substrate, not on whether-the-pattern-exists.

The author retains the substrate. The author publishes the floor.

## Citations + provenance

Patterns crystallised across the author's substrate work for independent practice. Some shapes echo prior work in software supply-chain attestation (in-toto), reproducible builds (Debian / Reproducible Builds project), and multi-rater calibration (inter-annotator agreement statistics). These are PATTERN-level echoes, not borrowings.

## Where to find the author

David Mantalios-Thompson is an independent senior planner and AI-native delivery lead based in Jarrow, UK. Engagement shapes (Discovery Sprint / Programme Reset / Composite delivery / Fractional CTO / AI Implementation Lead) at his website (link forthcoming once domain pair lands).

LinkedIn: linkedin.com/in/david-mantalios-thompson-8884091b4
Email: Thisisdmt@gmail.com

## Roadmap

This is a v0.1 methodology drop. Likely later additions, in dependency order:

- Reference implementation in TypeScript (manifest registry + claim ledger).
- Reference implementation of the assessor harness (provider adapters + 2-of-3 consensus check).
- Worked-example case studies (anonymised) drawn from buyer engagements.
- A small CLI: `manifest-eyes init / claim / complete / verify`.

Operator feedback welcomed via Issues.

## Quality and safety, all ways, always

The author's working principle. It is not a slogan; it is the floor. Quality includes the four-floor numbers, the consensus requirement, and the manifest discipline. Safety includes anti-enumeration in any client-facing surface, IP-protection on closed substrate, and the principle that human judgement remains in the loop on every behavioural decision.
