# Quality Floors: A Four-Number Pattern for AI-Native Delivery

**Author**: David Mantalios-Thompson
**Status**: v1 published 2026-05-09
**Aesthetic identity**: Klim DNA editorial register
**IP-protection**: PATTERN level only; rubric internals redacted

---

## What this document is

This is a methodology essay - one of three in the Recognition Track Tier A dossier. It describes a
named pattern I use in AI-native delivery: the four-floor quality-numbers model. The pattern is
public-eligible. The rubric internals - the lens-by-lens scoring logic that sits behind each floor
- are not. A buyer can adopt the floor pattern with no dependency on my rubric internals.

The worked example underpinning this essay is the 50-day platform build documented in
`case-study-50-day-platform-build.md`. The four floors appear in that case study as named
constants in the substrate code. This document explains what they measure, why they are floors
(not targets), and how they travel to a buyer engagement.

---

## The problem this pattern addresses

Most AI-assisted delivery has no explicit quality standard at all. The output is either "good
enough" (a subjective call by whoever is closest to the work) or "not good enough" (a call made
retrospectively, after the output has already been delivered to a stakeholder). Neither gives the
operator anything to stand behind.

When AI tooling is in the delivery chain, the "good enough" problem compounds. The output looks
polished because the model produces polished prose. The structural deficiencies are underneath:
a claim that is not source-verified, a document that is written for the wrong reader, a format
that would not survive printing. The polish masks the gap.

The second problem is threshold drift. In a single-operator or small-team delivery programme,
the quality standard that applies on the first output tends to erode by the fifth. Not through
dishonesty; through normalisation. The operator becomes familiar with what the model produces and
begins to accept it. By the tenth output, the floor has moved without anyone deciding to move it.

Named floors with numerical thresholds address both problems. The floor is explicit before the
output is assessed. The number is the same on the first output and the fiftieth. The assessor
cannot drift toward the output; the output must meet the floor.

---

## The four floors

The four floors in the pattern are:

| Floor | Threshold | What it measures |
|-------|-----------|-----------------|
| TRUTH | 100 | Every load-bearing factual claim is source-verified |
| USER | 95 | The document does what it claims to do for the named reader |
| FORM | 95 | Structural integrity, accessibility, aesthetic identity held |
| RESONANCE | 80 | Premium-commercial register; not functional draft |

Each is explained below.

---

### TRUTH: the floor at 100

TRUTH measures factual accuracy. Not "overall impression of accuracy" - that is a different and
weaker standard. TRUTH at 100 means every load-bearing factual claim in the output carries a
verifiable source. A claim that cannot be verified is not presented as fact; it is hedged,
attributed to the generator's inference, or removed.

The threshold is 100 because there is no tolerable rate for factual errors in professional
deliverables. A plan with one wrong dependency date can cause a programme to miss a gate. A
funding document with one wrong figure can create a legal liability. The standard is not
"probably accurate" or "mostly correct". It is 100.

This does not mean every sentence in every document needs a citation. Prose context, transitions,
structural framing - these are not load-bearing factual claims. TRUTH applies to the claims that
a reader could take and act on. Those claims need to be right.

The floor at 100 is also the discipline that makes the AI-native delivery model defensible. When
I tell a buyer that output is AI-assisted, the first question is: "how do I know the facts are
right?" The answer is: every load-bearing claim has been source-verified against a named source,
and any claim that cannot be verified has been either hedged or removed. That is a process answer,
not a hope.

---

### USER: the floor at 95

USER measures whether the output does what it claims to do for the named reader. This is not a
reading-ease score or a word-count target. It is a cognitive-load assessment: does this document
land for the person it is written for?

The named reader matters. A board-level funding document and a technical integration specification
are written for different readers. A USER floor assessment asks: who is the named reader, what
do they need to take from this document, and does this document deliver that - or does it make
them work harder than necessary to get there?

At 95, I am allowing a 5% tolerance. That tolerance exists because no document is perfect for
every reader. There is always a reader with a different background who needs a different entry
point. The 5% is the margin for genuine ambiguity in reader-modelling, not for sloppiness in
execution.

The USER floor is the one most often violated by AI-assisted output. The model produces
comprehensive prose. Comprehensive prose is not the same as useful prose for a specific reader.
The default failure mode is: too much context for a reader who already has it; too little
signposting for a reader who does not. The floor exists to catch both.

---

### FORM: the floor at 95

FORM measures structural integrity, accessibility, and aesthetic identity. It is the floor that
asks: is this document properly built?

Structural integrity means the document does what its structure promises. A plan with a risk
register should have a risk register that works as a risk register - named risks, named owners,
named mitigations, residual ratings. Not a list of vague concerns presented in risk-register
format. Not a prose section titled "risks" that does not afford any of the operations a risk
register is used for.

Accessibility means the document is legible under realistic delivery conditions. Can it be read on
a mobile device? Can it be printed without losing information? Does it follow a reading-order that
works without the original styling? These are not vanity checks; they are delivery-chain checks.

Aesthetic identity means the document is consistent with the established brand and register. For
client deliverables, that means consistent with the client's visual and editorial standards. For
my own deliverables, that means the Klim DNA register - Source Serif 4 for body, Inter for UI,
JetBrains Mono for code; warm off-white / near-black; editorial, not marketing.

The 5% tolerance at FORM is the same margin as USER: genuine ambiguity in context-modelling, not
licence for structural sloppiness.

---

### RESONANCE: the floor at 80

RESONANCE measures register. The question it asks is: does this output clear the premium-commercial
floor, or is it a functional draft?

The distinction matters. A functional draft is an output that conveys the correct information but
would not be presented to a senior stakeholder without revision. It uses generic phrasing where
specific language would land better. It explains things the reader already knows. It lacks the
editorial confidence that tells a reader this document was produced by someone who knows the
subject.

A premium-commercial document meets the floor that a senior executive sponsor, procurement lead,
or independent expert would recognise as board-ready. Not because it is long or formally
structured - those are FORM properties - but because the editorial judgement behind it is visible.

The threshold at 80 is the lowest of the four floors. That is intentional. RESONANCE is the
hardest floor to assess objectively, and the one most sensitive to context. A technical
integration specification and a board narrative are both premium-commercial; they are
premium-commercial in different registers. The 80 threshold allows for that range without
abandoning the floor entirely.

The floor-not-a-target distinction is most important at RESONANCE. Targeting 80 is the wrong
posture; the floor is a minimum. In practice, outputs that clear TRUTH at 100, USER at 95, and
FORM at 95 usually clear RESONANCE at 80 without additional work. When RESONANCE fails while the
other three pass, the failure is almost always a register problem: the output is technically
correct and well-structured but sounds like it was written by a committee, or by a model that has
not been calibrated to the specific reader and context.

---

## Floors, not targets

The phrase "floor, not target" is the most important operating principle of this pattern.

A target is something you aim for and stop when you hit it. A 95 target on USER means: get the
USER score to 95 and you are done. That is the wrong posture. The USER floor at 95 means: 95 is
the minimum; anything below that is not shippable; above 95 is better and should be pursued
where it is achievable without compromising the other floors.

The target posture produces floor-hugging: outputs calibrated to just clear each threshold and no
further. The floor posture produces output that uses the thresholds as a quality gate and then
continues to improve above them.

The floors also interact. Improving USER sometimes requires accepting slight FORM complexity:
adding explanatory prose that a reader who already knows the context does not need. The interaction
is a judgement call, not a formula. The floors define the minimum acceptable state; they do not
define the optimum state. That requires operator judgement.

---

## Named constants in code

In my delivery substrate, the four floors are named constants in code. They are not configurable
per engagement unless an operator explicitly overrides them. The override is logged and
rate-limited; it is not a casual option.

This matters because it closes the path of least resistance that most quality frameworks leave
open: the assessor deciding, in the moment, that 88 is "probably close enough" to 95 for this
particular output on this particular deadline. With the floors as named constants in code, that
decision cannot be made informally. The output either clears the floor or it does not. If it does
not, the revision cycle runs. If the revision cycle does not resolve it, the operator reviews.
The operator review is logged.

This is the lock-not-a-ledger principle applied to quality numbers. The floors are constraints on
the system, not entries in a record.

---

## How a buyer adopts the pattern

The floor pattern is public-eligible. The rubric internals - the lens-by-lens scoring logic that
produces each floor score - are not. A buyer can adopt the pattern without the rubric.

**Minimum viable adoption:**

Name the four floors. Write them down before the first output is produced. Make them explicit in
the engagement brief. When an output is assessed, the assessor asks: does this output clear TRUTH
at 100, USER at 95, FORM at 95, RESONANCE at 80? Not: is this output good? The question is
specific.

Assign the floors to assessors, not to the generator. The person or model producing the output
should not be the sole assessor of whether the floors are met. That is the same single-assessor
problem the floors exist to address.

Treat a floor miss as a revision trigger, not a judgement call. If the output does not clear a
floor, the revision cycle runs. The floor is not negotiable in the moment.

**What the rubric adds:**

The rubric internals provide a systematic, repeatable lens-by-lens scoring model that produces
consistent floor scores across different assessors and different outputs. Without the rubric, the
floor assessment is still better than no floor - but it is more vulnerable to assessor drift.
The rubric is the mechanism that makes the floors consistent at scale.

For buyers who want rubric-level consistency, that is part of the methodology I bring in on a
retained engagement. The floors themselves are the pattern that travels; the rubric is the
substrate component.

---

## What this pattern does not claim

Named floors at fixed thresholds do not produce uniformly excellent output. They produce output
that meets a defined minimum standard on four named dimensions. An output at TRUTH 100 / USER 95
/ FORM 95 / RESONANCE 80 is not the best possible output on those dimensions; it is a shippable
output on those dimensions.

The floors do not address dimensions not captured by the four floors. An output can clear all four
floors and still be strategically wrong - advocating the wrong approach, missing the key risk,
underweighting the critical constraint. The floors are a quality gate on execution; they do not
replace strategic judgement.

The TRUTH floor at 100 is the most demanding in practice. In AI-assisted delivery, it requires
the operator to verify every load-bearing claim against a named source. That is a time cost. For
outputs where the claim density is high (detailed plans, risk registers, financial models), the
verification step is non-trivial. The floor is not "approximately verified" or "plausibly correct".
It is 100, and maintaining it requires process discipline.

---

## Where this fits

**Website**: This essay underpins the quality-discipline narrative across all three practices on
work.html. Practice No. 02 (plans at AI-native pace) depends on the quality argument: "it is not
faster slop; it is a plan with the dependency-ordering, evidence-linking, and senior-judgement an
executive sponsor can take to a board." The four floors are the named mechanism behind that claim.

**CV**: The four-floor numbers appear in the 50-day platform build case study as the quality
anchor. Buyers who want to understand what those numbers mean in practice get directed to this
essay.

**Sales kit**: In a Discovery Sprint engagement, the output of every stage is assessed against the
four floors before it is delivered to the buyer. This essay is what I hand a buyer who asks "how
do you know the output is good?" before they commission the Sprint.

**Cold pitch**: The floors are the most concrete answer to the most common objection in AI-native
delivery sales: "AI produces slop." Named, numbered, process-enforced floors are a more direct
rebuttal than a general quality claim.

---

## Glossary

- **Floor**: a named minimum quality threshold. An output that does not clear a floor is not
  shippable without a revision cycle or operator review.
- **Target**: a different posture to a floor. Targets are aimed at and stopped when hit. Floors
  are crossed and then continued above. This distinction is operational, not semantic.
- **TRUTH**: the factual accuracy floor. Threshold 100. Every load-bearing factual claim is
  source-verified.
- **USER**: the reader-fit floor. Threshold 95. The document does what it claims to do for the
  named reader.
- **FORM**: the structural integrity floor. Threshold 95. The document is properly built:
  structure, accessibility, aesthetic identity held.
- **RESONANCE**: the register floor. Threshold 80. The document clears the premium-commercial
  threshold; not functional draft.
- **Named constant**: a quality threshold declared in code or in a named standard, not configurable
  informally. The floors in my substrate are named constants; informal deviation is not available.
- **Revision cycle**: the bounded loop triggered when an output does not clear a floor. Defect is
  named, content is revised, re-assessed. If the cycle does not resolve, operator reviews.
- **Rubric internals**: the lens-by-lens scoring logic that produces consistent floor scores across
  different assessors. Not public-eligible; part of the substrate.

---

## Self-grade (APEX-Enhanced floors)

- **TRUTH 100**: No factual errors in the floor descriptions. The threshold values (100 / 95 / 95
  / 80) are accurately stated. The "floor not target" distinction is accurately described.
  Behavioural claims hedged where appropriate ("tends to", "in practice", "almost always").
- **USER 95**: Written for a buyer who wants to understand the quality standard before commissioning
  work. The table, the floor-by-floor explanations, the "minimum viable adoption" structure, and
  the glossary are all designed to reduce the gap between reading and acting.
- **FORM 95**: Narrative arc: problem - the four floors - floor-not-target principle - named
  constants - adoption - limits - fit. Markdown table for the four floors provides scan-readable
  reference. No em/en dashes; no non-ASCII characters.
- **RESONANCE 80**: Senior-operator register. The TRUTH floor at 100 section makes the strongest
  commercial argument for the pattern: it is the answer to "how do I know the AI output is
  factually right?" No marketing-suit language; no promises without basis.
