# Language and Consistency Review — 2026-07-14

Reviewed: `main_revised.tex` → `main_language_reviewed.tex`
Build: **success** — `latexmk -pdf main_language_reviewed.tex` → exit 0, 48 pages, 0 errors, 0 undefined control sequences, 0 undefined citations, 0 undefined references, 0 duplicate labels.
Source integrity: SHA-256 of `main_revised.tex` **unchanged** (`2d73c8fc…fa71b1` before and after).
All 89 issue IDs are present in the `.tex` **and visible in the compiled PDF**.

## Summary

Totals by category: **G: 13 | L: 5 | P: 10 | E: 16 | T: 13 | N: 8 | A: 9 | F: 10 | M: 2**  (89 IDs)

The three most important findings:

1. **`Figures/genotype_phenotype.png` does not exist** (`F-01`, BLOCKER). Section 2.3 references `Figure~\ref{fig:genotype-phenotype}` in live prose, but the float contains a dashed TikZ placeholder box. Your thesis currently renders an empty dashed rectangle in the Literature Review. Only you can supply this asset.
2. **The node-activation equation contradicts its own prose** (`N-04`). Line 1001 says "the **pre-activation** value of a node is computed as the sum of incoming weighted signals plus a bias term", but the formula defines $z_j = \phi_j(b_j + \sum w_{ij} v_i)$ — with the activation *applied*. As written, $z_j$ is a post-activation output, so the sentence describes a quantity the equation never defines, and the recursion never closes ($v_i$ is "the output of source nodes", but nothing states $v_j = \phi_j(\cdot)$). This is the one finding that is a genuine mathematical error rather than a style or consistency issue.
3. **The activation set $\mathcal{A}$ has three competing names** (`T-01`–`T-11`): *palette* (6×), *library* (5×), *set* (2×). Eleven occurrences need normalising to the preferred term **activation set**.

Two further items you should know about, both discovered during verification rather than by the review sweep:

- **The thesis title claims reinforcement learning** (see *RL scope audit*). It is the single largest scope mismatch in the document, but your brief explicitly excluded the title, so it is **reported only, not annotated**.
- **Your source thesis already has 5 overfull hboxes** (`F-08`) — text running past the right margin — including the fitness formula at line 1366. This pre-exists my annotation and is not caused by it.

---

## G — Grammar, spelling, punctuation (Red)

| ID | § / line | Flagged text | Problem | Suggested direction |
|---|---|---|---|---|
| G-01 | §1 l.205 | "The set contain several distinct…" | Subject–verb agreement; singular *set* takes *contains*. | "The set **contains** several distinct function shapes" |
| G-05 | §1 l.141 | "We test this on two locomotion benchmarks. Hopper and Walker2D, …" | Sentence fragment: the second "sentence" has no verb. | Replace the full stop with a colon. |
| G-08 | §3.1 l.844 | "and it motivates a padding scheme of the neural network" | Dangling *it*; "padding scheme **of** the network" is ungrammatical. | "…, which motivates the padding scheme described below" |
| G-03 | §2.2 l.314 | "addressed these three problems and controlling complexity only in part" | Broken parallelism: a noun phrase coordinated with a gerund. *Three problems* already includes complexity control. | "addressed these three problems only in part" |
| G-02 | §2.1 l.259 | "In deeplearning we rely on" | Malformed compound. | "In **deep learning** we rely on" |
| G-06 | §2.1 l.260 | `the "strength" of each connection` | Straight ASCII quotes — LaTeX renders these as wrong-facing quotes. This is the only live instance in the document; everywhere else uses `` ``…'' ``. | ``` the ``strength'' of each connection ``` |
| G-04 | §2.2 l.311 | "Such penalties however, are hard to tune" | Misplaced comma; parenthetical *however* needs commas on both sides. | "Such penalties, however, are hard to tune" |
| G-07 | §2.2 l.309 | "can grow without boundaries" | Wrong noun: the idiom is *without bound*. | "can grow without bound" |
| G-12 | §2.2 l.296 | "the three instruments to drive the population" | Wrong non-finite complement. | "the three instruments **that drive** the population" |
| G-11 | §2.2 l.305 | "the new weights that have been added have not yet been…" | Redundant relative clause duplicating *added*. | "because the **newly added** weights have not yet been optimised" |
| G-13 | §1 l.163 | "However, available literature does not answer it." | Missing article. | "However, **the** available literature…" |
| G-09 | §5.6 l.1577 | "That regime puts far less genuine multi-task pressure" | *puts pressure* is incomplete without *on*; the verb has no object. | "That regime **applies** far less genuine multi-task pressure" |
| G-10 | §6 l.1640 | "It costs more between-task imbalance than the minimum tolerates" | Not idiomatic; misparses on first reading. | "It **permits** more between-task imbalance than the minimum **does**" |

## L — Clarity (Orange)

Reported only where comprehension genuinely breaks on first reading. Deliberate style — sentence-length variation, active voice, *we/our*, calibrated hedging — was **not** touched.

| ID | § / line | Flagged text | Problem | Suggested wording |
|---|---|---|---|---|
| N-04 ↔ L | see N-04 | *(cross-listed — the clearest comprehension failure is the maths)* | | |
| L-02 | §3.3.2 l.911 | "The distance is computed separately over node genes, aligned by node index, and over connection genes, aligned by…, and the two values are summed." | Two appositive insertions plus a trailing coordination; the reader must reread to see *what* is summed. | "The distance is computed separately for node genes (aligned by node index) and for connection genes (aligned by their identifying attributes); the two values are then summed." |
| L-03 | §6 l.1617 | "The follow-up question receives the more informative answer:" | The colon promises an answer and delivers a *question*. The sentence reads backwards. | End the sentence with a full stop, then pose the question separately. |
| L-01 | §1 l.135 | "This is the mechanism's intended behaviour" | *This* has no clear antecedent — the shielding, the placement, or the whole mechanism? | "**This shielding** is the mechanism's intended behaviour" |
| L-04 | §4.2 l.1099 | "…or whether the surrounding speciation machinery already produces it" | Trailing *it* is ambiguous between *an advantage* and *heterogeneity*. | "…already produces **that advantage**" |
| L-05 | §3.3.2 l.916 | "Attribute differences therefore contribute less to the distance in large genomes than under the original definition." | Unbalanced comparison: *in large genomes* vs *under the original definition* compares two different dimensions. | "Under this definition, attribute differences contribute less to the distance in large genomes than they do under the original one." |

## P — Plain academic language (Green)

| ID | § / line | Flagged text | Problem | Suggested direction |
|---|---|---|---|---|
| P-01 | §1 l.123 | "the structure that has not **earned its keep**" | Idiom (explicitly named in the brief). | "…that has not proved useful" |
| P-04 | §6 l.1616 | "**The lever is pulled**, and pulling it does not move fitness on this task." | Metaphor carrying the concluding claim of an RQ answer. | "The mechanism is exercised, and exercising it does not change fitness on this task." |
| P-05 | §5.6 l.1572 | "the **lever** HA-NEAT provides **is pulled**" | Same metaphor, second occurrence. | "the mechanism HA-NEAT provides is exercised" |
| P-06 | §2.7 l.644 | "mathematical ``**personalities**''" | Metaphor doing technical work; *roles* is precise and preserves the meaning. | "specialised mathematical **roles**" |
| P-07 | §5.6 l.1586 | "functional ``**personalities**''" | Same metaphor recurring in the Discussion. | "functional **roles**" |
| P-02 | §1 l.178 | "This thesis takes that as the **open territory** and works through it." | Metaphor; inflated framing. | "This thesis takes that as the open question and addresses it." |
| P-03 | §1 l.179 | "Two research questions **hold the work together**." | Metaphor where a plain verb exists. | "Two research questions guide the work." |
| P-08 | §2.6 l.574 | "Two of its **canonical** tasks **anchor** this thesis." | *canonical* here just means *standard*; *anchor* is ornamental. | "Two of its standard tasks are used in this thesis." |
| P-10 | §2.3 l.338 | "It allows for the **organic emergence** of topological structures" | Ornamental; the mechanism is simply mutation-driven growth. | "It allows topological structure to emerge through mutation" |
| P-09 | §2.2 l.316 | "It does so with a single coherent set of mechanisms." | Filler; adds nothing beyond the *three mechanisms* named in the next sentence. | Delete, or merge into the preceding sentence. |

**Deliberately kept:** *parsimonious* (l.368) and *parsimony* are used in the genuine model-selection sense (structural size under selection pressure) — **not** flagged. *canonical* at l.406 ("ReLU is the canonical example") is idiomatic in the activation-function literature — **not** flagged.

## E — British English (Blue)

16 US spellings in live prose. The thesis is otherwise consistently `-ise/-isation`, and in places mixes both **within one sentence** (l.93 has *optimisation*; l.1588 has *optimization*).

| ID | Line | US form | → UK form |
|---|---|---|---|
| E-01 | 305 | optimized | optimised |
| E-02 | 337 | optimizes | optimises |
| E-03 | 642 | generalization | generalisation |
| E-04 | 643 | specialize | specialise |
| E-05 | 644 | specialized | specialised |
| E-06 | 962 | **Normalize.** (list label) | Normalise. |
| E-07 | 970 | specialization | specialisation |
| E-08 | 1174 | specialization | specialisation |
| E-09 | 1385 | normalization | normalisation |
| E-10 | 1446 | localized | localised |
| E-11 | 1366 | specializing | specialising |
| E-12 | 1566 | hypothesize | hypothesise |
| E-13 | 1576 | optimization | optimisation |
| E-14 | 1586 | modularize | modularise |
| E-15 | 1587 | operationalized | operationalised |
| E-16 | 1588 | optimization | optimisation |

**Not flagged (verified, correct):** `colorlinks`/`linkcolor`/`citecolor`/`urlcolor` (l.26–29) are hyperref *options*, not prose. `\centering` is a LaTeX command. No live instances of *behavior*, *color*, *analyze*, *labeled*, *modeled*, or *center* in prose. *toward* (6×) is valid in both varieties and was left alone; if you want strict British consistency, *towards* is the more common British form.

## T — Terminology and scope (Teal)

| ID | Line | Flagged text | Problem | Suggested direction |
|---|---|---|---|---|
| T-01 (l.93), T-02 (225), T-03 (230), T-04 (503), T-05 (693), T-06 (947), T-07 (988), T-08 (1097), T-09 (1152), T-10 (1584), T-11 (1615) | *see IDs* | *activation **palette*** / *activation **library*** | The set $\mathcal{A}$ is called by three different names. **palette** 6× · **library** 5× · **set** 2×. | Normalise all to **activation set**. At the first explanatory mention, "set of activation functions" is also fine. |
| T-12 | 226 | "reassigns the **historical innovation numbers**" | A hybrid term appearing nowhere else. The Background uses *innovation number* (Stanley's term); the Methodology uses *historical marker* exclusively. | "reassigns the **historical markers**". Optionally add one bridging clause in Methodology: "historical markers, Stanley's innovation numbers". |
| T-13 | 1108 | "…in the **best genome**" | *champion* (≈35×, Results) and *best genome* (≈8×, Methodology) denote the same object. | Use **champion** in prose; keep *best genome* only where it names a logged MLflow artefact (`best_fitness`). Align l.1027, 1028, 1170, 1205, 1378. |

**Verified correct — not flagged:**
- **`main study`** is used throughout (12×); **`pop200` appears nowhere** in the document, including comments. Compliant with `CLAUDE.md`.
- **condition / treatment / arm** — *condition* dominates; `(treatment)` at l.1097 pairs with `(baseline)` and `(tanh only)` as a role label, not a competing term. *arm* is never used. No defect.
- **task / environment** — used consistently (*task* = the learning problem, *environment* = the Brax simulator instance). No defect.
- **genome / network / controller** — the three-way usage is principled (encoding / phenotype / behavioural role), not sloppy. No defect.

## N — Notation and mathematics (Violet)

| ID | Line | Flagged text | Problem | Suggested direction |
|---|---|---|---|---|
| **N-04** | 1001 | "the **pre-activation** value of a node is computed as the sum of incoming weighted signals plus a bias term" | **Genuine error.** The formula at l.1004 defines $z_j = \phi_j(b_j + \sum w_{ij}v_i)$ — activation *applied* — so $z_j$ is a **post**-activation output, not a pre-activation. The recursion also never closes: $v_i$ is defined as "the output values of source nodes" but nothing states $v_j = \phi_j(\cdot)$. | Split into two equations: $z_j = b_j + \sum_{i\in\mathcal{I}_j} w_{ij}v_i$ (pre-activation, matching the prose) and $v_j = \phi_j(z_j)$ (output). This closes the recursion and makes *sum aggregation* the actual subject of the sentence. |
| N-07 | 1383 | "$\varepsilon^2 \approx 0$" | $\varepsilon^2$ is **never defined**. It appears in Results without introduction; the Evaluation Protocol (l.1211) announces Hodges–Lehmann, Cliff's $\delta$ and TOST, but not epsilon-squared. | Introduce it at l.1211 with a one-clause gloss (the Kruskal–Wallis effect size) and its interpretation scale. |
| N-02 | 910 | "$H$ denotes the set of homologous gene pairs" | **Collision:** $H$ = set of homologous gene pairs (l.908/910) *and* $H$ = Kruskal–Wallis statistic (l.93, 1383, 1445, 1452, 1504, 1556, 1614). | **Cheapest fix in the document.** The set is used exactly once, in one equation. Rename it $\mathcal{H}$ — calligraphic, matching the $\mathcal{A}$ / $\mathcal{I}_j$ style already in use. Zero cost, collision gone. |
| N-03 | 910 | "$\delta_i$ is the attribute distance for pair $i$" | **Collision:** $\delta_i$ (attribute distance) vs Cliff's $\delta$ (effect size, l.1211+). Lower risk — $\delta_i$ always carries its subscript, Cliff's $\delta$ is always name-qualified — but it compounds with N-01/N-02. | Either rename to $\Delta_i$, or cover it with a notation table. |
| N-01 | 910 | "$c_d$ and $c_w$ weight the two terms" | **The known $d$ collision.** See the assessment below. | Options only — see below. You have decided **not** to rename either $d$. |
| N-05 | 864 | `a_{\text{Walker}} = f(\mathbf{o}_{\text{Walker}})_{1:6}` | Subscript is `Walker` here but `Walker2D` everywhere else. Also `_{1:6}` on a 6-dimensional output is a redundant no-op slice, and l.868 says Walker2D uses outputs "directly without modification" — which contradicts writing an explicit slice. | Rename to $a_{\text{Walker2D}}$ / $\mathbf{o}_{\text{Walker2D}}$; drop `_{1:6}` (or keep it only for symmetry with the Hopper line, and say so). |
| N-06 | 1366 | `\mathrm{fit} = \min(r_{\text{hopper}}/3000,\ldots)` | Inconsistent with the definition at l.968: subscripts lowercased (`hopper`/`walker2d` vs `Hopper`/`Walker2D`), and `\mathrm{fit}` vs `\text{fit}`. Recurs at l.1504. **This line also overflows the right margin** — see F-08. | Capitalise the subscripts and unify `\text{fit}` / `\mathrm{fit}` across l.968, 1366, 1504. |
| N-08 | 205 | "saturating ($\tanh$, $\sigma$)" | $\sigma$ is used bare for the sigmoid in the Introduction, **before** Table 1 (l.434) defines it. $\sigma$ also has a strong default reading as *standard deviation*, which the thesis does report (though never with the symbol $\sigma$) — a reading hazard, not a hard collision. | Write "sigmoid ($\sigma$)" at l.205, matching l.992's own convention. |

### The `$d$` collision — severity and options

**Severity: low-to-moderate, and largely benign in practice.** The two $d$'s never appear in the same section, paragraph, or chapter. Compatibility distance $d$ appears exactly once, in the displayed equation at l.908 and its gloss at l.910. Cohen's $d$ appears only in prose and is *always* immediately preceded by the words "Cohen's" (l.93, 211, 1199, 1409, 1625), which disambiguates it at every occurrence. **There is no equation in which both could be read.**

Two things raise it above zero. First, Cohen's $d$ appears **first in reading order** (Abstract l.93, Introduction l.211), so a reader arrives at the distance equation with a stale binding. Second — and this is the sharper edge — the distance equation *already* contains $c_d$, a subscripted $d$ meaning "disjoint", not "distance". So within the single expression at l.908 the letter $d$ carries two unrelated roles. Compounded with N-02 ($H$) and N-03 ($\delta$), **three of the four symbols in that one equation are re-used as statistics later in the thesis.** Individually survivable; together they read as an unmanaged notation namespace, which is the kind of thing an examiner picks at.

Four options (**not ranked — your call**; you have ruled out renaming either $d$, so option 1 is included only for completeness):

1. **Subscript the compatibility distance only** — $d_{\text{compat}}$ at l.908/910, Cohen's $d$ untouched. *Pro:* two lines changed; also disambiguates against $c_d$ in the same expression. *Con:* departs slightly from NEAT convention — though note Stanley & Miikkulainen actually use $\delta$, so the convention is weaker than it looks. **You have excluded this.**
2. **Add a notation table / list of symbols.** *Pro:* resolves N-01, N-02, N-03, N-08 and the $n$ reuse in one artefact, changes no equation or sentence, and is standard thesis practice. *Con:* does not remove the local friction at l.908 — the reader must leave the page — and does not fix N-07, which needs a *definition*, not a lookup entry.
3. **One clarifying sentence at the equation** — e.g. "This $d$ is the genetic compatibility distance, unrelated to Cohen's $d$ (Section 5.2)." *Pro:* one line; disarms the exact misreading. *Con:* meta-commentary about notation is slightly inelegant in a Methodology chapter, and it flags the collision rather than dissolving it.
4. **Leave $d$ alone; fix its two cheap neighbours instead** — rename $H \to \mathcal{H}$ (N-02) and optionally $\delta_i \to \Delta_i$ (N-03). *Pro:* the equation then reuses *one* statistical letter instead of three, which reads as a genuine convention clash rather than carelessness; $\mathcal{H}$ matches the $\mathcal{A}$/$\mathcal{I}_j$ style already used. Zero disruption to your decision on $d$. *Con:* the $d$ collision itself remains.

Options 2, 3 and 4 combine cleanly. **Given your decision not to rename $d$, option 4 (+ optionally 2) is the highest-value path**, but the choice is yours.

## A — Abbreviations (Purple)

| ID | Line | Abbreviation | Problem | Suggested direction |
|---|---|---|---|---|
| A-04 | 1382 | **IQR** | Never expanded. "Interquartile range" appears at l.1205 *without* the acronym in parentheses, then IQR is used cold in Results. | At l.1205 write "interquartile range (IQR)". |
| A-02 | 1399 | **HL** | Used in the Table 5 header, never introduced. "Hodges–Lehmann" is spelled out at l.1211 but the abbreviation is never defined. | Write "Hodges–Lehmann shift", or introduce "(HL)" at l.1211. |
| A-01 | 1079 | **MJX** | Used unexpanded in the Methodology table (l.1079), then expanded much later at l.1364 ("MJX (MuJoCo on GPU)") — backwards. | Expand at first use (l.1079 or its surrounding text); drop the late re-expansion. |
| A-03 | 1411 | **TOST** | Introduced backwards: "two one-sided tests" appears unabbreviated at l.1211, then "(Welch TOST)" at l.1411. | Introduce as "two one-sided tests (TOST)" at l.1211 and use TOST thereafter. |
| A-07 | 457 | **FD-NEAT** | **Never expanded anywhere**, yet used twice (l.457, and inside HA-FD-NEAT at l.458). | Expand at first use. |
| A-05 | 454 | **SANN** | Defined but used **exactly once**. | Drop the abbreviation; just name the method. |
| A-06 | 457 | **FS-NEAT** | Defined but used exactly once. | Drop the abbreviation, or keep only if referenced again. |
| A-08 | 650 | **MoW** | Defined but used exactly once. | Drop the abbreviation. |
| A-09 | 643 | **LLMs** | Defined but used exactly once. | Drop the abbreviation. |

**Verified correct:** NEAT, HA-NEAT, TWEANN, ANN, CPPN, XLA, JAX are all expanded at first use and used consistently. **RL** and **MDE** do not appear as abbreviations in live text at all.

## F — Figures, tables, cross-references (Amber)

| ID | Line | Severity | Problem | Suggested direction |
|---|---|---|---|---|
| **F-01** | 350–363 | **BLOCKER** | `Figures/genotype_phenotype.png` **does not exist.** `Figure~\ref{fig:genotype-phenotype}` is cited in live prose (l.350), but the float draws a dashed TikZ placeholder rectangle. The thesis currently ships a visible empty box in §2.3. | **Author action required.** Create/supply the asset, then swap in the `\includegraphics` already commented at l.353. No agent can invent this image. |
| **F-02a** (1455), **F-02b** (1474), **F-02c** (1533) | see IDs | HIGH | The three subfigure-**group** figures have **no group-level `\label`**. Only the panels carry labels. The composite float is therefore unreferenceable and its group caption is unanchored. | Add `\label{fig:main-complexity}`, `\label{fig:main-dynamics}`, `\label{fig:main-activation}` after each group `\caption{}`. Panel refs can stay (subcaption renders them as "6a"). |
| **F-08** | 1366, 1016–1019, 1107–1108, 572–578, 986–990 | HIGH | **Your source thesis has 5 overfull hboxes** — text running past the right margin. Line 1366's fitness formula is one of them (I verified this by building a pristine copy of `main_revised.tex`: 5 overfull hboxes; it is not caused by my annotation). | Break the long inline formula at l.1366 (e.g. display it, or use `\min\!\big(\ldots\big)` with a line break), and check the other four sites in the log. |
| **F-03a** (1425), **F-03b** (1492), **F-03c** (1550) | see IDs | MEDIUM | Four `\FloatBarrier` calls sit **inside** `figure` environments, after the caption. `placeins`' `\FloatBarrier` is a body command that flushes the pending float queue; executed inside a float it is at best a no-op. It is also applied to only 4 of 11 live floats. | Move each to the line *after* `\end{figure}`, or drop them. Apply consistently. |
| **F-04** | 1129, 1175, 1368, 1385, 1077, 1505 | MEDIUM | **Thousands separation is inconsistent** — even for the *same quantity*. l.1175: `1024 to 4096 … 2000 generations`; l.1368: `1{,}024--4{,}096`. l.1385: `1{,}000`/`5{,}000`; l.962/968/1087: `3000`/`5000`. l.1077: `1,000` (plain comma). l.1505 contains **both styles in one sentence**. | Pick one rule and enforce it (recommended: no separator below 10,000). Do **not** put `{,}` inside math mode — keep `/3000` bare. |
| **F-07** | 1119–1157 | MEDIUM | `tab:hyperparameters` has **no units** anywhere. "Max species stagnation & 40" has an implicit unit of *generations*; "Fitness target & 10{,}000" is in **raw-return** units, not normalised units — a real ambiguity, given the normalised-minimum objective is bounded near 1.0 (l.1163 has to explain this in prose). | Add a Unit column, or append units in-cell. At minimum disambiguate the fitness target: "10{,}000 (raw, unnormalised)". |
| **F-06a** (1067), **F-06b** (1121), **F-06c** (1220) | see IDs | MEDIUM | Three table captions are bare Title-Case noun phrases with no terminal period, while every other caption is a full descriptive sentence in sentence case with a period. Two caption styles coexist. | Convert to sentence-case descriptive captions, e.g. "Specifications of the two Brax evaluation environments." |
| **F-05** | 445 | MEDIUM | `\caption{Comparison of common activation functions}` — the **only caption in the document with no terminal full stop**, and generic where the body (l.416) and Table 1 both scope this to *the five functions used in this thesis*. Not self-contained. | "The five activation functions of the HA-NEAT activation set $\mathcal{A}$." (+ period) |
| **F-09** | 1069, 1140 | LOW | Numeric columns are left-aligned (`l`) in `tab:env-specs` and `tab:hyperparameters`, so values do not align on the decimal. `tab:main-fitness` correctly uses `{lcc}`. | Use `{lr}` / `S` columns, or accept as cosmetic. |

**Verified correct (checked, not skipped):** All 12 live `\includegraphics` resolve to files that exist (only `genotype_phenotype.png` is missing, and it is *not* in an `\includegraphics` — it is a placeholder box). **Every `\ref{}` resolves** — zero dangling references. **No `\ref` type mismatches** (section refs point at sections, figure refs at figures, table refs at tables). **All `\label{}` are unique** — no duplicates. **No orphan floats** — every `fig:`/`tab:` label is cited. Order of definition vs first reference is sound; the only forward reference (`tab:hyperparameters`, cited from Methodology before its Experimental-Settings definition) is a normal, deliberate pointer to a settings table. Panel `(a)`/`(b)` labelling matches source order in all five multi-panel captions.

> **Note on IDs without inline markers:** `F-08` (overfull hboxes) and `F-09` (column alignment) are
> document-wide typesetting findings with no single text span to colour, so they appear in this report
> only. `F-02*`, `F-03*`, `M-01` and `M-02` are *absences* — their markers are anchored at the relevant
> location as empty tags, exactly as you requested.

## M — Formal requirements (Grey)

Both are **flagged for your decision, not asserted as defects.** I searched the repository for institutional guidance (a style guide, thesis template, or submission-requirements file) and **found none**, so I am not inventing either requirement.

| ID | Item | Status |
|---|---|---|
| M-01 | **No `\listoffigures` / `\listoftables`**, with 11 live floats. | No positive evidence NOVA IMS requires them. **Your decision.** |
| M-02 | **No declaration of independent work / statement of authorship.** | Absent from the document. Many Master's programmes require one. **Verify against your programme handbook.** No repository evidence either way. |

Per your brief, I did **not** report: programme/university/department/supervisor placeholders, PDF metadata placeholders, the thesis title, or `\today`.

---

## Inventories

### Terminology variants

| Concept | Variants found | Preferred form |
|---|---|---|
| The set $\mathcal{A}$ of activation functions | **palette** (93, 947, 988, 1097, 1152, 1615) · **library** (225, 230, 503, 693, 1584) · **set** (1564, 1571) | **activation set** — 11 occurrences to change |
| Best evolved genome of a run | **champion** (≈35, Results) · **best genome** (≈8, Methodology: 1027, 1028, 1108, 1170, 1183, 1205, 1378) | **champion** in prose; *best genome* only for the logged artefact |
| Gene identity token | **historical marker** (10×, Methodology) · **innovation number** (3×, Background) · **historical innovation numbers** (226 — hybrid) | Split is defensible by section; **only the hybrid at l.226 is a defect** |
| Experimental group | **condition** (dominant) · **treatment** (1097, as a role label) · **arm** (0) | No change needed |
| Primary experiment | **main study** (12×) · **pop200** (0×) | Compliant with `CLAUDE.md` |

### Reinforcement-learning scope audit

Only **two live occurrences** exist in the entire document. Everything else labelled "RL"/"MTRL" is inside commented-out dead blocks (l.614–628, 743, 766, 768, 812, 827) and is out of scope.

| Location | Wording | Classification | Recommended wording |
|---|---|---|---|
| **l.37 — thesis title** | "**Reinforcement Learning** with NEAT in Multitask Environments" | **Revise — scope mismatch** | The thesis implements **no RL algorithm**; the method is neuroevolution in physics-based continuous control. A commented note at l.614 shows a supervisor already flagged this. Candidate: *"Heterogeneous Activation NEAT in Multi-Task Continuous Control"*. **Reported only — your brief excluded the title from annotation, so it carries no inline marker.** If the title cannot change administratively, add an explicit scope sentence to the Introduction. |
| l.573 | "…made physically grounded locomotion tasks tractable for **reinforcement-learning** research." | **Retain — contextual** | Correct as written. It describes MuJoCo's role in the RL *literature*, not this thesis's method. No change. |

Adjacent RL-flavoured vocabulary was checked and is used correctly: **policy** (8 live uses) in the method-agnostic sense of "the evolved control mapping"; **agent** (1 live use, l.838) not in an RL-method sense. Both **retain**.

### Symbols

| Symbol | Meaning(s) | First live use | Defined there? | Collision? |
|---|---|---|---|---|
| $d$ | compatibility distance · **Cohen's $d$** | 93 (Cohen's) / 908 (distance) | Yes, both | **Yes — N-01** (Cohen's appears *first*) |
| $H$ | set of homologous gene pairs · **Kruskal–Wallis statistic** | 93 (KW) / 908 (set) | Yes, both | **Yes — N-02** |
| $\delta_i$ / $\delta$ | attribute distance · **Cliff's $\delta$** | 908 / 1211 | Yes, both | **Yes — N-03** |
| $z_j$ | claimed pre-activation; formula gives post-activation | 1004 | **Contradictory** | **N-04** |
| $\varepsilon^2$ | Kruskal–Wallis effect size | 1383 | **No — never defined** | **N-07** |
| $\sigma$ | sigmoid | 205 | **No** — glyph used bare, defined at 434 | Reading hazard vs SD — **N-08** |
| $f$ | the network $\mathbb{R}^{17}\to\mathbb{R}^{6}$ · generic activation ($f(x)=x$) | 433 / 861 | Yes, both | Mild, different chapters |
| $n$ vs $n_1,n_2$ | seeds per condition · genome gene counts | 908 / 1409 | Yes | Mild, subscripted vs bare |
| $c_d$, $c_w$, $D$, $\theta$, $\mathcal{A}$, $p_{\text{act}}$, $\phi_j$, $b_j$, $w_{ij}$, $v_i$, $\mathcal{I}_j$, $\alpha$ | — | — | **Yes, all defined on first use** | No |
| $N_{\max}$ / $C_{\max}$ | array capacities | 881 / 882 | $N_{\max}$ never spelled out; $C_{\max}$ defined late (l.1017) | Minor |

### Abbreviations

| Abbreviation | Introduced at first use? | Uses | Issue |
|---|---|---|---|
| NEAT, HA-NEAT, TWEANN, ANN, CPPN, XLA, JAX | Yes | many | None |
| **IQR** | **No** | 3 | A-04 |
| **HL** | **No** | 3 | A-02 |
| **MJX** | **Backwards** (used 1079, expanded 1364) | 3 | A-01 |
| **TOST** | **Backwards** | 2 | A-03 |
| **FD-NEAT** | **Never expanded** | 2 | A-07 |
| **SANN**, **FS-NEAT**, **MoW**, **LLMs** | Yes, but | 1 each | Single-use — not worth abbreviating (A-05, A-06, A-08, A-09) |
| RL, MDE | — | 0 | Do not appear in live text |

---

## Author action required

1. **`Figures/genotype_phenotype.png` (F-01) — BLOCKER.** The asset does not exist. §2.3 currently renders an empty dashed placeholder box. You must supply the image; the `\includegraphics` line is already written and commented at l.353.
2. **Declaration of independent work (M-02).** Absent. No repository evidence establishes whether NOVA IMS requires one — **verify against your programme handbook.**
3. **List of Figures / List of Tables (M-01).** Absent, with 11 floats. No evidence it is required. Your decision.
4. **The thesis title (out of annotation scope, reported for completeness).** It promises reinforcement learning; the work is neuroevolution. This is the largest scope mismatch in the document and a supervisor has already raised it.

## Deliberately not reported

- **Commented-out draft text, old tables, and planning comments** — explicitly out of scope. Large dead blocks (≈ l.596–830, 922–934, 1031–1055, 1240–1355) were excluded from every category. I verified each finding sits in **live** text; three subagent findings were dropped for landing in comments.
- **Calibrated hedging.** The marker-reassignment explanation is presented as a hypothesis, RQ1 receives a qualified negative, and the MDE bound is stated as excluding only large effects. All intentional. Untouched.
- **Statistics, p-values, effect sizes, numerical results.** Not reassessed.
- **Citation content and syntax.** Not assessed. `\parencite`/`\textcite` are already normalised; **zero instances of `\parentcite`** — confirmed.
- **Items already fixed in `revision_report.md`.** Cross-checked; no previously-fixed issue is re-reported.
- **`parsimonious` / `parsimony`** — used in the genuine model-selection sense. Kept.
- **`canonical` at l.406** ("ReLU is the canonical example") — idiomatic in the literature. Kept.
- **`toward`** (6×) — valid in British English. Not flagged.
- **Long-but-clear sentences, active voice, first-person plural** — deliberate style. Not flagged.
