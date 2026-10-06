# Rubric: is this pull request ready to submit?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Plan fidelity & silent drift prevention | Git diff and `plan.md` scope pair | Fails if the diff contains unapproved scope additions or strays from `plan.md` without an explicit deviation note. Passes when the diff matches the approved plan scope or carries an honest recorded deviation note. | required |
| Test evidence & verification | `### Test Evidence` section in PR description | Fails if test evidence is missing, summarized without logs, or lacks observable before/after outputs. Passes when exact before/after `pytest` commands and passing test execution outputs are attached. | required |
| Clean diff & reviewability | File list in git diff | Fails if temporary working notes (`plan.md`), test logs, IDE configs, or debris are committed to the diff. Passes when the diff contains only clean, necessary code and test file edits. | required |
| Standards & disclosure compliance | PR description template and AI disclosure line | Fails if PR template sections are missing or if the AI-use disclosure statement is omitted. Passes when all required PR template headings and an explicit AI assistance disclosure statement are present. | required |

## Verdict rule

Verdict is `accept` if and only if all `required` checks grade `pass`. Any `required` check that grades `fail` or `unclear` causes the verdict to be `reject` (`unclear` is treated as `fail` / `reject`).
