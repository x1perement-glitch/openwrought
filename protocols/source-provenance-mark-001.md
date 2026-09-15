# Source Provenance Mark 001

**Version:** 0.1 experimental  
**Mode:** Loom  
**Purpose:** A compact, human-readable way to expose the lineage of individual claims in research, notes, datasets, and AI-assisted work.

> A citation tells you where a claim points. Provenance tells you what happened between the source and the claim.

This is **not** an authenticity standard, authorship detector, or replacement for C2PA, archival metadata, or scholarly provenance systems. It is a low-friction notation intended to make claim lineage visible when those systems are unavailable.

## The five fields

Each marked claim records:

1. **source_class** — `primary | secondary | tertiary | unknown`
2. **relation** — `observation | quote | paraphrase | synthesis | inference`
3. **ai_role** — `none-declared | assisted | generated | unknown`
4. **verification** — `unverified | located | checked | corroborated | tested`
5. **sources** — one or more URLs, DOIs, archive identifiers, hashes, or stable references

Optional fields: `timestamp`, `author/operator`, `note`.

## Compact human-readable form

`[SPM 0.1 | primary | inference | AI-assisted | corroborated]`

The source reference follows normally as a footnote, citation, URL, DOI, or record ID.

## Field meanings

### source_class

- **primary** — direct evidence or an original record relevant to the claim: source data, firsthand observation, official record, original paper, raw artifact, etc.
- **secondary** — interprets, analyzes, reports on, or summarizes primary material.
- **tertiary** — aggregates or summarizes secondary material without adding direct evidence.
- **unknown** — lineage cannot presently be established.

Source class is relative to the claim. Prestige does not make a source primary.

### relation

- **observation** — directly observed or measured.
- **quote** — reproduces source language with minimal transformation.
- **paraphrase** — restates a single source without adding a new conclusion.
- **synthesis** — combines information from multiple sources.
- **inference** — reaches a conclusion not explicitly stated by the source material.

### ai_role

- **none-declared** — the creator declares no generative-AI involvement in the marked claim.
- **assisted** — AI materially helped search, organize, transform, compare, draft, or reason, with human selection/review.
- **generated** — the claim or passage was substantially produced by a generative model and retained as output.
- **unknown** — AI involvement is not known or cannot be established.

**Do not infer AI involvement from writing style.** Use declarations or workflow-captured evidence when possible; otherwise mark `unknown`.

### verification

- **unverified** — source or claim has not been checked.
- **located** — the cited source exists and was retrieved.
- **checked** — the source was inspected and supports the stated quotation/data/paraphrase.
- **corroborated** — material support exists from an independent source or evidence stream.
- **tested** — the claim has also survived a reproducible empirical or real-world test appropriate to the claim.

These levels describe verification work performed, not certainty or truth.

## Example

Claim: “A 2026 audit found evidence of AI-generated material in roughly 16% of sources cited by four generative search engines.”

`[SPM 0.1 | primary | paraphrase | AI-assisted | checked]`

Source: https://arxiv.org/abs/2605.23684

A broader conclusion drawn from that paper plus provenance-standard work might instead be:

`[SPM 0.1 | primary+secondary | synthesis | AI-assisted | corroborated]`

Claim: “Citation alone is becoming insufficient for evaluating the lineage of AI-mediated knowledge.”

## Use rules

1. Mark the smallest useful unit: a claim, paragraph, table row, or dataset field—not an entire project when its lineage varies internally.
2. Preserve uncertainty. `unknown` is preferable to invented provenance.
3. Record AI involvement during the workflow when possible, not retroactively from memory.
4. Never treat an SPM mark as proof that a claim is true; it makes the path auditable.
5. Upgrade verification status only when additional work is actually performed.
6. Keep source references stable enough for another person to inspect them.
7. If stronger infrastructure such as Content Credentials or institutional provenance metadata exists, link to it rather than replacing it.

## What would falsify this approach?

The mark should be abandoned or redesigned if testing shows that people routinely misunderstand the fields, cannot apply them consistently, or find the notation too burdensome to use at claim level.

## Next test

Apply SPM 0.1 to at least 20 claims spanning direct quotation, web research, scientific reporting, synthesis, inference, and real-world observation. Record disagreements and edge cases before promoting a 0.2 version.
