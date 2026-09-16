# SPM 0.2 Trial 01 — same 20 claims

**Date:** 2026-09-16  
**Purpose:** A/B-style comparison against SPM 0.1 Trial 01 using the exact same claim wording.

## Method

The 20 claims from `tests/spm-001-trial-01.md` were re-marked without changing their wording. Ambiguity means the schema still forces a materially debatable classification or omits provenance information necessary to interpret the mark. Effort remains relative (`low`, `medium`, `high`); no stopwatch timing is invented.

Fresh context check: the provenance problem remains active. NISO Plus Global/Online begins today (September 16, 2026) and explicitly includes tracking provenance, attribution, and usage in AI systems. NISO's June workshop report describes a minimum provenance payload as a first step for AI-mediated scholarly content. A May 2026 audit of four generative search engines used 712 real-world queries and reported evidence of AI-generated sources in roughly 16% of cited sources.

## Result

- SPM 0.1 material ambiguity: **9/20**.
- SPM 0.2 material ambiguity: **3/20**.
- Reduction: **6 cases / 66.7%**.
- SPM 0.2 marking overhead: **8 low, 10 medium, 2 high** versus 0.1's **11 low, 7 medium, 2 high**.
- Audit usefulness improved most for inference and multi-source claims.
- The redesign therefore passes the internal ambiguity target but increases routine marking overhead modestly.

## Case comparison

| # | 0.2 classification summary | Ambiguity | Effort | What changed |
|---|---|---|---|---|
| 1 | quote + no inference; S1 primary/content-checked | low | low | Source checking no longer implies claim validation. |
| 2 | paraphrase + no inference; S1 primary/content-checked | low | low | Clean. Source AI status can remain unknown independently of claim AI role. |
| 3 | paraphrase + inference; S1 primary/content-checked; claim unvalidated | low | medium | Major 0.1 failure fixed: source support and inferential validation are separate. |
| 4 | quote + no inference; S1 primary/content-checked | low | low | Still little added value over an ordinary citation; this is a legitimate low-value use case. |
| 5 | paraphrase + no inference; S1 primary/content-checked | low | low | Clean. |
| 6 | paraphrase + no inference; S1 primary/content-checked | low | low | Clean. |
| 7 | synthesis + inference; multiple source records; claim unvalidated | **medium** | high | Structure is representable, but whether pages reporting a workshop are primary or secondary remains claim-relative and genuinely contestable. |
| 8 | synthesis + inference; separate Openwrought/NISO records; claim unvalidated | low | high | 0.1's forced synthesis-vs-inference choice is fixed. |
| 9 | paraphrase + no inference; S1 primary/content-checked | low | low | Clean. |
| 10 | paraphrase + no inference; S1 primary/content-checked; source AI unknown | low | medium | Claim AI production and AI status of sources studied by the paper no longer collide. |
| 11 | paraphrase + inference; S1 primary/content-checked; claim unvalidated | low | medium | `content-checked` cannot be mistaken for validation of the broader conclusion. |
| 12 | paraphrase + inference; S1 primary/content-checked; claim unvalidated | low | medium | Same fix as #11. |
| 13 | observation + no inference; two repository records; claim tested; validation method recorded | **medium** | medium | `tested` is now auditable, but observation vs synthesis remains debatable because the operator inspected two artifacts. |
| 14 | paraphrase + no inference; S1 primary/content-checked | low | low | Clean. |
| 15 | paraphrase + no inference; S1 primary/content-checked | low | low | Clean. |
| 16 | synthesis + no inference; LOC + ISO/IIPC source records; corroborated | low | medium | Source-to-class pairing fixes 0.1 ambiguity. |
| 17 | paraphrase + no inference; S1 primary/content-checked | low | low | Clean. |
| 18 | paraphrase + no inference; archive-operator source primary/content-checked; claim unvalidated | low | medium | Clearly distinguishes 'operator reports completion' from independent validation of completeness. |
| 19 | paraphrase + no inference; Reddit report primary relative to report/content-checked; claim unvalidated | **medium** | medium | Source class still depends strongly on exact claim framing. This is intrinsic, but compact notation may not communicate the relativity clearly enough. |
| 20 | paraphrase + inference; Reddit report primary relative to report/content-checked; generalized claim unvalidated | low | medium | The dangerous 0.1 `located` signal is gone; the generalized technical claim is visibly unvalidated. |

## Remaining failures

### 1. Source class remains claim-relative

SPM 0.2 correctly pairs class with each source, but `primary` can still be misunderstood as an intrinsic property. A Reddit post is primary evidence that a user reported an experience and weak evidence for a general technical rule.

**Candidate 0.3 change:** rename `class` to `evidence_role` or require a short `role_for_claim` note when class is likely to be misunderstood.

### 2. Observation versus synthesis

A claim produced by directly inspecting two artifacts can reasonably be called an observation of both or a synthesis across both. Transformation categories still overlap at this boundary.

**Candidate change:** define `observation` as a source type / evidence acquisition method rather than a transformation, or permit `transformation` arrays. Do not change this until independent raters show the ambiguity is recurrent.

### 3. Compactness cost

0.2 is semantically cleaner but longer. Source-level records add useful information at the cost of friction. This may be acceptable for research notes and datasets but excessive for ordinary prose.

**Candidate solution:** two display modes using one underlying record: a compact badge for reading and an expanded record for audit.

## Decision

**SPM 0.2 passes the internal redesign test but remains experimental.** Ambiguity fell from 9/20 to 3/20 without a high-overhead increase, but the single-operator test cannot establish whether other people interpret the categories consistently.

The next meaningful experiment is no longer another self-edit. It is an independent classification test. Give another rater the definitions and the same 20 claims without Openwrought's classifications, then measure agreement field by field.

## Sources used for current-context verification

- NISO, June 2026 provenance workshop report: https://www.niso.org/niso-io/2026/06/workshops-highlight-standards-needed-for-AI-ecosystem
- NISO Plus Global/Online 2026 program context: https://www.niso.org/niso-io/2026/06/now-available-preliminary-program-niso-plus-2026-globalonline
- Allaham & Diakopoulos, *Synthetic Sources?*: https://arxiv.org/abs/2605.23684
