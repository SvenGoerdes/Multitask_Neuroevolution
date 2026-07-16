# Thesis Review Report — 2026-07-13
Reviewed: main.tex (+ included files) → main_reviewed.tex
Totals: W: 4 | C: 3 | U: 3 | S: 15

## Red — Incorrect (W)
| ID | Location | Flagged text (first ~8 words) | Problem | Suggested direction |
|----|----------|-------------------------------|---------|---------------------|
| W-01 | §2.1, ¶2 | "We solely rely on adapting the weights of..." | Contradicts §2.2; the thesis uses neuroevolution to optimize structure, not backpropagation | Rephrase to refer to standard deep learning instead of "we" |
| W-02 | §4.2, ¶1 | "This condition uses \texttt{DefaultConn} without historical..." | Contradicts §3.3.2; standard NEAT requires historical markers for crossover alignment | Clarify if default connections use implicit structural keys or define historical markers consistently |
| W-03 | §5.2, ¶3 | "Two one-sided tests (Welch TOST) sharpen this..." | Methodological contradiction: using a parametric test (Welch TOST) despite explicitly stating that parametric tests are inappropriate | Use non-parametric equivalence tests (e.g. bootstrap-based) or qualify the test |
| W-04 | §5.4, ¶2 | "The per-genome imbalance $|r_{\text{hopper}} - r_{\text{walker2d}}|$..." | Mathematical error: the formula uses raw returns $r$ instead of normalised scores $\hat{r}$ or $\bar{r}$, though reported values are normalised differences | Change variables in the formula to represent normalised returns |

## Orange — Unsupported (C)
| ID | Location | Flagged text (first ~8 words) | Problem | Suggested direction |
|----|----------|-------------------------------|---------|---------------------|
| C-01 | §1, ¶6 | "Within neuroevolution, even the basic step of passing..." | Unsupported claim: a strong statement about the rarity of multi-task observation padding in neuroevolution is made without citation | Provide a reference or soften the claim |
| C-02 | §3.3.2, ¶2 | "where $D$ denotes the count of non-homologous..." | Scaling issue: dividing the weight difference sum by $\max(n_1, n_2)$ discounts weight similarity as genomes grow, unlike standard NEAT | Check if TensorNEAT indeed implements distance this way and explain the divergence |
| C-03 | §4.3, ¶4 | "One NEAT run (seed 5213) was aborted..." | Lack of support/explanation: no reason is provided for aborting and excluding this seed's run | Add a brief note explaining the abort condition (e.g., hardware/run failure) |

## Blue — Unclear (U)
| ID | Location | Flagged text (first ~8 words) | Problem | Suggested direction |
|----|----------|-------------------------------|---------|---------------------|
| U-01 | §3.2, ¶3 | "Formally, given a network $f: \mathbb{R}^{17} \rightarrow \mathbb{R}^{6}$..." | Notation inconsistency: Equations 1 & 2 use 1-based indexing ($_{1:3}$, $_{1:6}$), while Figure 4 caption uses 0-based indexing (inputs 11-16, outputs 3-5) | Standardize indexing across the text and figures to be consistently 0-based or 1-based |
| U-02 | §4.3, ¶1 | "available at [repository URL]." | Placeholder: the repository link is left as bracketed draft text | Replace the placeholder with the actual repository URL or remove the sentence |
| U-03 | §5.5, ¶2 | "Among the 55 hidden nodes, relu accounted..." | Case/style inconsistency: activation names are written in lowercase plain text ("relu", "sigmoid", etc.) unlike formatting in §3.5 | Format activation function names consistently with the math-mode and capitalized styles used in §3.5 |

## Violet — Style (S)
| ID | Location | Flagged text (first ~8 words) | Problem | Suggested direction |
|----|----------|-------------------------------|---------|---------------------|
| S-01 | §1, ¶2 | "adds a node or a connection only when..." | Run-on sentence: connects two independent clauses with "and" twice | Split into two sentences or improve punctuation |
| S-02 | §1, ¶3 | "What happens around that activation gene matters as..." | Informal register: "matters as much as" is slightly too colloquial | Rephrase to "is as critical as" or similar formal academic phrasing |
| S-03 | §1, ¶4 | "We test this on two locomotion benchmarks. Hopper..." | Typo/punctuation: period instead of a colon or comma separating the list | Change the period to a colon |
| S-04 | §1, ¶7 | "Fitness aggregation, a strategy of combing two..." | Spelling typo: "combing" instead of "combining" | Correct spelling to "combining" |
| S-05 | §1, ¶7 | "A common approach is to use NSGA II..." | Missing punctuation: missing comma after "NSGA II" separating the appositive clause | Add a comma after "NSGA II" |
| S-06 | §1, ¶7 | "In contrast we compared three such aggregators..." | Missing punctuation: missing comma after the introductory transition "In contrast" | Add a comma after "In contrast" |
| S-07 | §1, ¶8 | "The contribution is empirical. We propose no new..." | Choppy sentences: three short, consecutive sentences in the contributions section | Combine into a single, cohesive sentence |
| S-08 | §1, ¶9 | "with each hidden node drawing its activation from..." | Typo: double periods at the end of the sentence ("functions..") | Remove the duplicate period |
| S-09 | §1, ¶9 | "We fixed the set of functions in advance... It spans..." | Ambiguous pronoun: "It" has an unclear antecedent (set or composition) | Clarify by replacing "It" with "This palette" or "The library" |
| S-10 | §2.1, ¶1 | "Cells are constantly rewiring and find new pathways..." | Redundancy: repetitive sentences re-stating brain rewiring and connections within the same paragraph | Consolidate paragraph to eliminate repetitive descriptions |
| S-11 | §2.1, ¶2 | "...keeps its wiring, but the \"strength\" of..." | Formatting: standard double quotes `"` are used instead of LaTeX directional quotes | Replace with double backticks and single quotes (``strength'') |
| S-12 | §2.1, ¶3 | "This variety is functionally useful." | Simple register: too simple/abrupt compared to the rest of the academic text | Rephrase to "This physiological diversity serves concrete functional roles." |
| S-13 | §2.2, ¶1 | "TWEANNs) (\cite{stanley_evolving_2002})." | Inconsistent citation formatting: manual parenthetical wrapping of `\cite` is mixed with `\parencite` elsewhere | Standardize on using `\parencite` directly |
| S-14 | §2.2, ¶5 | "Earlier TWEANN methods addressed these three problems..." | Awkward grammar: coordination of verb and participle ("addressed... and controlling") | Rephrase to "...addressed these three problems and the challenge of controlling..." |
| S-15 | §3.2, ¶1 | "This design was chosen over modular sub-networks to..." | Informal phrasing: "keep the transfer learning argument clean" is colloquial | Rephrase to "ensure a clear comparison of transfer performance" |

## Cross-cutting observations
- **Parenthesis Citations Inconsistency**: The document has a mix of manual parenthetical wrappers like `(\cite{...})` and the proper `\parencite` or `\textcite` commands. Manually wrapping `\cite` is prone to parenthetical duplication or formatting style violations under APA guidelines.
- **0-based vs 1-based Indexing Inconsistency**: The text references inputs 11--16 and outputs 3--5 (0-based indexing) in Figure 4's description, but uses 1-based indexing in Equations 1 & 2, which could confuse readers.
