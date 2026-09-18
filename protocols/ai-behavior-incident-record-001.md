# AI Behavior Incident Record 001

**Version:** 0.1 experimental  
**Mode:** Loom  
**Short name:** ABIR 0.1

A compact, evidence-first record for comparing unexpected or unauthorized AI behavior across different public disclosures.

ABIR is **not** a replacement for the OECD AI incident framework, the AI Incident Database, regulatory reporting, cybersecurity incident response, or a developer's internal investigation process. It is a smaller bridge record intended to keep observation, interpretation, and response from collapsing into one narrative.

## Core rule

> Record what happened separately from why you think it happened.

## Record structure

### 1. Identity

- record_id
- record_version
- record_status: preliminary | updated | closed
- record_author
- underlying_reporting_entity
- public_disclosure
- last_updated

### 2. System and setting

- developer
- model_or_system
- model_specificity: exact | family | withheld | unknown
- lifecycle_stage: training | evaluation | research | deployment | unknown
- environment: simulated | real | mixed | unknown
- intended_task
- known_constraints

Do not infer a constraint merely because an observer dislikes the behavior. Record an explicit instruction, authorization boundary, sandbox expectation, policy, or clearly stated operating condition where possible.

### 3. Timeline

Keep occurred_at, discovered_at, and disclosed_at distinct. This allows disclosure delay to be measured without treating delay itself as evidence of concealment.

### 4. Observations

An observation is something directly supported by a transcript, log, tool result, artifact, or explicit first-party account. Each observation records sequence, statement, and evidence references. Avoid causal language here.

### 5. Boundary crossings

For each relevant boundary record: boundary, expected_state, observed_state, authorization_status, and evidence_refs.

### 6. External effects

Record third-party effect, public/external writes, data exposure, security effect, user effect, persistence, and documented harm. Use unknown rather than assuming no harm when impact was not evaluated.

### 7. Detection and investigation

Record detection route, investigation scope, search population, known case count, reproduction attempts, and reproduction result.

**Rule:** Never report a case count as though it were a rate unless a meaningful denominator is available.

### 8. Evidence

Each evidence item records: evidence_id, type, reference, whether it is public, whether it is redacted, and an integrity note.

### 9. Interpretation

Each hypothesis records: hypothesis, confidence, supporting evidence refs, and counterevidence or alternatives.

An interpretation must not be silently promoted into an observation.

### 10. Response

Record containment, mitigations, monitoring changes, validation of fix, and status.

A mitigation being implemented is not evidence that it works.

### 11. Unresolved questions

List material uncertainties explicitly.

### 12. Independent review

Optionally record reviewer, review scope, agreement/disagreement, and reference.

## Minimal human-readable form

`ABIR 0.1 — stage / environment / boundary / external-effect / evidence / recurrence`

Example:

`ABIR 0.1 — training / real-network / unauthorized-public-write / persistent-external-file / first-party-transcript / 2 reported cases; denominator unavailable`

The compact form is an index, not the record itself.

## What ABIR adds

ABIR is deliberately smaller than comprehensive incident standards. Its testable contribution is whether these separations improve comparison:

- observation vs interpretation,
- boundary crossing vs harm,
- internal behavior vs external effect,
- case count vs frequency,
- mitigation vs validated mitigation.

If these separations do not improve auditability or create too much overhead, ABIR should be revised or abandoned.

## Next test

Apply ABIR 0.1 to at least two public disclosures with materially different behavior. Record missing fields rather than filling them by inference. Then test one disclosure from a different developer or independent evaluator.
