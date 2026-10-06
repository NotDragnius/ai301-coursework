# Procedure: PR pre-check evaluation workflow

This document specifies the exact 4-stage evaluation procedure for `pr-precheck`.

## Stage 1: Read Order

1. **Issue & Plan Context**: Read reported problem and approved plan scope pair.
2. **Candidate PR Metadata**: Read PR title, description, and branch name.
3. **Git Diff**: Read exact file changes (`git diff main...HEAD`).
4. **Test Evidence**: Read before/after test outputs and repo check logs.

## Stage 2: Evidence Gathering

- Compare git diff hunks against `plan.md` scope (`silent drift`).
- Inspect file list in git diff for working notes, `plan.md`, or IDE debris (`unreviewable`).
- Verify before/after test output logs in description (`not tested`).
- Check PR template structure and AI disclosure line (`standards wall`).

## Stage 3: Check Execution

Grade each check in `rubric.md` as `pass` (`P`), `fail` (`F`), or `unclear` (`?`).

## Stage 4: Verdict Assembly

- Output `accept` if all required checks grade `pass`.
- Output `reject` if any required check grades `fail` or `unclear`.
