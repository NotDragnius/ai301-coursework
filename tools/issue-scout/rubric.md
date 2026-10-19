# Rubric: is this a good first issue?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Active repository | Repository commits list, releases box, and `archived` status on GitHub | Fails if the repository is archived. Passes if the repository has a default-branch commit or official release within 90 days of today. Quiet repositories with recent push activity pass without requiring high-frequency issue replies. | required |
| scope-feasible | Issue body: the work it asks for | The issue describes one identifiable piece of work someone could start: a behavior, a gap, or a task you can point at. It fails only when there is no single piece of work in it: a codebase-wide checklist, an "improve X everywhere", or a container issue tracking many sub-tasks. An open design edge, an "etc.", or several files involved never fails this check; that raises the difficulty note instead. | required |
| Unclaimed status | Issue assignees, linked PRs in sidebar, and recent claim comments in thread | Passes if there is no assigned user, no open linked PR, and any existing claim comment has been inactive for 90+ days without maintainer confirmation. Fails if actively assigned, has an open linked PR, has an open PR mentioned in the thread, or carries a recent unresolved claim comment. | required |
| AI contribution policy | Repository `CONTRIBUTING.md`, dedicated AI policy files (`docs/AI_POLICY.md`), or adopted policies | Passes unless the project explicitly prohibits AI-assisted or AI-generated contributions (including policies adopted by reference or bans scoped to newcomer/good-first-issue labels). Disclosures, human verification requirements, or silence pass. | required |
| Newcomer friendly signal | Labels (`good-first-issue`, `help-wanted`, `beginner-friendly`) or maintainer invitation comments | Passes if a newcomer label or explicit maintainer invitation is present. | preferred |

## Difficulty note

With each accepted candidate, report a one-line difficulty note in the read-out summary:

- **straightforward**: the issue names where the change lives and the change is bounded.
- **moderate**: the location is yours to find, or several files are involved.
- **ambitious**: an open design edge, or an unfamiliar subsystem; name the edge, because claiming this issue means raising it with the maintainer early.

The note is information for the chooser, never a verdict input: it does not appear in the fenced JSON block, it never changes accept or reject, and in eval mode it is skipped entirely.

## Verdict rule

Accept if and only if all `required` checks grade `pass`. Any `required` check that grades `fail` or `unclear` causes the verdict to be `reject` (`unclear` is treated as `fail`). `preferred` checks never alter the verdict; they are reported and used solely alongside `scope.md` to rank accepted issues in live mode.

## Dated patch notes

- **2026-10-18**: Replaced the original strict scope check (`Scoped & bounded deliverable`) with `scope-feasible` and added the difficulty note section. In the sandbox, issues were artificially bounded, but real-world issues frequently contain open edges or multi-file traces. Scope now functions as an informative difficulty dial (straightforward / moderate / ambitious) rather than a blunt filter gate, while true umbrellas and architecture checklists still fail the floor.
