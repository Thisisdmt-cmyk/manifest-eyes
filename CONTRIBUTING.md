# Contributing to manifest-eyes

Thank you for the interest. This is a methodology-pattern repository, not a code framework. Most contributions will arrive as Issues or Pull Requests against the docs and schemas.

## What contributions are welcomed

- **Clarifications** to the methodology essays in `docs/`. If a passage reads ambiguously to a senior practitioner, that is a defect; an Issue or PR is welcomed.
- **Schema refinements**. The `schemas/*.json` files are JSON Schema Draft 2020-12. Edge cases the schemas should reject but currently allow (or vice versa) are valid Issues.
- **Worked examples** for `examples/`. Anonymised, please. Real-client examples must arrive with explicit permission.
- **Provider substitutions** in `schemas/eyes-config.example.json`. The named three (Mistral / Cohere / DeepSeek-via-HF) are illustrative; alternative diverse-jurisdiction triples are interesting and welcomed.
- **Reference-implementation links**. If you build a runtime that consumes these schemas (manifest registry, claim ledger, assessor harness), open an Issue with a link; the author will add it to a roadmap section.

## What contributions are not in scope

- Changes that fold the patterns back to a single-assessor or single-jurisdiction model. The whole point is the diversity of three.
- Changes that add specific commercial substrate (TCOM / TSOM / QEREN / Permanence / closed-source rubric internals). The patterns are public-eligible by design; the substrate that produced them is not.
- Provider lock-in. The schemas should remain provider-substitutable.
- Non-Apache-2.0-compatible licensing on derivative work in this repository.

## Pull request expectations

- One concept per PR. Schema PRs separate from doc PRs separate from example PRs.
- Plain-English commit messages. No "fix typos" without naming the files.
- No em / en dashes anywhere - regular hyphens only.
- For doc changes: the author may run a 2-of-3 consensus pass against the change before merging. The pass is informational only; reviewer judgement is final.

## Issue expectations

- Provide enough context that a fresh reader can act on the Issue without your back-channel knowledge.
- Cite the file + line where applicable.
- For methodology critique: state the existing claim, state your counter-claim, name the evidence.

## Code of conduct

The author's TCOM principle binds this repository: Quality and Safety, all ways, always. Disagreement is welcomed; rudeness is not. Issues that read as personal attacks are closed without comment.

## Maintainer

David Mantalios-Thompson (<Thisisdmt@gmail.com>). Independent practice; foundry of one. Response cadence is event-driven; expect commentary on substantive Issues but not on every drive-by note.
