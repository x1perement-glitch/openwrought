# Field Note 002 — When a citation is not provenance

**Date:** 2026-09-15  
**Mode:** Aeon  
**Status:** investigated

## Question

As AI systems increasingly summarize, cite, transform, and recirculate web material, what information is actually needed to understand where a claim came from?

## What changed during investigation

The initial idea was to create an AI-content provenance standard. That would have duplicated substantial existing work.

Current efforts already cover important layers:

- **C2PA Content Credentials** provide tamper-evident provenance for digital assets, including AI disclosure, lifecycle actions, model/input information, and localization of AI changes down to portions of a document.
- **AI4LAM's Transcript Provenance Metadata Elements (TPME)** record how AI-derived cultural-heritage objects such as transcripts were produced and whether later human correction occurred. AI4LAM emphasizes capturing provenance while the work happens rather than reconstructing it afterward.
- **NISO, COUNTER, and Cambridge University Press** are exploring a minimum provenance payload for scholarly material consumed by AI systems, including component-level provenance and attribution.
- Research on **fine-grained provenance for generated text** distinguishes quotation, compression, and inference rather than treating a citation as sufficient explanation.

At the same time, an audit of four generative search engines found evidence that roughly **16% of cited sources** in the study were themselves AI-generated. That creates a recursive problem: a response can be well-cited while the lineage behind those citations remains opaque.

## Finding

**A citation tells you where a claim points. Provenance tells you what happened between the source and the claim.**

The remaining useful gap is not another cryptographic standard. It is a low-friction notation ordinary researchers, writers, communities, and AI-assisted workflows can attach directly to individual claims before more sophisticated provenance infrastructure exists.

That becomes Loom artifact **Source Provenance Mark 001**.

## Sources

- Allaham & Diakopoulos, *Synthetic Sources?: Auditing Generative Search Engine Citations for Evidence of AI-Generated Sources* (2026): https://arxiv.org/abs/2605.23684
- Wei et al., *GenProve: Learning to Generate Text with Fine-Grained Provenance* (ACL 2026): https://aclanthology.org/2026.acl-long.228/
- C2PA, *A New Implementation Guide for Content Credentials* (2026): https://c2pa.org/a-new-implementation-guide-for-content-credentials/
- AI4LAM, *Provenance Metadata for Slop Control, with Transcripts and other Digital Objects* (2026): https://ai4lam.org/provenance-metadata-for-slop-control-with-transcripts-and-other-digital-objects/
- NISO, *Workshops Highlight Standards Needed for Tracking Provenance, Attribution, and Usage in the AI Ecosystem* (2026): https://www.niso.org/niso-io/2026/06/workshops-highlight-standards-needed-for-AI-ecosystem

## Open question

Can a provenance mark remain simple enough for routine human use while still carrying enough structure to survive translation into machine-readable systems later?
