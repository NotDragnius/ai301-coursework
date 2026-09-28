# Rubric: is this implementation plan sound and ready to build?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Diagnosis follows from repro | `## Problem Diagnosis` section in `plan.md` | Fails if the diagnosis contradicts or ignores the reproduction stack trace/evidence. Passes when the diagnosis directly cites the failure mechanism from the reproduction evidence. | required |
| Bounded scope pair | `## Scope Pair` section in `plan.md` | Fails if `Not In Scope` is omitted, vague, or if `In Scope` includes unrelated features/refactoring. Passes when both `In Scope` and `Not In Scope` boundaries are explicitly stated. | required |
| Actionable execution steps | `## Targeted Files & Areas` and `## Proposed Approach` sections | Fails if steps are vague ("fix the code") or touch unlisted core architecture. Passes when targeted file paths are listed and implementation steps are concrete and runnable. | required |
| Observable test plan | `## Test Plan` section in `plan.md` | Fails if test commands are omitted or expected-after outcomes are not specified. Passes when exact command lines (before and after) and observable pass criteria are provided. | required |
| Honest risks & unknowns | `## Risks & Unknowns` section in `plan.md` | Fails if risks/unknowns are omitted or brushed off ("no risks"). Passes when potential edge cases, side effects, or technical unknowns are explicitly addressed. | required |
| Voice & thread compliance | Draft plan comment text and repo facts policy line | Fails if plan comment asserts completion, uses generic summaries, or violates `voice-guide.md` structure. Passes when voice guidelines and repo conventions are followed. | required |

## Verdict rule

Verdict is `accept` if and only if all `required` checks grade `pass`. Any `required` check that grades `fail` or `unclear` causes the verdict to be `reject` (`unclear` is treated as `fail` / `reject`).
