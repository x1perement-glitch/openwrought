# SPM 0.1 Trial 01 — 20 real claims

**Date:** 2026-09-15  
**Status:** completed first-pass stress test  
**Purpose:** test whether Source Provenance Mark 0.1 can describe real claim lineage without hiding uncertainty.

This is a single-operator first pass. It tests internal applicability and exposes edge cases; it does **not** establish inter-rater reliability. Human timing was not measured, so effort is recorded as relative overhead (`low`, `medium`, `high`) rather than invented stopwatch data.

## Result summary

- 20/20 claims could be forced into syntactically valid SPM 0.1 marks.
- 9/20 produced material classification ambiguity.
- 19/20 gained at least some audit value; a very simple direct quotation gained little beyond an ordinary citation.
- Marking overhead: 11 low, 7 medium, 2 high.
- The strongest failure is not syntax. It is **semantic compression**: several different provenance questions are collapsed into single fields.

### Four failures exposed

1. **`verification` conflates source checking with claim validation.** A source can be checked while an inference drawn from it remains unvalidated.
2. **`ai_role` describes production of the marked claim, but not AI involvement in the source being cited.** These are independent facts.
3. **`relation` forces a choice between `synthesis` and `inference`, even when a claim is both.**
4. **Global `source_class` loses source-by-source structure in multi-source claims.** An array says which classes are present, but not which source has which class.

## Cases

| # | Claim under test | SPM 0.1 mark | Ambiguity | Effort | Audit value | Observation |
|---|---|---|---|---|---|---|
| 1 | C2PA defines provenance as the “logical concept of understanding the history of an asset and its interaction with actors and other assets.” | `[primary | quote | assisted | checked]` | low | low | medium | Works cleanly. AI selected the quote but did not author its language. |
| 2 | C2PA 2.4 added an AI Disclosure Assertion for machine-readable AI transparency information. | `[primary | paraphrase | generated | checked]` | low | low | medium | Clean single-source paraphrase. |
| 3 | C2PA authenticity is about cryptographically verifiable tamper evidence, not a guarantee that content is semantically true. | `[primary | inference | generated | checked]` | **high** | medium | high | `checked` only means the specification was inspected; it does not independently validate the inference about truth. |
| 4 | RFC 9110 states that “HTTP is a stateless application-level protocol for distributed, collaborative, hypertext information systems.” | `[primary | quote | assisted | checked]` | low | low | low | Ordinary citation already communicates most of the useful lineage. |
| 5 | NISO argues that provenance and attribution are central to verifying generative-AI outputs. | `[primary | paraphrase | generated | checked]` | low | low | medium | Primary relative to a claim about NISO's stated position. |
| 6 | NISO workshop reporting identifies a minimum provenance payload as an initial step for AI-mediated scholarly content. | `[primary | paraphrase | generated | checked]` | low | low | medium | Clean if claim is explicitly about the workshop report. |
| 7 | The information-standards community is converging on provenance as a near-term AI problem. | `[primary, secondary | synthesis | generated | checked]` | **high** | high | high | Source class changes depending on whether the claim is about NISO, workshop participants, or the broader community. Multiple NISO pages are not independent corroboration. |
| 8 | NISO's minimum-provenance work and SPM's claim-level notation are complementary layers rather than competing standards. | `[primary, primary | inference | generated | checked]` | **high** | high | high | This is both multi-source synthesis **and** a new inference. SPM 0.1 permits only one relation value. |
| 9 | The 2026 generative-search audit used 712 real-world human-generated queries. | `[primary | paraphrase | generated | checked]` | low | low | medium | Clean empirical-paper paraphrase. |
| 10 | The audit found evidence of AI-generated sources in roughly 16% of cited sources across four generative search engines. | `[primary | paraphrase | generated | checked]` | low | low | high | Important distinction: `ai_role=generated` describes this test claim, not the AI status of sources studied by the paper. |
| 11 | A normal-looking citation can resolve to a source for which there is evidence of AI generation without making that lineage obvious to the reader. | `[primary | inference | generated | checked]` | **high** | medium | high | The source supports the premise; `checked` can be mistaken for validation of the broader inference. |
| 12 | Saying “16% of citations were AI-generated” overstates the audit, which reports evidence of AI-generated **sources**, not proof that the citations themselves were generated. | `[primary | inference | generated | checked]` | **high** | medium | high | Useful provenance distinction, but again source inspection and inferential validation are collapsed. |
| 13 | The Openwrought SPM protocol defines five required fields, and the JSON schema independently encodes those same required fields. | `[primary, primary | observation | generated | tested]` | **medium** | medium | high | Re-fetching both repository files makes this reproducibly testable, but `observation` versus `paraphrase` is debatable. `tested` also needs the test method recorded. |
| 14 | WHO estimated about 95,000 measles deaths globally in 2024. | `[primary | paraphrase | generated | checked]` | low | low | medium | Clean official-data paraphrase. |
| 15 | WHO reports first-dose measles vaccination coverage of 84% in 2025, below the 2019 level of 86%. | `[primary | paraphrase | generated | checked]` | low | low | medium | Clean official-data paraphrase. |
| 16 | WARC is a standardized format for storing web-archive content and related metadata. | `[primary, primary | synthesis | generated | corroborated]` | **medium** | medium | high | Library of Congress plus ISO/IIPC provide independent evidence streams. Global source-class arrays still lose source-to-class pairing. |
| 17 | The Library of Congress says its web archives are stored in WARC and, for some older collections, ARC formats, with multiple copies maintained. | `[primary | paraphrase | generated | checked]` | low | low | medium | Clean claim about the Library's own practice. |
| 18 | RPG Maker Chat currently reports 100% archive completion and 151,945 RPG Maker Web threads secured. | `[primary | paraphrase | generated | checked]` | low | low | medium | Primary to the archive operator's current status claim; not independent proof that every source thread was captured correctly. |
| 19 | A July 2026 Reddit user reported that embedded YouTube videos did not play in ReplayWeb.page and did not appear to be contained in their WARC files. | `[primary | paraphrase | generated | checked]` | **medium** | medium | high | Primary evidence that the user reported the experience, not primary evidence for a general technical rule. Claim wording is doing essential provenance work. |
| 20 | Browsertrix WARC captures do not preserve embedded YouTube videos. | `[unknown | inference | generated | located]` | **high** | medium | high | The only evidence used here is a single user report. `located` confirms the report exists but can look like partial substantive verification even though the generalized claim remains unvalidated. |

## Source set

1. C2PA 2.4 technical specification — https://spec.c2pa.org/specifications/specifications/2.4/specs/C2PA_Specification.html
2. RFC 9110 — https://www.rfc-editor.org/rfc/rfc9110.html
3. NISO, *For AI Systems, Provenance Is Fundamental to Building Knowledge, Trust, and Assessment* — https://www.niso.org/niso-io/2026/05/ai-systems-provenance-fundamental-building-knowledge-trust-and-assessment
4. NISO, *Workshops Highlight Standards Needed for Tracking Provenance, Attribution, and Usage in the AI Ecosystem* — https://www.niso.org/niso-io/2026/06/workshops-highlight-standards-needed-for-AI-ecosystem
5. Allaham & Diakopoulos, *Synthetic Sources?* — https://arxiv.org/abs/2605.23684
6. WHO measles fact sheet — https://www.who.int/news-room/fact-sheets/detail/measles
7. Library of Congress Web Archiving FAQ — https://www.loc.gov/programs/web-archiving/about-this-program/frequently-asked-questions/
8. ISO 28500:2017 WARC — https://www.iso.org/standard/68004.html
9. IIPC WARC 1.1 — https://iipc.github.io/warc-specifications/specifications/warc-format/warc-1.1/
10. RPG Maker Chat archive status — https://rpgmakerchat.com/
11. Reddit /r/DataHoarder, *Archiving embedded videos* — https://www.reddit.com/r/DataHoarder/comments/1ul2ixt/archiving_embedded_videos/
12. Openwrought SPM protocol and schema — `protocols/source-provenance-mark-001.md`, `schemas/source-provenance-mark-001.schema.json`

## What survives from 0.1

The basic idea survives: exposing claim lineage at the claim level is useful, and the compact mark forces useful questions that ordinary citations do not.

The field model does **not** survive unchanged.

## Proposed 0.2 direction

Do not patch the labels cosmetically. Split the dimensions:

### 1. Source-level records

Each source should carry its own metadata instead of sharing one global class:

```text
sources[] = {
  ref,
  class,
  source_ai_status,
  source_check
}
```

Suggested `source_ai_status`: `human-declared | ai-declared | mixed-declared | unknown`.

### 2. Separate transformation from reasoning

```text
transformation = observation | quote | paraphrase | synthesis
reasoning = none | inference
```

A claim can therefore be `synthesis + inference` without losing either fact.

### 3. Rename AI field

`ai_role` → `claim_ai_role` so it is explicit that this describes production of the marked claim.

### 4. Split verification

```text
source_check = unlocated | located | content-checked
claim_validation = unvalidated | corroborated | tested
```

If `tested`, record a `validation_method` or stable test reference.

## Decision

**SPM 0.1 should not be promoted as-is.** The experiment supports a 0.2 redesign rather than abandonment. The core value is real, but the current fields compress materially different kinds of provenance into labels that can imply more verification than was actually performed.

## Next test

Build SPM 0.2 from these failures, then re-mark the same 20 claims without changing their wording. Success criterion: materially fewer ambiguous cases without more than modest additional marking overhead. After that, use at least one independent human rater before calling the notation stable.
