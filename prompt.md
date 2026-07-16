You are the lead academic editor for a LaTeX Master's thesis. Implement the confirmed findings from the language and consistency review while preserving the existing text, structure, technical claims, and authorial voice as closely as possible.

This is a **targeted revision**, not a rewrite. Make the smallest change that resolves each issue. Do not conduct a new thesis-wide editing pass.

Actively orchestrate multiple subagents. You retain sole authority for integrating changes into the thesis file.

## Inputs

Read these files completely before acting:

- `thesis/main_language_reviewed.tex` — annotated review source and baseline for this task.
- `thesis/language_review_report.md` — the 89 findings and their exact IDs.
- `thesis/main_revised.tex` — unannotated approved source, used only to verify that annotation wrappers are preserved correctly.
- `thesis/revision_report.md` — previous implementation history.
- `.claude/principles/academic-writing.md`
- The \scientific-writing-humanizer skill 

Treat the Humanizer skill as a **bounded line-editing policy**, not permission for a broad rewrite. Apply it only when changing text for an existing review finding or when a directly adjacent adjustment is essential for the changed sentence to read naturally.

## Git baseline — mandatory

Before making substantive changes:

1. Run `git status --short` and preserve all existing user changes.
2. If `thesis/main_language_reviewed_revised.tex` already exists, stop and request direction. Do not overwrite it.
3. Copy:

```bash
cp thesis/main_language_reviewed.tex thesis/main_language_reviewed_revised.tex
```

4. Stage and commit **only** this new baseline file on the current branch:

```bash
git add -- thesis/main_language_reviewed_revised.tex
git commit -m "chore: add language revision baseline"
```

Never use `git add -A`.

After the baseline commit:

- Make all revisions only in `thesis/main_language_reviewed_revised.tex`.
- Do not modify `thesis/main_language_reviewed.tex`, `thesis/main_revised.tex`, `thesis/main.tex`, or any existing `.bib` file unless a verified new citation is strictly necessary.
- Leave all substantive edits unstaged and uncommitted.
- Do not create a final commit.
- The author must be able to inspect the complete thesis revision with:

```bash
git diff -- thesis/main_language_reviewed_revised.tex
```

Create `thesis/language_revision_report.md` after the baseline commit. Leave it unstaged and uncommitted as well.

## Annotation preservation

`main_language_reviewed_revised.tex` must retain all existing coloured review wrappers and issue IDs.

When fixing a marked passage, update the text inside the existing wrapper rather than removing the wrapper. For example:

```latex
\revGram{G-01}{The set contains several distinct function shapes}
```

The colours and IDs are now an audit trail showing what was revised. They do not indicate that the corrected text remains wrong.

Do not renumber, delete, duplicate, or create new review IDs. Preserve report-only findings as report-only findings.

## Explicitly deferred by the author

Do not fix, improve, generate, or otherwise alter the following:

- `F-01`: the missing `Figures/genotype_phenotype.png` asset and its placeholder;
- `F-08`: existing overfull hboxes, margin overflow, or line-breaking/layout adjustments;
- `M-01`: adding a List of Figures or List of Tables;
- `M-02`: declaration of independent work or statement of authorship;
- the thesis title, including its reinforcement-learning scope mismatch;
- programme, university, department, supervisor, co-supervisor, PDF metadata, or other author-supplied thesis details;
- commented-out draft text, old tables, or planning comments.

Do not attempt to solve these indirectly. For example, do not add `\small`, `\resizebox`, manual spacing, or forced line breaks to address overfull boxes.

A content correction may naturally alter a line that happens to overflow, but do not optimize the layout or treat the warning as a revision target.

## Style and Humanizer constraints

Use the /scientific-writing-humanizer skill only to make changed passages sound like precise, natural academic writing.

For every rewritten passage:

- preserve the technical meaning, claims, data, citations, and calibrated hedge level;
- retain the thesis’s first-person plural and active academic voice where appropriate;
- prefer direct wording over metaphors, idioms, inflated vocabulary, vague attributions, and unnecessary nominalisation;
- avoid chatty language, rhetorical questions, conversational asides, and generic AI-style framing;
- do not run a broad AI-vocabulary sweep beyond the reported findings;
- do not alter unaffected paragraphs merely to vary sentence length or remove a pattern globally;
- do not introduce a semicolon in prose, captions, headings, tables, or any newly written text;
- if a review suggestion would normally use a semicolon, find a clear alternative using a full stop, comma, colon, or sentence restructuring;
- do not introduce em dashes merely as stylistic punctuation.

Do not remove legitimate technical terminology such as `parsimonious` where it has the formal model-selection meaning already validated in the review.

## Scope of implementation

Use `language_review_report.md` as the issue ledger.

Implement all confirmed findings except the explicitly deferred items above. Use these priorities:

### Priority 0 — correctness and notation

Resolve first:

- `N-04`: correct the activation equation and close the recursion using separate pre-activation and output equations.
- `N-02`: rename the homologous-pair set from `$H$` to `$\mathcal{H}$`.
- `N-03`: rename attribute distance from `$\delta_i$` to `$\Delta_i$`.
- `N-05`, `N-06`, `N-07`, `N-08`: apply the minimal corrections described in the review.
- Preserve the author’s prior decision: do **not** rename compatibility-distance `$d$` or Cohen’s `$d$` (`N-01`).

For `N-07`, use an existing verified source where available. If a new source is genuinely necessary, add at most three verified scholarly references across the entire task, record each one, and use the repository’s bibliography workflow. Do not invent metadata or citation keys.

### Priority 1 — grammar, clarity, terminology, and abbreviations

Resolve:

- all `G-*` grammar and punctuation issues;
- all `L-*` clarity issues;
- all `P-*` plain-language issues;
- all `E-*` British-English standardisation issues;
- `T-01` through `T-13`, including normalising to **activation set**, replacing the hybrid historical-identity term, and using **champion** in prose;
- all `A-*` abbreviation issues.

Keep the title unchanged even though the report identifies it as an RL scope mismatch. The only live body reference to reinforcement learning is contextual and should remain unchanged.

### Priority 2 — figures, tables, and LaTeX structure

Resolve the non-deferred `F-*` findings:

- add group-level labels for the affected composite figures;
- move or remove misplaced `\FloatBarrier` commands;
- standardise thousands separators using the review’s recommended rule;
- improve caption consistency;
- clarify table units and the raw, unnormalised fitness target;
- apply low-risk numeric-column alignment improvements if they do not create layout work.

Do not fix `F-01` or `F-08`.

## Multi-agent orchestration

First, read the full review and build a coverage matrix for all review IDs.

Then spawn at least four subagents with non-overlapping scopes. They must inspect the relevant source, validate the proposed edit, and return minimal replacement text or precise LaTeX changes. They must not edit `main_language_reviewed_revised.tex` directly.

You may use this division:

- **Subagent A:** grammar, clarity, plain academic language, British English (`G`, `L`, `P`, `E`);
- **Subagent B:** terminology, RL scope preservation, abbreviations (`T`, `A`);
- **Subagent C:** notation, mathematics, and equations (`N`);
- **Subagent D:** figures, tables, cross-references, and LaTeX mechanics (`F`).

You must validate every recommendation before integrating it. Resolve any conflict in favour of the smallest technically correct change.

After integration, spawn a fresh final-audit subagent. It must compare the revised annotated file, the original language review, and the implementation report. It should report only:

- unaddressed non-deferred IDs;
- accidental rewrites beyond scope;
- introduced semicolons;
- broken wrappers or IDs;
- changed technical claims, citations, or hedging;
- compilation risks.

Fix valid audit findings before final verification.

## `language_revision_report.md`

Create this report:

```markdown
# Language Review Revision Report — <date>

Source: `main_language_reviewed.tex` → `main_language_reviewed_revised.tex`
Baseline commit: <short hash>
Build: <status>

## Summary

- Fixed:
- Deferred by author:
- Intentionally unchanged:
- Needs author decision:
- New references added:

## Issue ledger

| Review ID(s) | Status | Location | Minimal change | Rationale |
|---|---|---|---|---|

Statuses:
- Fixed
- Fixed by combined edit
- Deferred by author
- Intentionally unchanged
- Needs author decision

## Significant changes

Briefly explain only changes with meaningful technical or structural consequences, including:

- the corrected node-activation equations;
- notation changes from `$H$` to `$\mathcal{H}$` and `$\delta_i$` to `$\Delta_i$`;
- the definition of `$\varepsilon^2$`;
- terminology normalisation;
- any necessary figure/table-label or unit changes.

## Deferred by author

List exactly:

- F-01 missing figure;
- F-08 overfull hboxes;
- M-01 lists of figures/tables;
- M-02 declaration of independent work;
- thesis-title replacement and RL title mismatch;
- author-supplied thesis metadata.

## Verification

- Wrapper/ID integrity:
- Source files left unchanged:
- Build result:
- Git status:
```

Every review ID must have one status. If one edit resolves multiple IDs, list every ID separately or as an explicit grouped entry.

## Verification

From `thesis/`, compile:

```bash
latexmk -pdf main_language_reviewed_revised.tex
```

Verify:

- `main_language_reviewed_revised.pdf` is produced;
- no undefined control sequences, citations, references, or duplicate labels were introduced;
- all original review wrappers and IDs remain present exactly once;
- `main_language_reviewed.tex`, `main_revised.tex`, and `main.tex` have unchanged hashes from before the task;
- no new semicolons were introduced in the revised file;
- `git diff --check` succeeds;
- all substantive edits remain unstaged and uncommitted after the baseline commit.

Do not attempt to eliminate the author-deferred overfull-box warnings. Report them as known, deferred warnings only.

## Completion: exactly five lines

1. `Revision status:` fixed, deferred, unchanged, and unresolved totals.
2. `Highest-priority fixes:` the notation and technical corrections completed.
3. `Style and terminology:` counts for grammar, clarity, plain-language, UK-English, terminology, and abbreviation fixes.
4. `Deferred by author:` missing figure, overflow, lists, declaration, title, and metadata.
5. `Build and Git:` compilation result, baseline commit hash, and confirmation that revisions remain unstaged and uncommitted for `git diff`.
