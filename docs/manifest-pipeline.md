# Manifest Pipeline: A Stage-Gated Delivery Pattern for AI-Native Work

**Author**: David Mantalios-Thompson
**Status**: v1 published 2026-05-09
**Aesthetic identity**: Klim DNA editorial register
**IP-protection**: PATTERN level only; substrate names redacted

---

## What this document is

This is a methodology essay - one of three in the Recognition Track Tier A dossier. It describes a
named pattern I use in AI-native delivery: the manifest pipeline. The pattern is public-eligible.
The substrate I built it on is not. A buyer can adopt the pattern with no dependency on my
substrate.

The worked example underpinning this essay is the platform substrate build referenced in
an operator-internal worked example. Where I reference the build, the case study has the full
narrative; this document has the pattern mechanics.

---

## The problem this pattern addresses

AI-native delivery has a specific failure mode that conventional stage-gating does not address:
the AI shortcuts the pipeline.

In conventional delivery, the pipeline is enforced by human discipline and process gates. A
project manager does not submit a design document before the requirements document is approved;
the governance process stops them. That discipline is imperfect, but it exists.

In AI-native delivery, the generator does not have that discipline by default. The model is
capable of producing a polished final deliverable from a one-line brief. It will do so if asked.
The pipeline is not a constraint the model recognises; it is a constraint the operator must
enforce. And in a high-velocity delivery environment, the temptation to shortcut is constant.
The senior practitioner - me, or whoever is operating the AI tooling - is under pressure to
deliver quickly. The shortcut is always one prompt away.

The manifest pipeline addresses this by making the pipeline a lock, not a ledger. A ledger is a
record of what happened; it does not prevent anything. A lock is a constraint: the next stage
cannot start until the prior stage's output has been verified and its packet completed. The lock
is enforced in the system, not by the operator's discipline.

The second problem the pattern addresses is observability. In AI-native delivery, the audit trail
of how an output was produced is often invisible. A buyer who asks "how was this produced?" gets
a general answer: "AI-assisted, reviewed by a senior practitioner." They cannot see which
information fed which stage, what was evaluated and by whom, or where the operator exercised
judgement and why. The manifest pipeline makes every stage transition explicit and traceable.

---

## The manifest pipeline pattern

A manifest is a structured document that describes a complete piece of delivery work as a
sequence of stage-gated packets. Each packet declares:

- **Stage number and name** (e.g. Stage 1 Research, Stage 2 Generate, Stage 3 Evaluate,
  Stage 4 Refine, Stage 5 Verify, Stage 6 Build, Stage 7 Quality-gate)
- **Model tier** (which class of model or process should execute this stage)
- **Inputs** (what the packet requires before it can start)
- **Outputs** (what the packet must produce to be considered complete)
- **Dependencies** (which prior packets must be complete before this one can be claimed)

A packet moves through three states: pending, in-progress (claimed), and complete. A packet
cannot be claimed until its dependencies are complete. A packet cannot be completed without a
result reference - a named output file or artefact that demonstrates the stage was executed.
The completion is validated: if the result type does not match what the packet declared as its
output, the completion is rejected.

This is the lock mechanism. The stage cannot be advanced by intention; it must be advanced by
execution. A packet declared as "Stage 2 Generate / outputs: specification document" cannot be
completed with a final HTML deliverable. The system rejects it. The only way to complete Stage 2
is to produce a specification document.

---

## Stage sequencing and the lock principle

The standard stage sequence in the pattern is:

**Stage 1 - Research**: domain research, evidence gathering, brief clarification. Output is a
structured research document. Model tier: sonnet-class generation plus search capability.

**Stage 2 - Generate**: a specification document (a TSOM-style prompt, in my deployment) that
describes what the final output should be: its requirements, constraints, architecture, and
quality expectations. This stage produces a specification, not the final artefact. Model tier:
sonnet-class generation.

**Stage 3 - Evaluate**: independent assessment of the specification against the quality floors
(documented in `quality-floors-methodology.md`). This is the stage where the three-Eye consensus
runs (documented in `multi-eye-consensus-methodology.md`). Model tier: external-diverse.

**Stage 4 - Refine**: revision of the specification based on the evaluation results. If Stage 3
produces a conditional or block verdict, the defect is named and the specification is revised.
Model tier: sonnet-class generation.

**Stage 5 - Verify**: mechanical verification of the refined specification. Checks that all
required inputs are present, all declared outputs are reachable, all dependencies are correctly
stated. Model tier: mechanical (no language model needed for this stage).

**Stage 6 - Build**: construction of the final deliverable against the verified specification.
This is the only stage that produces the final artefact. It cannot run until Stage 5 is complete.
Model tier: sonnet-class generation with execution capability.

**Stage 7 - Quality-gate**: mechanical and assessment checks on the final deliverable. Includes
text quality (word count, structure, no-ASCII-error checks), visual quality (if applicable), and
witness tests (interaction checks, if applicable). Model tier: mechanical plus assessment.

The lock principle operates at every transition. Stage 2 cannot start until Stage 1 is complete.
Stage 3 cannot start until Stage 2 is complete and its output type has been validated. Stage 6
cannot start until Stage 5 is complete. There is no path to Stage 6 that bypasses Stage 3.

---

## Why the lock principle matters for AI-native delivery

The pipeline enforcement problem in AI-native delivery is not theoretical. It is the pattern that
produces the most common class of quality failure in AI-assisted work: orphan artefacts.

An orphan artefact is a deliverable produced by a generator without going through the pipeline.
It may be polished. It may be factually accurate. It may look exactly like a pipeline-produced
artefact. The difference is: there is no audit trail of how it was produced, no record of what
specification it was built against, no evaluation verdicts showing that it cleared the quality
floors, and no verification that the inputs were complete and correct.

For a buyer, an orphan artefact is uncertifiable. It cannot be independently audited. It cannot be
re-run against the same specification to produce a consistent output. It cannot be traced back to
a named source for each load-bearing claim. The quality discipline that the pipeline enforces is
simply absent.

The temptation to produce orphan artefacts is not malicious; it is structural. In a high-velocity
AI delivery environment, the path of least resistance is always to generate the final output
directly. The manifest pipeline closes that path by making it impossible to mark a stage complete
without producing and validating its declared output. The model cannot shortcut because the system
does not accept the shortcut.

---

## Double-claim prevention and operator-override

The manifest pipeline includes two additional integrity mechanisms.

**Double-claim prevention**: a packet that is already in-progress cannot be claimed by a second
operator. This prevents two parallel workstreams from attempting to complete the same stage
simultaneously - which would produce two result references for the same packet and break the
traceability chain.

**Operator-override**: there are legitimate reasons to skip stages or override validation rules.
A direct operator instruction for a well-scoped task. A stage whose output type does not match
the standard validation because the task is non-standard. An engagement where the buyer has
explicitly scoped out certain stages.

Operator-override is available in the manifest system. It requires: an explicit reason, logged in
the manifest record; a rate limit (the fourth override on a single manifest requires an
accumulation confirmation); and a flag in the completion record that the override was used. The
AI cannot use operator-override autonomously; it is an explicit decision by the operator, logged
with a reason.

This distinction matters for buyers. The pipeline is not a bureaucratic system that blocks
legitimate work. It is a discipline system that requires legitimate deviations to be explicit and
logged rather than silent and invisible.

---

## Model tier routing

Each packet declares a model tier. The tier is not just a performance hint; it is a routing
declaration. Generation work runs on sonnet-class models. Evaluation work runs on
external-diverse models (the three Eyes). Mechanical work runs on script-based processes with no
language model. Orchestration decisions run on opus-class models.

The tier routing prevents two common drift patterns in AI-native delivery:

**Extended-reasoning tasks on a tier below the declared tier.** If a packet declares opus-class
for orchestration, running it on sonnet-class is drift. The manifest system flags this; inline
execution on the wrong tier is an oversight the system should surface.

**Research on opus-class when sonnet-class is sufficient.** The reverse drift: running expensive
model capacity on tasks that do not need it. This is a cost problem as well as a routing problem;
the manifest tier declaration is the discipline that prevents it.

Buyers who adopt the pattern should think of the tier declaration as a contract: the packet's
output is only certified if it was produced by a model at or above the declared tier. Outputs
produced on a lower tier may be acceptable in practice, but they are not certified by the manifest.

---

## How a buyer adopts the pattern

The pattern is public-eligible. A buyer can implement it with no dependency on my substrate.

**Minimum viable adoption:**

Define your delivery stages before any output is produced. Name them. Declare the input each
stage needs and the output each stage must produce. Write this down in a structured document
before the first prompt is sent.

Enforce the claim / complete cycle. Before a stage starts, the operator claims it. The claim is
a commitment: I am responsible for this stage's output. Before the next stage starts, the current
stage is completed with a named result reference.

Validate output types at completion. A stage declared to produce a specification cannot be
completed with a final deliverable. The validation can be manual for small-scale adoption; it
should be automated for sustained programmes.

Log every operator-override with a reason. Overrides are legitimate; silent overrides are not.
The log is the accountability mechanism.

**What the substrate adds:**

In my deployment, the manifest is a JSON-Schema-conformant object, the claim and complete cycle
is enforced by scripts, and the output-type validation is mechanical. For a buyer adopting the
pattern manually, the mechanical enforcement is replaced by process discipline. The pattern works
at either level; the mechanical enforcement makes it more robust at scale.

**The adoption sequence I recommend:**

Start with a single engagement type - one scope, one standard stage sequence. Run three to five
engagements using the manual version of the pattern. Look at where the discipline holds and where
it does not. The failure points tell you which stages are most likely to be shortcut without
mechanical enforcement. Build the mechanical enforcement for those stages first.

---

## What this pattern does not claim

The manifest pipeline is designed to enforce the sequencing and traceability of delivery work. It
does not enforce the quality of the work within each stage. A Stage 2 specification that is
complete (declared outputs produced, dependencies met) but poor in quality will advance through
the pipeline. The quality floors (documented in `quality-floors-methodology.md`) and the
three-Eye evaluation (documented in `multi-eye-consensus-methodology.md`) are the mechanisms that
address quality within stages. The manifest pipeline is the mechanism that ensures the stages run
in order and produce traceable outputs.

The pattern also does not address scope creep within a stage. A Stage 6 Build packet can be
completed with a deliverable that does not match what the Stage 2 specification required - if the
operator validates the completion without checking against the specification. The output-type
validation is a format check, not a content check. Content alignment with the specification
requires operator review at the Stage 6 completion step.

---

## Where this fits

**Website**: This essay underpins the delivery discipline narrative across all three practices on
work.html. It is the structural answer to "how do you prevent AI-native delivery from becoming
fast slop with no governance?" The pipeline is the governance.

**CV**: The manifest pipeline pattern is the named methodology behind the "stage-gated delivery"
reference in an operator-internal worked example. Buyers who want to understand the governance
model behind the AI-native delivery practice get directed here.

**Sales kit**: In a Discovery Sprint engagement, the Sprint itself is structured as a manifest: a
defined research stage, an analysis stage, a recommendation stage, and a delivery stage. The
buyer gets a delivered result with a traceable audit trail, not an AI-generated document of
uncertain provenance.

**Cold pitch**: The manifest pipeline is the direct answer to the "AI governance" question in
enterprise sales. Most buyers in regulated sectors need to be able to answer: how was this
produced? The manifest pipeline makes that answer concrete and specific.

---

## Glossary

- **Manifest**: a structured document describing a piece of delivery work as a sequence of
  stage-gated packets. One manifest per engagement or deliverable unit.
- **Packet**: a single stage within a manifest. Declares its stage number, model tier, inputs,
  outputs, and dependencies.
- **Claim**: the act of marking a packet in-progress and assigning it to an operator. A packet
  that is not claimed cannot be completed.
- **Complete**: the act of marking a packet done, with a named result reference. The completion
  is validated against the packet's declared output type.
- **Lock principle**: the constraint that the next stage cannot start until the prior stage is
  complete and its output validated. The pipeline is a lock, not a ledger.
- **Orphan artefact**: a deliverable produced outside the pipeline, without a manifest audit trail.
  Orphan artefacts cannot be certified by the pipeline; their traceability is broken.
- **Double-claim prevention**: the constraint that a packet already in-progress cannot be claimed
  by a second operator.
- **Operator-override**: an explicit, logged exception to a pipeline validation rule. Not
  available autonomously; requires a stated reason and is rate-limited.
- **Model tier**: the class of model or process appropriate for a given stage. Declared in the
  packet; routing should be enforced, not honour-based.
- **Orphan-artefact risk**: the structural temptation in high-velocity AI delivery to generate
  final outputs directly, skipping the pipeline. The manifest lock closes this path.

---

## Self-grade (APEX-Enhanced floors)

- **TRUTH 100**: Stage names, stage sequence, and stage descriptions are accurately stated and
  consistent with the pattern as deployed in an operator-internal worked example. Operator-override
  behaviour accurately described (explicit, logged, rate-limited). No substrate names asserted.
  Behavioural claims hedged where appropriate.
- **USER 95**: Written for a technically-literate buyer or senior practitioner who wants to
  understand the governance model behind AI-native delivery. The minimum-viable-adoption section
  and the glossary reduce the gap between understanding and acting.
- **FORM 95**: Narrative arc: problem - pattern mechanics - lock principle - double-claim and
  override - model tier routing - adoption - limits - fit. No em/en dashes; no non-ASCII
  characters.
- **RESONANCE 80**: The "lock not a ledger" framing and the orphan-artefact concept give the essay
  a distinctive editorial register rather than generic methodology documentation. No
  marketing-suit language.
