# Language Review Revision Report — 2026-07-14

Source: `main_language_reviewed.tex` → `main_language_reviewed_revised.tex`
Baseline commit: `73ad9b4`
Build: **success** — `latexmk -pdf main_language_reviewed_revised.tex` → exit 0, 49 pages, 0 errors, 0 undefined control sequences, 0 undefined citations, 0 undefined references, 0 duplicate labels. 5 overfull hboxes remain (pre-existing, F-08, deferred by author).

## Summary

- **Fixed: 80** — all 13 G, all 5 L, all 10 P, all 16 E, all 13 T, 7 N (N-02…N-08), all 9 A, 7 F (F-02a/b/c, F-03a/b/c, F-04, F-05, F-06a/b/c, F-07 — counted as 7 findings across 11 IDs).
- **Deferred by author: 5** — F-01, F-08, M-01, M-02, thesis title / RL scope.
- **Intentionally unchanged: 2** — N-01 ($d$ collision, author decision), F-09 (column alignment, see below).
- **Needs author decision: 0.**
- **New references added: 0.** No `.bib` file was touched. The one item that could have required a citation (N-07, epsilon-squared) was resolved with a definition instead, per author instruction.

All 89 review IDs are accounted for. Every one has exactly one status.

## Issue ledger

| Review ID(s) | Status | Location | Minimal change | Rationale |
|---|---|---|---|---|
| G-01 | Fixed | l.233 | `contain` → `contains` | Subject–verb agreement. |
| G-02 | Fixed | l.287 | `deeplearning` → `deep learning` | Malformed compound. |
| G-03 | Fixed | l.341 | dropped `and controlling complexity` | Broken parallelism; complexity control is already one of the three problems. |
| G-04 | Fixed | l.339 | `penalties however,` → `penalties, however,` | Parenthetical needs commas both sides. |
| G-05 | Fixed | l.169 | full stop → colon | Sentence fragment. |
| G-06 | Fixed | l.288 | `"strength"` → ` ``strength'' ` | ASCII quotes render wrong-facing in LaTeX. |
| G-07 | Fixed | l.337 | `without boundaries` → `without bound` | Correct idiom. |
| G-08 | Fixed | l.872 | `and it motivates a padding scheme of` → `which motivates the padding scheme described below` | Dangling *it*; ungrammatical *scheme of*. |
| G-09 | Fixed | l.1611 | `puts` → `applies` | *puts pressure* needs *on*. |
| G-10 | Fixed | l.1674 | `costs … tolerates` → `permits … does` | Misparses on first reading. |
| G-11 | Fixed | l.333 | `the new weights that have been added` → `the newly added weights` | Redundant relative clause. |
| G-12 | Fixed | l.324 | `instruments to drive` → `instruments that drive` | Wrong non-finite complement. |
| G-13 | Fixed | l.191 | added `the` | Missing article. |
| L-01 | Fixed | l.163 | `This` → `This shielding` | Antecedent was ambiguous. |
| L-02 | Fixed | l.939 | split into two sentences, appositives parenthesised | Comprehension failure. **Report's suggestion used a semicolon; replaced with a full stop** per the no-semicolon constraint. |
| L-03 | Fixed | l.1651 | colon → full stop, following clause capitalised | The colon promised an answer and delivered a question. Touches text just outside the wrapper (the capitalisation). |
| L-04 | Fixed | l.1127 | trailing `it` → `that advantage` | Ambiguous referent. |
| L-05 | Fixed | l.944 | rebalanced the comparison | Compared two different dimensions. |
| P-01 | Fixed | l.151 | `earned its keep` → `proved useful` | Idiom. |
| P-02 | Fixed | l.206 | `open territory and works through it` → `open question and addresses it` | Metaphor. |
| P-03 | Fixed | l.207 | `hold the work together` → `guide the work` | Metaphor. |
| P-04 | Fixed | l.1650 | `lever is pulled … move fitness` → `mechanism is exercised … change fitness` | Metaphor carrying an RQ conclusion. Claim and hedge preserved. |
| P-05 | Fixed | l.1606 | same metaphor removed | **Also required repairing l.1607**, where `that lever` was orphaned → `that mechanism`. |
| P-06 | Fixed | l.671 | `mathematical ``personalities''` → `mathematical roles` | Metaphor doing technical work. `specialised` left in its own adjacent E-05 wrapper. |
| P-07 | Fixed | l.1620 | `functional ``personalities''` → `functional roles` | Same metaphor recurring. |
| P-08 | Fixed | l.602 | `canonical tasks anchor` → `standard tasks are used in` | Ornamental. |
| P-09 | Fixed by combined edit | l.343 | merged into the preceding sentence | The report offered "delete **or** merge". Deleting would have destroyed the wrapper, and the claim (NEAT solves all three with *one* mechanism set) is substantive. Merging keeps both the claim and the ID. |
| P-10 | Fixed | l.366 | `organic emergence of topological structures` → `topological structure to emerge through mutation` | Ornamental. |
| E-01 … E-16 | Fixed (16) | see report | US `-ize/-ization` → UK `-ise/-isation` | All 16 verified as live prose. Zero live US spellings remain. |
| T-01 … T-11 | Fixed (11) | see report | *palette* / *library* → **activation set** | Three competing names for the set $\mathcal{A}$ normalised to one. Wording adjusted per site so no sentence repeats *set* awkwardly. |
| T-12 | Fixed | l.254 | `historical innovation numbers` → `historical markers` | Hybrid term appearing nowhere else. The optional Methodology bridging clause was **declined**: the Background already defines *innovation number* before the Methodology's first *historical marker*, so a third gloss would be redundant. |
| T-13 | Fixed by combined edit | l.238, 1136, 1198, 1211, 1233, 1407 | *best genome* → **champion** in prose | Plus a one-clause gloss at the first body use (l.238): "Every champion, the best genome of a run, …". **l.1054–1055 deliberately keep *best genome*** — they name MLflow-logged artefacts, as the report requires. |
| A-01 | Fixed | l.1107, 1393 | MJX expanded at first use, late re-expansion dropped | Was introduced backwards. |
| A-02 | Fixed | l.1428, 1412 | header spelled out; `(HL)` introduced at first prose use | **Caught by the final audit.** Expanding only the header removed the abbreviation's sole anchor while bare `HL` remained twice at l.1412, leaving it undefined document-wide. Both sites now resolved. |
| A-03 | Fixed | l.1239, 1440 | `two one-sided tests (TOST)` at first mention | Was introduced backwards. *Welch* qualifier carried forward to the definition so no detail is lost. |
| A-04 | Fixed | l.1233 | `interquartile range (IQR)` at first mention | IQR was used cold in Results. |
| A-05 | Fixed | l.482 | dropped `(SANN)` | Single live use, verified. |
| A-06 | Fixed | l.485 | dropped `(FS-NEAT)` | Single live use, verified. |
| A-07 | Fixed | l.485 | `FD-NEAT` → `Feature Deselective NEAT (FD-NEAT)` | Never expanded anywhere. Expansion **verified against the literature** (Papavasileiou et al.; the cited paper's own title names both FS-NEAT and FD-NEAT). Acronym retained — it is reused in *HA-FD-NEAT*. |
| A-08 | Fixed | l.678 | dropped `(MoW)` | Single live use, verified. |
| A-09 | Fixed | l.671 | dropped `(LLMs)`, lowercased | Single live use, verified. |
| N-01 | Intentionally unchanged | l.938 | none | **Author decision:** neither compatibility-distance $d$ nor Cohen's $d$ is renamed. Wrapper retained verbatim. |
| N-02 | Fixed | l.936, 938 | $H$ → $\mathcal{H}$ | Collided with the Kruskal–Wallis $H$. Matches the existing $\mathcal{A}$/$\mathcal{I}_j$ style. |
| N-03 | Fixed | l.936, 938, 940 | $\delta_i$ → $\Delta_i$ | Collided with Cliff's $\delta$. Author-confirmed rename. |
| N-04 | Fixed | l.1029–1034 | **split into two equations** | The genuine mathematical error. See below. |
| N-05 | Fixed | l.892 | `Walker` → `Walker2D`; dropped `_{1:6}` | Subscript inconsistent; the slice was a no-op on a 6-D output and contradicted the prose ("directly without modification"). |
| N-06 | Fixed | l.1394, 1536 | subscripts capitalised, `\mathrm{fit}` → `\text{fit}` | Unified on the definition site (l.996). **No layout change** — F-08 untouched. |
| N-07 | Fixed | l.1239 | defined $\varepsilon^2$ at the Evaluation Protocol | Was used undefined. **No citation added** (author instruction). See below. |
| N-08 | Fixed | l.233 | `($\tanh$, $\sigma$)` → `($\tanh$ and the sigmoid $\sigma$)` | $\sigma$ was used bare before definition, with a standard-deviation reading hazard. |
| F-01 | Deferred by author | l.350–363 | none | Missing asset. Author action required. |
| F-02a/b/c | Fixed (3) | l.1501, 1522, 1582 | added group-level `\label` | Composite floats were unreferenceable. Used `fig:main-activation-usage` for the third to avoid a near-collision with the existing `sec:main-activation`. |
| F-03a/b/c | Fixed (3, + 1 untagged) | l.1453, 1523, 1583, **1550** | `\FloatBarrier` moved to after `\end{figure}` | Executed inside a float it is a no-op. **Moved, not dropped** — all four sit at end-of-subsection in Results, so the barrier is doing legitimate work. The untagged 4th call was fixed for consistency; **no new ID was minted.** |
| F-04 | Fixed | l.989, 1105, 1396, 1413, 1642 | rule: **no separator below 10,000** | Five sites normalised. Math-mode numbers stay bare. Nothing needed a separator *added* — the only two values ≥ 10,000 already had one. The F-04 wrapper site itself (l.1203) was already compliant and is untouched. |
| F-05 | Fixed | l.473 | self-contained sentence-case caption + period | The only caption with no terminal full stop. **Deliberately does not use `$\mathcal{A}$`** — the symbol is not defined until the Methodology, so referencing it in a Literature Review caption would defeat the self-containment this fix exists to achieve. |
| F-06a/b/c | Fixed (3) | l.1095, 1149, 1248 | Title-Case noun phrases → descriptive sentence-case captions | Two caption styles coexisted. |
| F-07 | Fixed | l.1157, 1159, 1160, 1179 | in-cell units | **Fitness target disambiguated as raw, unnormalised** — the real ambiguity. Chose in-cell over a Unit column: adding a column would force a table re-flow, which is deferred layout work. Cannot widen the table (the activation-set row already sets that column's width). |
| F-08 | Deferred by author | 5 sites | none | Overfull hboxes. Pre-existing (5 before, 5 after). |
| F-09 | Intentionally unchanged | l.1097, 1151 | none | **Considered rejection.** The finding is real but the remedy would harm these two tables: their value columns hold text (`[-1, 1] (continuous)`, `Brax v0.14.1 (MJX)`, `Enabled (via OriginConn)`), not numbers. Right-aligning would ragged-left a text column to line up two integers. `siunitx` is ruled out (new dependency, and it would fail on non-numeric cells). Report-only finding — no wrapper exists, none invented. |
| M-01, M-02 | Deferred by author | — | none | Author decision. |

## Significant changes

**The node-activation equations (N-04).** This was the one genuine mathematical error. The prose called $z_j$ a *pre-activation*, but the equation defined $z_j = \phi_j(b_j + \sum w_{ij} v_i)$ — with the activation applied — making $z_j$ a post-activation output. The sentence therefore described a quantity the equation never defined. Worse, the recursion never closed: $v_i$ was glossed as "the output values of source nodes", but no equation ever produced a $v$.

Split into two equations:

    z_j = b_j + Σ_{i ∈ I_j} w_ij · v_i,    v_j = φ_j(z_j)

$z_j$ is now genuinely the pre-activation, which is what the prose asserts and what makes *sum aggregation* the actual subject of the sentence. $v_j = \phi_j(z_j)$ closes the recursion, so the $v_i$ in the sum are well-defined by the same relation applied at the source nodes (evaluation proceeds in topological order, established elsewhere in the thesis). The gloss was extended to define both $z_j$ and $v_j$, which the previous gloss omitted entirely.

**Notation renames (N-02, N-03).** $H \to \mathcal{H}$ for the homologous-pair set, and $\delta_i \to \Delta_i$ for the attribute distance. Both collided with statistics used later (the Kruskal–Wallis $H$ and Cliff's $\delta$). Verified that no Kruskal–Wallis $H$ and no Cliff's $\delta$ was renamed by mistake, and that the commented-out twin of the equation was left alone. Per the author's decision, $d$ and $c_d$ are unchanged, so that equation now reuses one statistical letter rather than three.

**The definition of $\varepsilon^2$ (N-07).** Epsilon-squared was used twice in Results and never defined. It is now introduced at the Evaluation Protocol as the Kruskal–Wallis effect size, $\varepsilon^2 = (H - k + 1)/(n - k)$, with $k$ the number of conditions and $n$ the total runs. The formula reproduces both values the thesis reports: at $H = 7.45$, $k = 3$, $n = 90$ it gives $0.0626 \approx 0.063$ (matching the reported figure exactly), and at $H = 1.48$ it gives a slightly negative value, consistent with the thesis's "$\varepsilon^2 \approx 0$". No interpretation scale (small/medium/large) is asserted, because epsilon-squared has no single canonical threshold set and claiming one without a citation would be unsupported. **No reference was added.**

**Terminology normalisation.** The set $\mathcal{A}$ had three names — *palette* (6×), *library* (5×), *set* (2×). All eleven now read **activation set**. Separately, *best genome* → **champion** in prose, with a one-clause gloss at the first body use so the term is defined before it is relied on. The MLflow-logged-artefact uses correctly retain *best genome*.

**Figure and table changes.** Three composite figures gained group-level labels (they were previously unreferenceable). Four `\FloatBarrier` calls moved outside their floats, where they actually do something. The hyperparameter table's fitness target is now marked *raw, unnormalised* — a real ambiguity, since the normalised-minimum objective is bounded near 1.0 and the value is 10,000.

**Regression caught by the final audit (A-02).** Expanding the Table 5 header to "Hodges--Lehmann shift" removed the abbreviation's only anchor while bare `HL` still appeared twice in the prose, leaving it undefined document-wide — a net regression over the original state. Fixed by introducing `(HL)` at its first prose use.

## Deferred by author

- **F-01** — missing `Figures/genotype_phenotype.png`; the TikZ placeholder box remains untouched.
- **F-08** — overfull hboxes / margin overflow. 5 before, 5 after. No `\small`, `\resizebox`, manual break, or spacing change was made anywhere, and no fix was motivated by layout.
- **M-01** — no List of Figures / List of Tables added.
- **M-02** — no declaration of independent work / statement of authorship added.
- **Thesis title**, including the reinforcement-learning scope mismatch. The one live body reference to RL (MuJoCo's role in the RL literature) is contextual and correct, and was left unchanged.
- **Author-supplied thesis metadata** — programme, university, department, supervisor, co-supervisor, PDF metadata.

## Verification

- **Wrapper/ID integrity:** PASS. 89 wrappers, each ID exactly once. `diff` of the sorted wrapper-token sets against the baseline is empty — identical wrapper type and ID for all 89. No renumbering, deletion, duplication, or invented IDs. Report-only findings (F-08, F-09) remain report-only.
- **Source files left unchanged:** PASS. SHA-256 of `main_language_reviewed.tex`, `main_revised.tex`, and `main.tex` are byte-identical to their pre-task values. `master_thesis.bib` untouched (no `.bib` file was modified, per author instruction).
- **No new semicolons:** PASS. Semicolon count unchanged (40 → 40). No added line in the diff introduces one. The report's semicolon-bearing suggestion for L-02 was reworked into a two-sentence split.
- **Build result:** PASS. `latexmk -pdf main_language_reviewed_revised.tex` → exit 0, `main_language_reviewed_revised.pdf` produced, 49 pages, 0 errors, 0 undefined control sequences, 0 undefined citations, 0 undefined references, 0 duplicate labels. 5 overfull hboxes (pre-existing, deferred).
- **`git diff --check`:** PASS.
- **Git status:** baseline commit `73ad9b4` contains only the copied baseline file. All substantive edits are **unstaged and uncommitted**. Inspect with `git diff -- thesis/main_language_reviewed_revised.tex`.
