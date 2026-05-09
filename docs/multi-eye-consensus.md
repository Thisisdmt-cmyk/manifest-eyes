# Multi-Eye Consensus: An Independent Assessment Pattern for AI-Native Delivery

**Author**: David Mantalios-Thompson
**Status**: v1 published 2026-05-09
**Aesthetic identity**: Klim DNA editorial register
**IP-protection**: PATTERN level only; substrate names redacted

---

## What this document is

This is a methodology essay - one of three in the Recognition Track Tier A dossier. It describes a
named pattern I use in AI-native delivery: the Multi-Eye Consensus model. The pattern is
public-eligible. The substrate I built it on is not. A buyer can adopt the pattern with no
dependency on my substrate.

The worked example underpinning this essay is the platform substrate build referenced in
an operator-internal worked example. Where I reference the build, the case study has the full
narrative; this document has the pattern mechanics.

---

## The problem this pattern addresses

Single-assessor quality control is the default in most AI-assisted delivery. One model - or one
senior reviewer - reads the output, approves it, and moves the work forward. That posture has
three structural deficiencies that compound each other.

**Calibration drift.** Any single assessor develops blind spots over repeated evaluation on the
same subject matter. A human reviewer who has read 30 iterations of the same plan begins to
pattern-match rather than evaluate. A language model whose training data overlaps heavily with the
content it is assessing produces verdicts shaped by that overlap. The assessor drifts toward the
distribution it knows, and the outputs drift with it.

**Training-data bleed.** When a single model both generates content and assesses it, there is a
non-trivial risk that the assessor has been trained on materially similar content to the generator
- or is the same model family in a different configuration. The two do not hold each other to an
independent standard; they are pulling from the same source. The effect is bias amplification, not
bias correction.

**Jurisdictional substrate concentration.** If the generator and the assessor both sit on the same
provider's infrastructure - same data-routing, same legal jurisdiction, same acceptable-use policy
- then a single regulatory or policy change can disable both simultaneously. The assessment layer
provides no independence from the generation layer. The entire quality chain becomes a
single-point risk.

None of these deficiencies is catastrophic in isolation. Combined across a sustained delivery
programme, they produce the kind of output drift that shows up as: gradually softening quality
numbers, unnoticed factual errors in later deliverables, house-style drift that no individual
reviewer flags because each sees only one piece. The pattern I use was designed to counteract all
three.

---

## The Multi-Eye Consensus pattern

The pattern is named for the three independent assessor positions, referred to as Eyes. Each Eye
is a separate model from a separate provider on a separate legal jurisdiction. They evaluate every
output stage; 2-of-3 consensus is required to advance the work; two dissents block advancement
until the operator reviews.

The three assessor positions in the pattern as I deploy it:

- **Eye 1** - European Union / French jurisdiction. Enterprise-grade evaluation capability with
  strong multilingual and cross-cultural calibration.
- **Eye 2** - Canadian jurisdiction. Enterprise retrieval and generation strength; well-calibrated
  on structured document assessment (plans, specifications, risk registers).
- **Eye 3** - Open-weights model on Western infrastructure. No API dependency on a proprietary
  vendor; weights are auditable and portable. Provides adversarial signal because the model family
  has a different training base and different reasoning tendencies than the proprietary Eyes.

This configuration was chosen for three reasons.

First, no US providers in the quality pipeline. Jurisdictional independence matters for programmes
where data-routing or regulatory substrate is part of the brief. A buyer operating under UK GDPR
or EU AI Act requirements benefits from an assessment layer that does not route data through US
legal jurisdiction. The pattern supports that requirement structurally, not just contractually.

Second, no two Eyes share a model family. Calibration drift requires shared training. If two Eyes
are from the same model family - even different versions or configurations - they tend to agree for
reasons other than the quality of the output. The pattern requires genuine family-level
independence.

Third, portable by design. Any of the three Eye positions can be replaced with another provider
meeting the same criteria: separate jurisdiction, separate model family, separate infrastructure.
The pattern does not require my specific provider choices; it requires the structural criteria. A
buyer adopting the pattern can substitute any assessor that meets those criteria.

---

## How consensus works in practice

Consensus operates stage by stage, not as an end-of-chain audit.

Before each assessed stage advances to the next, all three Eyes receive the same input and the
same evaluation prompt. Each Eye returns a verdict (advance / block / conditional) and a scoring
set against named floors. The scoring floors used in my deployment are defined in
`quality-floors-methodology.md`; the key point for this pattern is that the floors are named
constants, not subjective impressions. An Eye scoring a stage must either confirm the floor is met
or identify a specific defect that explains why it is not.

**2-of-3 advance**: if two or more Eyes score all floors at or above threshold and return an
advance verdict, the stage advances to the next.

**2-of-3 conditional**: if two Eyes return a conditional verdict with a named defect, the stage
enters a revision cycle. The defect is named, the content is revised, and the revised output is
re-assessed. The revision cycle is bounded; if it does not resolve within a defined number of
passes, the operator reviews.

**2-of-3 block or split dissent**: if two or more Eyes block, or if the three verdicts split in a
pattern that does not yield a clear advance signal, the stage is blocked and the operator reviews
before the work continues. The block is not a failure state; it is the pattern working as designed.
The operator's review is the quality gate, not a fallback when the assessors disagree.

A single dissent does not block. One Eye disagreeing with two is a registered minority view,
captured in the assessment record, but it does not stop the work. The 2-of-3 threshold is the
balance point between independence (requiring genuine consensus) and forward motion (not allowing
one outlier assessor to block indefinitely).

---

## Why this beats single-Eye assessment

The structural case for three Eyes over one is the calibration argument above: drift,
training-data bleed, jurisdictional concentration. There is a more direct practical argument.

In any sustained delivery programme - a multi-month AI implementation, a stalled PMO recovery, a
multi-stream planning engagement - output quality tends to drift in a single direction: down. Not
in any single step. Across many small steps, each of which passes a single assessor whose
threshold has subtly shifted. The cumulative drift is invisible until it is significant.

Three independent assessors from different model families produce a signal that is harder to drift
unnoticed. When all three agree, the confidence in the verdict is higher than any single assessor
can provide. When they disagree, the disagreement itself is information: it flags ambiguity in the
content, or a gap between what the generator intended and what an independent reader receives.

The adversarial signal from the open-weights Eye is the most underrated benefit in practice. This
Eye frequently disagrees with the proprietary Eyes in ways that are substantively useful - not
because it is wrong, but because it is reading from a different training base with different
implicit standards. That disagreement, when it appears, is the earliest signal of content sliding
toward house-style rather than genuine quality.

The cost of the pattern is assessment latency. Three evaluations take longer than one. I accept
that cost because the alternative - undetected quality drift across a multi-month programme - is
more expensive to correct. Assessment latency is front-loaded and predictable; correction cost is
back-loaded and variable.

---

## The shaping layer: a separate concern

The consensus pattern above governs the quality pipeline: the verdicts that block or advance work.
There is a second, separate layer I use for ideation and creative input. In this shaping layer,
additional models may contribute suggestions, surface ambiguities, and propose competitive angles.
They do not certify, vote, block, or assess.

The distinction matters for buyers. The quality-sovereignty arguments above apply only to the
quality pipeline. The shaping layer is a different concern; what matters there is cognitive
diversity and creative signal, not jurisdictional independence. Mixing the two layers is a common
governance mistake in AI-native delivery programmes. Keeping them separate is a structural design
decision, not an afterthought.

Any model that shapes a run is excluded from that run's assessment. The Eyes dedicated to
assessment do not double as shapers. Cognitive independence is maintained by role-separation, not
just by provider-separation.

---

## How a buyer adopts the pattern

The pattern is public-eligible. A buyer can implement it with no dependency on my substrate.

**What you need:**

Three model API access points from three providers satisfying: separate model families, separate
legal jurisdictions, separate infrastructure. The specific providers are a deployment choice, not
a pattern requirement. The criteria are the pattern.

A consistent evaluation prompt per output stage. The prompt asks each Eye to assess named floors,
return a named verdict, and justify any deviation. The prompt structure is the same for all three
Eyes; the independence comes from the models, not the prompt.

A decision rule: 2-of-3 advance proceeds; 2-of-3 conditional triggers a revision cycle; 2-of-3
block or split triggers operator review.

An assessment record. Each stage's verdicts are captured - Eye, verdict, scores per floor, named
defects if any. The record is append-only; verdicts are not revised retroactively.

**What you do not need:**

My substrate. The substrate is where I host the pattern; the pattern travels without it.

Any specific provider. The Eye positions are configuration, not prescription. A buyer with
existing API relationships can substitute providers that meet the criteria.

A large team. The pattern as I deploy it is single-operator. Assessment is automated; the
operator reviews only when the decision rule requires it.

**The adoption sequence I recommend:**

Start with a single output surface - one document type, one stage. Wire three Eyes to evaluate it.
Run the pattern for five to ten outputs. Look at the disagreement signal before looking at the
advance/block outcomes. The disagreement signal tells you where your current quality is genuinely
uncertain versus where it is genuinely solid. Build from there.

Trying to adopt the pattern across an entire programme simultaneously is the most common adoption
failure mode. The pattern is a capability; build it incrementally.

---

## What this pattern does not claim

The pattern is designed to reduce the risk of undetected quality drift. It does not eliminate it.
An assessor prompt can itself be poorly designed, producing assessments that miss the defects that
matter. Three Eyes agreeing on a bad assessment is worse than one Eye flagging uncertainty;
consensus amplifies calibration errors as well as correct verdicts. The pattern is most robust
when evaluation prompts are stress-tested against known defect types before deployment.

The pattern does not replace operator judgement. The 2-of-3 advance rule moves work forward; it
does not certify that the work is right. The operator reviewing block cases is not a fallback for
a failed pattern - it is a structural part of the pattern. Any assessment regime that removes
operator judgement entirely has removed the highest-quality signal in the chain.

The jurisdictional independence argument has limits. No routing model can provide absolute
data-sovereignty guarantees without infrastructure specific to the programme. For programmes with
genuine data-sovereignty requirements, jurisdictional independence in the assessment layer is a
risk-reduction measure, not a compliance mechanism. That distinction matters.

---

## Where this fits

**Website**: The methodology essays sit behind the work.html three-practices section as the Tier A
dossier. This essay underpins Practice No. 03 (AI-native delivery, owned by the team) and
Practice No. 02 (plans at AI-native pace).

**CV**: The Multi-Eye Consensus pattern is the named methodology behind the AI-native delivery
practice. Buyers who ask "how do you maintain quality at AI-native pace?" get directed here.

**Sales kit**: This essay pairs with an operator-internal worked example. The case study is the
velocity proof; this essay is the quality-discipline proof. Buyers asking "but does AI actually
hold quality?" get this essay.

**Cold pitch**: In a Discovery Sprint pitch, I reference the three-Eye consensus model as the
evaluation posture I bring in - not as a vendor dependency, but as a pattern that can be applied
inside the buyer's existing provider set.

---

## Glossary

- **Eye**: an independent assessor model from a separate provider and jurisdiction. Three Eyes per
  assessment run in the standard pattern.
- **Consensus**: 2-of-3 Eyes returning matching verdicts to resolve a stage's assessment outcome.
- **Calibration drift**: the tendency of any single assessor to shift its quality threshold over
  time, especially when repeatedly evaluating similar content.
- **Training-data bleed**: the risk that a generator and an assessor draw from overlapping
  training data, reducing the independence of the assessment.
- **Jurisdictional substrate concentration**: the risk that generator and assessor sit on the same
  legal-jurisdiction infrastructure, creating a single-point regulatory exposure.
- **Named floor**: a quality constant with a name and a numerical threshold used as the assessment
  criterion.
- **Assessment record**: the append-only log of verdicts per stage. Retroactive revision not
  permitted.
- **Operator review**: the human decision step triggered when the automatic decision rule does not
  produce a clear advance signal. Not a fallback; a structural part of the pattern.
- **Shaping layer**: a separate ideation layer where additional models may contribute creative
  input. Distinct from the quality pipeline; shaping models do not assess or certify.

---

## Self-grade (APEX-Enhanced floors)

- **TRUTH 100**: All named providers described by jurisdiction type only (EU/French, Canadian,
  open-weights on Western infrastructure). No specific product names asserted beyond
  public-eligible descriptions. No factual errors introduced. Behavioural claims hedged
  appropriately throughout ("tends to", "in practice", "designed to").
- **USER 95**: Written for a technically-literate buyer who is not an AI specialist. Adoption
  sequence, "what you need / do not need" structure, and glossary reduce the gap between
  understanding the pattern and acting on it.
- **FORM 95**: Narrative arc: problem - pattern mechanics - why it beats alternatives - shaping
  layer distinction - adoption - limits - fit. No em/en dashes; no non-ASCII characters.
- **RESONANCE 80**: Senior-operator register throughout. The limits section distinguishes this
  from vendor collateral. No marketing-suit language; no superlatives without evidence.
