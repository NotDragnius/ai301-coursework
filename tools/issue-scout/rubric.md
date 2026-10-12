# Rubric: is this a good first issue?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Active repository | Repository commits list, releases box, and `archived` status on GitHub | Fails if the repository is archived. Passes if the repository has a default-branch commit or official release within 90 days of today. Quiet repositories with recent push activity pass without requiring high-frequency issue replies. | required |
| Scoped & bounded deliverable | Issue body description and discussion thread | Passes if the issue describes one self-contained task for a single contributor in one PR — including terse descriptions, bug reports listing several potential root causes, or single fixes touching multiple files. Fails if it is an explicit multi-item tracking/umbrella issue, an unresolved architectural debate, a pure support request, a task requiring core framework refactoring, or an issue with 2+ previous abandoned/unmerged PR attempts. | required |
| Unclaimed status | Issue assignees, linked PRs in sidebar, and recent claim comments in thread | Passes if there is no assigned user, no open linked PR, and any existing claim comment has been inactive for 90+ days without maintainer confirmation. Fails if actively assigned, has an open linked PR, has an open PR mentioned in the thread, or carries a recent unresolved claim comment. | required |
| AI contribution policy | Repository `CONTRIBUTING.md`, dedicated AI policy files (`docs/AI_POLICY.md`), or adopted policies | Passes unless the project explicitly prohibits AI-assisted or AI-generated contributions (including policies adopted by reference or bans scoped to newcomer/good-first-issue labels). Disclosures, human verification requirements, or silence pass. | required |
| Newcomer friendly signal | Labels (`good-first-issue`, `help-wanted`, `beginner-friendly`) or maintainer invitation comments | Passes if a newcomer label or explicit maintainer invitation is present. | preferred |

## Verdict rule

Accept if and only if all `required` checks grade `pass`. Any `required` check that grades `fail` or `unclear` causes the verdict to be `reject` (`unclear` is treated as `fail`). `preferred` checks never alter the verdict; they are reported and used solely alongside `scope.md` to rank accepted issues in live mode.
