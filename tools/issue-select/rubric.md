# Rubric: is this a good first issue?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Active repository | `archived:` flag and `last push to any branch` date in the Repo facts block | Fails if `archived: yes`. Passes if the last push date is within 90 days of the capture date. A quiet repository with recent activity passes without needing a high-frequency response sample. | required |
| Scoped & bounded deliverable | The issue body and comment thread | Passes if the issue describes one self-contained task for a single contributor in one PR — including terse descriptions, bug reports listing several potential root causes, or single fixes touching multiple files. Fails if it is an explicit multi-item tracking/umbrella issue, an unresolved product debate, a pure support request, a task requiring core framework refactoring, or an issue with 2+ previous abandoned/unmerged PR attempts. | required |
| Unclaimed status | `assignees`, `linked PRs`, and claim comments in the issue thread | Passes if there is no assigned user, no open linked PR, and any existing claim comment has been inactive for 90+ days. Fails if actively assigned, has an open linked PR, or carries a recent unresolved claim comment. | required |
| AI contribution policy | `contribution policy` line in Repo facts (`CONTRIBUTING.md` / AI guidelines) | Passes unless the project explicitly prohibits AI-assisted or AI-generated contributions. Disclosures, human verification requirements, or silence pass. | required |
| Newcomer friendly signal | Labels (`good-first-issue`, `help-wanted`) or maintainer comments in the thread | Passes if a newcomer label or explicit maintainer invitation is present. | preferred |

## Verdict rule

Accept if and only if all `required` checks grade `pass`. Any `required` check that grades `fail` or `unclear` causes the verdict to be `reject` (`unclear` is treated as `fail`). `preferred` checks never alter the verdict; they are reported and used solely alongside `scope.md` to rank accepted issues in live mode.
