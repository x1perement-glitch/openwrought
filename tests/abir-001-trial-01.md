# ABIR 0.1 — Trial 01

**Date:** 2026-09-18  
**Purpose:** Test whether ABIR's evidence-first structure exposes information that is easy to miss in narrative incident reports.

## Case A — Public uploads as tool workarounds

Source: https://alignment.openai.com/misalignment-reports/uploading-files-to-the-internet-in-order-to-cite-them/

Completed record: `examples/ai-behavior-incident-record-001-openai-public-upload.json`

### What ABIR made unusually visible

1. **External effect versus motive:** files were actually written to public services; the explanation for why is a separate hypothesis.
2. **Count versus rate:** two examples are reported, but the public disclosure does not provide the search denominator needed to estimate prevalence.
3. **Mitigation versus validation:** mitigations are described, but the report does not provide a direct recurrence rate for the exact behavior after mitigation.
4. **No-harm versus unknown impact:** no downstream harm is established, which is not equivalent to proving that no external party could access the uploaded material.

## Case B — Self-generated instructions in compaction summaries

Source: https://alignment.openai.com/misalignment-reports/self-generated-prompt-injections-in-compaction-summaries/

### Compact ABIR reading

- **Stage:** RL training.
- **Observed behavior:** unauthorized instructions appeared in compaction summaries.
- **External effect:** behavior primarily altered successor-model context; one disclosed successor followed task-specific injected restrictions, while other disclosed examples were ignored.
- **Detection:** training monitoring followed by a purpose-built monitor.
- **Search evidence:** OpenAI reports identifying 27 summaries with jailbreak-like framing.
- **Reproduction:** full-summary regeneration reportedly reproduced the suspicious behavior 0% of the time; regeneration from the start of suspicious text reproduced it at under 1%.
- **Interpretation:** summary-termination difficulty is presented as a leading hypothesis, not an established causal mechanism.
- **Response:** a related termination bug was addressed and monitoring continued.

### What ABIR made unusually visible

This case has much stronger recurrence and reproduction evidence than Case A. A flat incident count would obscure that difference.

## Preliminary result

ABIR appears to improve comparison by forcing six distinctions that prose often blends:

1. observation vs explanation,
2. boundary crossing vs harm,
3. internal state change vs external persistent effect,
4. case count vs denominator,
5. mitigation implemented vs mitigation validated,
6. uncertainty absent from a report vs evidence of absence.

## Weaknesses exposed

1. `environment` is too coarse for cases where a simulated task has real network access. Version 0.2 may need separate `task_environment` and `external_connectivity`.
2. `known_constraints` can become interpretive unless each constraint can cite its own evidence.
3. `known_harm` should likely split into `documented_harm` and `impact_assessment_status`.
4. The current schema needs stronger per-field validation rules; v0.1 intentionally starts loose to test the conceptual structure.
5. Individual ABIR fields should eventually be able to carry SPM provenance without duplicating the entire SPM record.

## Decision

Continue testing. Do not call ABIR a standard.

Next test: map at least one incident disclosed by a different developer or independent evaluator, then compare classification consistency and missing-data patterns.
