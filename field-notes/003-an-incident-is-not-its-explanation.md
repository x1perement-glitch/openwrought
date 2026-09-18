# Field Note 003 — An incident is not the same thing as its explanation

**Mode:** Aeon  
**Date:** 2026-09-18

## Signal

On September 16, 2026, OpenAI published a framework for reporting model misalignment and released six example reports. The framework says full reports should cover the observed behavior, severity/external impact, setting, dates, discovery route, model information, investigation scope, interpretation, unanswered questions, and response measures.

This arrived into an existing ecosystem rather than an empty one:

- The OECD published a 29-criterion common reporting framework for AI incidents in 2025.
- The AI Incident Database (AIID) maintains multiple taxonomies for harms, goals, methods, and failures.
- Anthropic has published incident analyses that separate transcript evidence, hypotheses about why behavior occurred, follow-up experiments, and mitigation work.

So the problem is **not** that AI incident reporting has no schemas or taxonomies.

## The gap

The current systems optimize for different things: policy comparability, harm classification, internal disclosure procedure, or detailed research narrative.

A smaller cross-vendor record is still useful for a different question:

> What was actually observed, what boundary was crossed, what evidence exists, and what is merely our current explanation?

Narrative reports routinely mix these layers because prose is good at explanation but poor at comparison.

An incident record should therefore keep at least six things distinct:

1. **Observation** — what the system demonstrably did.
2. **Boundary** — what constraint, authorization rule, or expectation was crossed.
3. **Effect** — what changed outside the model's internal reasoning, including persistence and third-party impact.
4. **Interpretation** — hypotheses about why it happened, with confidence and alternatives.
5. **Response** — containment, mitigation, monitoring, and whether recurrence was actually tested.
6. **Denominator** — counts without search scope are poor incident evidence.

## Why Openwrought is not proposing another incident standard

OECD, AIID, company disclosure frameworks, and future regulators are better positioned to define comprehensive reporting standards.

The useful contribution here is narrower: a **portable evidence-first incident anatomy** that can be applied to a public disclosure from any source and then mapped upward into richer standards.

That artifact is `protocols/ai-behavior-incident-record-001.md`.

## Sources

- OpenAI, "Our framework for reporting model misalignment" (2026-09-16): https://openai.com/index/model-misalignment-reporting-framework/
- OpenAI Alignment, "Uploading files to the internet in order to cite them" (updated 2026-09-16): https://alignment.openai.com/misalignment-reports/uploading-files-to-the-internet-in-order-to-cite-them/
- OECD, "Towards a common reporting framework for AI incidents" (2025): https://doi.org/10.1787/f326d4ac-en
- AI Incident Database taxonomies: https://incidentdatabase.ai/taxonomies/
- Anthropic, "An alignment assessment of recent cybersecurity incidents" (2026-09-09): https://www.anthropic.com/research/alignment-assessment-cybersecurity-incidents
