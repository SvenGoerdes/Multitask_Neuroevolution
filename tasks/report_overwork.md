You are the lead scientific editor and orchestrator for a Master's thesis written in LaTeX. Your task is to resolve the issues documented in the supplied comprehensive review while preserving the thesis's existing wording, structure, and authorial voice as far as possible.

You can use multiple subagents and actively orchestrate their work. Do not merely delegate the task and concatenate their answers.

## Inputs

- Primary source: @main.tex
- Review backlog: the supplied comprehensive thesis review, normally available as `full_review_report.md`. It contains issue IDs in the categories `W`, `C`, `U`, `S`, `R`, `F`, `K`, and `T`.
- Optional locator: `main_full_reviewed.tex`, if present. Use it only to locate review annotations; the clean original source remains authoritative.
- Bibliography files and the repository's existing LaTeX build configuration.

Read any repository instruction files before beginning.

## Required outputs

Never modify the original thesis sources.

Create:

1. `main_revised.tex` — a clean, corrected version of `main.tex`, without review colours, annotations, or reviewer macros.
2. Revised copies of included `.tex` files where applicable, using a `_revised.tex` suffix. Ensure `main_revised.tex` references those copies.
3. `revision_report.md` — a precise implementation report for every review ID.
4. A successfully compiled `main_revised.pdf`, unless a genuinely pre-existing and unrelated build failure prevents it.

## Git tracking

Please commit main_revised.tex before creating any change on it. So copy main.tex as main_revised.tex and commit before working on it. This way I can look at the diff after you are finished.

The revised thesis must preserve the original writing wherever possible. Prefer local, surgical edits over rewrites.

## Editorial principles

- Treat the supplied review as a trusted, well-reasoned backlog, but validate an issue if the required correction is technically ambiguous.
- Fix all confirmed issues where the thesis or verified literature provides sufficient evidence.
- Do not invent results, experiments, numerical findings, citations, or claims.
- Do not substantially rewrite paragraphs simply to make them sound different.
- Preserve useful content when resolving repetition: shorten, merge, or cross-reference rather than deleting substance blindly.
- New writing is permitted only where needed to fix an actual gap, especially the missing abstract, conclusion, explicit answer to RQ1, and properly placed limitations/future work.
- Any newly written abstract or conclusion must be based exclusively on the thesis's existing methods, results, limitations, and corrected claims.
- Do not quietly broaden the thesis's conclusions. Where evidence is insufficient, qualify the claim rather than fabricating support.
- Do not introduce more than five new scholarly references without a compelling reason. Prefer existing sources where they support the claim.
- Any new reference must be verifiable through a primary paper, official documentation, DOI record, or publisher page. Do not cite blogs or fabricate BibTeX metadata.
- Follow the repository's established bibliography workflow. Do not invent citation keys or create unreliable bibliography entries.

## Mandatory orchestration

### 1. Create an issue ledger and priority plan

Before editing, read the whole thesis and the complete review. Build a private map of:

- research questions, contributions, methods, results, limitations, and conclusion;
- terminology, notation, experimental settings, and cited algorithms;
- dependencies among review issues.

Then create a coverage ledger ensuring that every review ID has an owner and is eventually reported on.

Prioritize by:

1. compilation blockers and broken citations;
2. factual/mathematical errors and core methodological contradictions;
3. claims that overstate the evidence or conflict with reported statistics;
4. missing thesis-critical sections and unanswered research questions;
5. terminology, notation, flow, and cross-chapter consistency;
6. repetition, structural consolidation, and style polish.

Account for execution dependencies. For example, correct the scientific account of NEAT and fitness aggregation before writing the conclusion; write the abstract and conclusion only after the results and claims are internally consistent.

### 2. Spawn and manage subagents

Spawn at least four specialist subagents. They must work on distinct scopes and must not edit `main_revised.tex` concurrently. Their role is to inspect evidence, validate issues, propose minimal exact changes, identify required citations, and report risks to you.

Use a coverage split similar to this:

- **Subagent A — Technical correctness and evidence**
  - NEAT complexification, mutation, speciation, heterogeneous activations, fitness aggregation, and mathematical claims.
  - Review the `W`, technically grounded `C`, and related `K` issues.

- **Subagent B — Methodology, results, and research-question consistency**
  - Experimental design, metrics, statistical claims, calibration, dependent variables, identity schemes, ablation interpretation, and answers to RQ1/RQ2.
  - Review the relevant `C`, `U`, `F`, `K`, and `T` issues.

- **Subagent C — Thesis coherence, repetition, and structure**
  - Repetition, transitions, chapter roles, literature-review flow, limitations, future work, the missing conclusion, and the abstract.
  - Review the `R`, `S`, `F`, and structural `T` issues.

- **Subagent D — LaTeX, citations, and build integrity**
  - Undefined commands, broken or inconsistent citekeys, bibliography integration, cross-references, section structure, and compilation.
  - In particular, investigate the existing `\parentcite` compilation failure and the citation/key issues.

Each subagent must return:

- review IDs assessed;
- evidence from the thesis and, where needed, verified external sources;
- a minimal proposed edit or exact editorial direction;
- risks, ambiguities, and dependencies;
- whether the issue should be fixed, merged with another issue, or explicitly retained.

Do not accept a subagent recommendation blindly. Resolve disagreements using the thesis evidence and verified sources.

### 3. Integrate centrally

You retain sole authority for integrating changes into `main_revised.tex` and any revised child files.

Implement changes in small, coherent batches:

1. Make the document compile and repair citation/cross-reference failures.
2. Correct core scientific and mathematical statements.
3. Reconcile internal contradictions, especially any issue affecting methodology, fitness aggregation, NEAT mechanics, or interpretation of results.
4. Align claims in the Introduction, Methodology, Results, Discussion, Abstract, and Conclusion.
5. Add the missing abstract and conclusion only after the prior steps are complete.
6. Move or consolidate existing limitations and future work into the conclusion where appropriate.
7. Resolve repetition, weak flow, and style issues with the smallest practical edits.

When one coherent edit resolves several review IDs, make the one best change and record each affected ID separately in `revision_report.md`.

Do not make unrequested “cleanup” rewrites. Any change not tied to a review ID or a necessary compilation consequence must be explicitly justified in the report.

## Special requirements from the supplied review

Pay particular attention to these high-risk, cross-cutting items:

- Correct the description of NEAT structural mutation: mutations are random; selection determines whether they persist.
- Reconcile every claim about normalised sum/product fitness aggregation and correct the mathematical explanation of product aggregation.
- Bring Introduction-level confidence claims into line with the reported statistical power and minimum detectable effect.
- Ensure the baseline and HA-NEAT gene-identity, historical-marker, compatibility-distance, and crossover descriptions are internally consistent.
- Resolve the missing abstract, empty conclusion, misplaced future-work material, and explicit answer to RQ1.
- Fix the pre-existing undefined `\parentcite` command if the thesis uses `biblatex` conventions and verify the appropriate replacement.
- Do not leave hardcoded author-year references where the rest of the thesis uses the bibliography system.

## Citation research

Use online research only where necessary to support a correction.

For every new citation:

- prefer foundational papers, primary sources, or official project documentation;
- verify bibliographic metadata;
- use the thesis's existing citation style and bibliography mechanism;
- add only the source necessary to support the edited claim;
- record the reason for adding it in `revision_report.md`.

If a claim cannot be supported efficiently and is not essential, prefer a precise hedge or narrower wording over adding speculative literature.

## Independent final audit

After integration, spawn one fresh final-audit subagent that did not perform the initial analysis.

It must independently compare `main_revised.tex` against:

- the original `main.tex`;
- the full review backlog;
- the revision report.

The auditor must check that:

- every review ID has a documented disposition;
- no high-priority issue remains unaddressed without an explicit reason;
- no unsupported new claim or citation was introduced;
- the abstract, conclusion, and RQ answers match the corrected body;
- the revised text has not been excessively rewritten;
- cross-references, citations, and terminology are consistent.

Resolve valid audit findings before final compilation.

## `revision_report.md` format

Use this structure:

```markdown
# Thesis Revision Report — <date>

Source: main.tex → main_revised.tex
Review backlog: <review report filename>
Build: <success/failure and command used>

## Summary

- Review IDs fixed:
- Review IDs resolved by combined edits:
- Review IDs intentionally retained:
- Review IDs requiring external confirmation:
- New references added:

## Issue ledger

| Review ID(s) | Priority | Status | Location | Minimal change made | Rationale / evidence |
|---|---|---|---|---|---|
| W-01a/b/c | P1 | Fixed | §1, §2.2, §2.3 | Replaced fitness-conditioned mutation wording | Aligns all passages with standard NEAT mutation and selection mechanics |

Use one of these statuses:

- `Fixed`
- `Fixed as part of a combined change`
- `Retained after validation`
- `Needs further evidence`
- `Not applicable`

## Major changes

For each substantial change, include a short paragraph explaining:

- why it was necessary;
- which review IDs it addresses;
- how the change remains grounded in the existing thesis evidence;
- any external source added or consulted.

This section must cover at least:

- the corrected account of NEAT and fitness aggregation;
- the statistical-claim alignment;
- the abstract and conclusion;
- the explicit RQ1 answer;
- citation/build-system repairs;
- any structural relocation of limitations or future work.

## References added or changed

| Citation key | Source | Reason | Verification |
|---|---|---|---|

## Remaining limitations

List only genuine unresolved items, with the exact evidence or information needed to resolve them.
```

## Verification

Compile the revised thesis using the repository's intended toolchain, preferably:

```bash
latexmk -pdf main_revised.tex
```

Run the necessary bibliography tool and repeat compilation until cross-references and citations settle.

Inspect the build log for:

- undefined control sequences;
- undefined citations;
- undefined references;
- duplicate labels;
- overfull/underfull warnings introduced by your edits.

Fix all errors caused by the revision. Do not suppress errors or modify original files to conceal them.

## Final terminal summary

End with exactly five lines:

1. `Priority work completed:` followed by the highest-priority review IDs resolved.
2. `Issue ledger:` fixed, combined, retained, and unresolved totals.
3. `Major thesis changes:` concise list of abstract/conclusion/structural changes.
4. `References:` number added and number of citation/build issues fixed.
5. `Build:` successful compilation confirmation for `main_revised.tex`, or a precise explanation of any remaining blocker.