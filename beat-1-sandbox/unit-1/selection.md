# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/69

**Verdict output**

```
Ranked live-mode grading of 3 candidates from codepath/pathreview-ai301-fa26-s1:

1. #69: Output parser crashes on a top-level JSON array fallback (rag/generator/output_parser.py)
  - Top fit: Direct fit for Python backend logic handling LLM/RAG output parsing; isolated fix with existing failing test.
2. #72: verify_password raises UnknownHashError on malformed stored hashes (core/security.py)
  - Good secondary fit: Backend security utility fix in Python, clear scope, but less relevant to AI data pipelines.
3. #61: Health check DB probe fails under SQLAlchemy 2.x (api/routes/health.py)
  - Accepted candidate: Small dependency version fix in API route, well bounded.

[
  {"item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/69",
   "checks": [
     {"name": "Active repository", "grade": "pass", "evidence": "not archived, last push 2026-09-10 (4 days ago)"},
     {"name": "Scoped & bounded deliverable", "grade": "pass", "evidence": "single bug in rag/generator/output_parser.py with reproducing test case"},
     {"name": "Unclaimed status", "grade": "pass", "evidence": "0 assignees, 0 open PRs, no active claims"},
     {"name": "AI contribution policy", "grade": "pass", "evidence": "no restrictive AI policy present in repo docs"},
     {"name": "Newcomer friendly signal", "grade": "pass", "evidence": "labeled good-first-issue"}
   ], "verdict": "accept"},
  {"item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/72",
   "checks": [
     {"name": "Active repository", "grade": "pass", "evidence": "not archived, last push 2026-09-10"},
     {"name": "Scoped & bounded deliverable", "grade": "pass", "evidence": "single security fix in core/security.py"},
     {"name": "Unclaimed status", "grade": "pass", "evidence": "0 assignees, 0 open PRs"},
     {"name": "AI contribution policy", "grade": "pass", "evidence": "no restriction stated"},
     {"name": "Newcomer friendly signal", "grade": "pass", "evidence": "labeled good-first-issue"}
   ], "verdict": "accept"},
  {"item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/61",
   "checks": [
     {"name": "Active repository", "grade": "pass", "evidence": "not archived, last push 2026-09-10"},
     {"name": "Scoped & bounded deliverable", "grade": "pass", "evidence": "single DB probe fix in api/routes/health.py"},
     {"name": "Unclaimed status", "grade": "pass", "evidence": "unassigned, 0 PRs"},
     {"name": "AI contribution policy", "grade": "pass", "evidence": "no restriction stated"},
     {"name": "Newcomer friendly signal", "grade": "pass", "evidence": "labeled good-first-issue"}
   ], "verdict": "accept"}
]
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

1. Initial run: 14/20 agreement. Overly restrictive criteria in `Scoped & bounded deliverable` and a separate response-time check incorrectly rejected valid issues (such as issue-01, issue-04, issue-14, issue-16, and issue-19).
2. Removed the standalone response-latency check after recognizing it duplicated `Active repository` and penalized maintained repos with low sample counts (e.g. issue-14). Re-running disagreed items via `--only`: 5/6 matched.
3. Refined `Scoped & bounded deliverable` criteria to ensure concise descriptions, multi-file documentation changes, or bug reports with multiple candidate root causes are not flagged as unscoped. Re-testing the 6 items with `--only`: 6/6 matched.
4. Final full evaluation run (`--save-run eval-run.txt`): 19/20 agreement (bar: 18/20: PASS).

**Issue analysis**

`issue-04`: Rubric verdict `accept`, matching the gold label (`accept`).
The issue body lists multiple items ("Including remove identity, fuse spiders, remove self loops, etc.") in a brief note. In an earlier iteration, my scope check misinterpreted this bulleted list as an un-scoped multi-part deliverable. The gold rationale clarifies that this is a single maintainer-filed bug in an active repository where the listed items share the exact same underlying logic fix (rule preview handling). Updating the pass condition to explicitly permit checklists of identical small fixes allowed the rubric to correctly align with the gold label.

**Check rationale**

Current text of `Scoped & bounded deliverable` (weight: required) in `rubric.md`:

> Passes if the issue describes one self-contained task for a single contributor in one PR — including terse descriptions, bug reports listing several potential root causes, or single fixes touching multiple files. Fails if it is an explicit multi-item tracking/umbrella issue, an unresolved product debate, a pure support request, a task requiring core framework refactoring, or an issue with 2+ previous abandoned/unmerged PR attempts.

This check is formulated to distinguish between genuine scope issues (such as un-scoped epic tracking threads or open architectural debates) and benign complexity (such as concise bug writeups, single fixes across a few files, or reports with multiple suspected causes). Earlier versions were too strict, misclassifying well-bounded tasks like issue-01, issue-04, and issue-19 as unscoped.

**Trade-offs**

Widening `Scoped & bounded deliverable` to accommodate brief issue bodies and multi-file changes introduced a false positive on `issue-20` (gold: `reject`, rubric: `accept`). Issue-20 is a feature request ("Add company logo shape to the toolbar") with unspecified requirements ("Logo asset TBD") and no maintainer discussion. Because its single-feature description resembles bounded work, the broader scope rule accepts it. Tightening the check to filter out unresolved assets/requirements would have caused regressions across 5 valid issues, so accepting this single discrepancy maintains a strong overall score of 19/20 while satisfying all category floors.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

1. Fit to interests & time: Issue #69 is a great match for my background in Python and interest in LLM/RAG data processing pipelines (`rag/generator/output_parser.py`). It focuses on handling edge-case JSON structure fallbacks during model output parsing, providing relevant practical experience in a manageable 2-4 hour scope.
2. Rubric evaluation vs manual checks: The rubric correctly verified that the issue is active, unassigned, bounded within one file, and compliant with contribution policies. Manually reviewing the repository confirmed that a pre-written failing unit test is already available in the test suite to validate the fix.
3. Anticipated difficulty: Low to moderate. The task is localized to `output_parser.py` with an existing failing test case, minimizing setup complexity and allowing fast iteration.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
