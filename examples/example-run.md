# Worked example - end-to-end manifest run

This walkthrough shows a complete manifest-eyes run for a single piece of work: drafting a methodology essay, evaluating it through three assessors, refining on dissent, building the rendered artefact, and verifying the result. All names below are illustrative; the example is anonymised.

## Brief

> Operator: "Draft a methodology essay (~1,800 words) on the Multi-Eye Consensus pattern. Public-eligible PATTERN level only; no closed-substrate names. Klim DNA aesthetic register. Hedged behavioural claims. Cite the three named assessors as illustrative; the pattern is provider-substitutable."

## Manifest

```json
{
  "manifest_id": "essay-mec-2026-05-09",
  "product_type": "methodology-essay",
  "brief": "Methodology essay (~1,800 words) on the Multi-Eye Consensus pattern...",
  "depth": "full",
  "operator": "human:dmt",
  "created_at": "2026-05-09T10:00:00Z",
  "stages": [
    { "packet_id": "research",  "stage": "research",  "model_tier": "sonnet",          "depends_on": [],          "expected_output_type": "markdown" },
    { "packet_id": "generate",  "stage": "generate",  "model_tier": "sonnet",          "depends_on": ["research"], "expected_output_type": "markdown" },
    { "packet_id": "evaluate",  "stage": "evaluate",  "model_tier": "external-diverse", "depends_on": ["generate"], "expected_output_type": "json", "consensus_floor": "2-of-3" },
    { "packet_id": "refine",    "stage": "refine",    "model_tier": "sonnet",          "depends_on": ["evaluate"], "expected_output_type": "markdown" },
    { "packet_id": "build",     "stage": "build",     "model_tier": "sonnet",          "depends_on": ["refine"],   "expected_output_type": "markdown" },
    { "packet_id": "verify",    "stage": "verify",    "model_tier": "mechanical",      "depends_on": ["build"],    "expected_output_type": "json" }
  ]
}
```

## Run sequence

### Stage 1 - research (sonnet)

Claim filed: `claim_id=a8b...`, `kind=claim`, `claimant=sonnet:researcher`. The researcher gathers prior art on multi-rater calibration, software supply-chain attestation patterns, jurisdictional substrate diversity in AI policy literature. Notes are produced in markdown at `output/essay-mec-2026-05-09/research-notes.md`. Claim completed: `kind=complete`, `result_ref=output/.../research-notes.md`.

### Stage 2 - generate (sonnet)

Sonnet drafts the ~1,800-word essay using the researcher's notes. Output at `output/.../essay-draft-v1.md`. Claim filed + completed.

### Stage 3 - evaluate (external-diverse, 2-of-3 floor)

Three assessors run in parallel against `essay-draft-v1.md`:

```
assessor-1 (Mistral large)             -> verdict: pass        (TRUTH 100, USER 96, FORM 95, RESONANCE 82)
assessor-2 (Cohere command-a-03-2025) -> verdict: review     (TRUTH 100, USER 92, FORM 95, RESONANCE 78)
assessor-3 (DeepSeek-R1 via HF)        -> verdict: pass        (TRUTH 100, USER 95, FORM 96, RESONANCE 81)
```

Outcome: 2-of-3-pass with one review-flag from Cohere. Cohere rationale: USER score below 95 floor on the "how to adopt" section; the reader cannot leave with a concrete adoption sequence. Claim filed: `kind=complete`, `consensus.outcome=2-of-3-pass`. Per the floor rule, 2-of-3 lets the run advance, but the dissent rationale is propagated to the refine packet.

### Stage 4 - refine (sonnet)

Sonnet receives both the draft and the Cohere dissent rationale. Refines the "how to adopt" section to add an explicit five-step adoption sequence with named owner, named output, named gate. Output at `output/.../essay-draft-v2.md`. Claim filed + completed.

### Stage 5 - build (sonnet)

Sonnet renders the final markdown for publication: header block, body, "Where this fits" footer, APEX self-grade. Output at `output/.../multi-eye-consensus-methodology.md`. Claim filed + completed.

### Stage 6 - verify (mechanical)

Mechanical checks:
- ASCII-clean (no em / en dashes): pass
- IP-protection grep (TCOM / TSOM / QEREN / Permanence / Crystal Store / Dream Cycle / APEX rubric internals): pass
- Floor stamp present in artefact metadata: pass
- Word count within 1,500 to 2,000: pass (1,820 words)
- All cited references verifiable: pass

Claim filed: `kind=verify`, `directive_001_floor: { truth: 100, user: 96, form: 95, resonance: 82 }`. The artefact is now eligible for publication.

## What this example shows

1. **Single-assessor would have shipped the v1 draft** (Mistral and DeepSeek both passed). The Cohere dissent is the load-bearing signal that drives the refine; without three assessors, the dissent never surfaces.
2. **The dissent is informational, not blocking** under the 2-of-3 floor. The run advances; the dissent rationale propagates forward.
3. **The mechanical verify is non-substitutable** for the three-assessor pass. They check different things: assessors check meaning; mechanical checks structure.
4. **Every claim is a write-once ledger entry**. The audit trail from brief to publishable artefact is reconstructable from the ledger alone.

## The same example, single-assessor

If the same brief had run through a single Mistral evaluation:

- Mistral verdict: pass
- Refine stage: skipped (no dissent)
- Published artefact: v1 draft

The "how to adopt" weakness Cohere flagged would have shipped. A reader trying to adopt the pattern would have hit the gap and asked the author for the missing detail. The author would have answered, and the answer would have lived in an email rather than the published artefact. Multiple readers would have asked the same question.

The cost of three-assessor consensus is roughly 2x to 3x the assessment-stage cost. The benefit is the dissent that drives a refine that ships once instead of being asked many times.

## Quality and safety, all ways, always.
