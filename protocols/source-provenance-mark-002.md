# Source Provenance Mark 002

**Version:** 0.2 experimental  
**Mode:** Loom  
**Status:** redesign after SPM 0.1 Trial 01

> A citation identifies a destination. Provenance records the path from evidence to claim.

SPM 0.2 is a compact claim-lineage notation. It is not a truth score, authenticity detector, or replacement for C2PA, scholarly metadata, archival provenance, or cryptographic credentials.

## Why 0.2 exists

SPM 0.1 could mark all 20 trial claims, but 9/20 produced material ambiguity. The failures came from compressing distinct questions into single fields. Version 0.2 separates them.

## Claim record

Each marked claim contains:

1. `transformation` — `observation | quote | paraphrase | synthesis`
2. `reasoning` — `none | inference`
3. `claim_ai_role` — `none-declared | assisted | generated | unknown`
4. `claim_validation` — `unvalidated | corroborated | tested`
5. `sources[]` — source-level provenance records
6. optional `validation_method`, `timestamp`, `author_operator`, `note`

## Source record

Each source independently records:

- `ref` — URL, DOI, archive identifier, hash, repository path, or stable record ID
- `class` — `primary | secondary | tertiary | unknown`
- `source_ai_status` — `human-declared | ai-declared | mixed-declared | unknown`
- `source_check` — `unlocated | located | content-checked`

`source_ai_status` records only declared or workflow-captured evidence. Do not infer AI authorship from style.

## Dimensions

### transformation

- `observation` — claim records a direct measurement or inspection performed by the claimant/operator.
- `quote` — source language is reproduced with minimal transformation.
- `paraphrase` — one source is restated without a materially new conclusion.
- `synthesis` — information from multiple sources is combined.

### reasoning

- `none` — no materially new conclusion is added beyond the transformation.
- `inference` — the claim reaches a conclusion not explicitly established by the source material.

This split permits `synthesis + inference`, a combination SPM 0.1 could not represent.

### claim_ai_role

- `none-declared` — creator declares no generative-AI involvement in producing the marked claim.
- `assisted` — AI materially aided search, organization, comparison, transformation, drafting, or reasoning, with human selection/review.
- `generated` — substantial claim language or reasoning was model-produced and retained.
- `unknown` — production history cannot be established.

This field concerns the marked claim, not the cited sources.

### source_check

- `unlocated` — reference has not been retrieved.
- `located` — reference was retrieved, but its substantive support was not checked.
- `content-checked` — source content was inspected for the claimed quotation/data/support.

### claim_validation

- `unvalidated` — no independent validation beyond checking cited sources.
- `corroborated` — materially independent evidence supports the claim.
- `tested` — the claim survived a reproducible empirical, computational, or real-world test appropriate to it.

If `tested`, include `validation_method` or a stable test reference.

## Compact form

A compact display describes the claim first, followed by numbered source records:

`[SPM 0.2 | paraphrase | no-inference | AI:generated | validation:unvalidated | S1]`

`S1 [primary | AI:unknown | content-checked] <reference>`

For a synthesis that also makes a new inference:

`[SPM 0.2 | synthesis | inference | AI:generated | validation:corroborated | S1,S2]`

The notation is intentionally descriptive rather than scored. A primary source is not automatically reliable; a tested claim is not automatically universally true.

## Use rules

1. Mark the smallest useful claim unit.
2. Pair metadata with each source; never use a global source-class array.
3. Preserve uncertainty. `unknown` is valid information.
4. Do not upgrade `claim_validation` merely because cited sources were inspected.
5. Corroboration requires a materially independent evidence stream, not several pages repeating the same origin.
6. `tested` requires a reproducible validation method or reference.
7. Record claim AI involvement separately from source AI status.
8. Do not infer source AI status from prose style.
9. Link stronger provenance infrastructure when available instead of duplicating it.

## Examples

### Direct standards quotation

Claim: C2PA defines provenance using a specific definition in its technical specification.

`[SPM 0.2 | quote | no-inference | AI:assisted | validation:unvalidated | S1]`

`S1 [primary | AI:unknown | content-checked] C2PA technical specification`

The source was checked; the claim is not labeled `corroborated` merely because the quote matches.

### Multi-source inference

Claim: Citation alone is becoming insufficient for evaluating lineage in AI-mediated knowledge.

`[SPM 0.2 | synthesis | inference | AI:generated | validation:corroborated | S1,S2]`

Each source receives its own class, AI status, and check state.

## Compatibility

SPM 0.2 is complementary to asset-level provenance such as C2PA and institutional metadata initiatives such as minimum provenance payload work. SPM asks a narrower question: *what happened between these particular sources and this particular claim?*

## Promotion gate

Do not call 0.2 stable until:

1. the exact 20 claims from SPM 0.1 Trial 01 are re-marked;
2. material ambiguity falls well below 9/20 without a large overhead increase; and
3. at least one independent human classification pass is compared with the Openwrought pass.
