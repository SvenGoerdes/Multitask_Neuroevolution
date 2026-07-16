# Thesis Coherence Review — 2026-07-13
Reviewed: main.tex (+ included files) → main_coherence_reviewed.tex
Totals: R: 3 | F: 3 | K: 3 | T: 2

## Teal — Repetition (R)
| ID | Location(s) | Flagged text (first ~8 words) | Problem | Suggested direction |
|----|-------------|-------------------------------|---------|---------------------|
| R-01a | §1, ¶8; §3.1, ¶3 | "Hopper is a single planar leg, and each..." | Repeats the physical/kinematic segment layout overlap explanation between Introduction and Problem Formulation | Consolidate the explanation or make the later section a brief cross-reference |
| R-02a | §2.1, ¶3; §2.4, ¶5 | "Two neurons can receive the same input..." | Repeats the concept of biological response diversity and its representation in ANNs across two background subsections | Consolidate biological variety under §2.4 (Activation Functions) and remove it from §2.1 |
| R-03a | §3.2, ¶4; §3.3.2, ¶2 | "At the implementation level, nodes are stored as..." | Duplicates node/connection gene field details between Genome Representation and NEAT Foundation | Remove structural definitions from §3.3.2 and cross-reference §3.2 |

## Purple — Argument Flow (F)
| ID | Location | Flagged text (first ~8 words) | Problem | Suggested direction |
|----|----------|-------------------------------|---------|---------------------|
| F-01 | §1, ¶7 | "In contrast we compared three such aggregators..." | Interpretation details of the three fitness functions are introduced prematurely under the literature gap | Move the detailed comparison to the Contributions or Methodology sections |
| F-02 | §2.1, ¶3 | "Biological neurons also differ in their built-in..." | Placed under "Structural Differences" (static vs dynamic wiring), disrupting flow with functional response variety | Move functional response properties to §2.4 (Activation Functions) |
| F-03 | §2.3, ¶3 | "and no hand-tuned complexity penalty is required..." | Abrupt section transition; removing original bridge text makes the shift to Activation Functions disjointed | Restore a brief transition sentence explaining that NEAT keeps activations fixed |

## Blue — Internal Consistency (K)
| ID | Location(s) | Flagged text (first ~8 words) | Problem | Suggested direction |
|----|-------------|-------------------------------|---------|---------------------|
| K-01a | §3.4, ¶5; §5.2, ¶2 | "Formally, writing $r_{\text{Hopper}}$ and..." | Inconsistent variable cases ($r_{\text{Hopper}}$ / $r_{\text{hopper}}$) and function names ($\text{fit}$ / $\mathrm{fit}$) between Chapters 3 and 5 | Standardize math notation and variable casing across all sections |
| K-02 | §5.3, ¶4 | "the ablation and HA-NEAT settled on more..." | Inconsistency: claiming HA-NEAT was more compact than NEAT despite noting the contrast is not statistically significant ($p = 0.10$) | Qualify the claim to specify that only the ablation was statistically different |
| K-03 | §5.6, ¶4 | "(Section~\ref{subsec:research-gap-and-contribution})" | Cross-reference error: points to Section 2.9 (Research Gap) instead of Section 2.8 where the personalities hypothesis is introduced | Update cross-reference to point to Section 2.8 |

## Amber — Structure (T)
| ID | Location | Flagged text (first ~8 words) | Problem | Suggested direction |
|----|----------|-------------------------------|---------|---------------------|
| T-01 | §4.4 | "Two preliminary experiments calibrated the design of..." | Empirical results and figures (interpretations of calibrations) live in Experimental Settings rather than Results | Move the interpretation and results of the calibration experiments to Chapter 5 |
| T-02 | §6 | "\section{Conclusion and Future Work}" | Empty section: Chapter 6 contains no text, leaving research questions and findings without a final summary | Author needs to write the conclusion text |

## Cross-cutting observations
- **Ineffective Background Transitions**: Key concepts (e.g. biological variety) are split across dynamic topology and activation function subsections, creating redundant structural repeats and abrupt transitions.
- **Results Placed in Methodology/Settings**: Calibration results are interpreted in Chapter 4, which duplicates Chapter 5's role and introduces experimental outputs prior to the main results.
- **Logical/Statistical Inconsistencies**: The text draws definitive conclusions (e.g. HA-NEAT compactness, personalities hypothesis references) that are not supported by the stated non-significant statistical results.
