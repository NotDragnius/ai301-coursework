---
name: repro-check
description: Grade a draft claim comment and reproduction report against a written rubric and voice guide. Decide whether the reproduction package is ready to post upstream or should be held for revisions.
---

# repro-check: rubric-driven reproduction grading

You are grading a reproduction package (a claim comment, reproduction report, or full package bundle) for a GitHub issue to answer a single question: is this reproduction report complete, honest, reproducible, and ready to post upstream? You execute the rubric in `rubric.md` and the communication style in `voice-guide.md`, check by check, against the provided evidence.

## Inputs

One of:
- **Live mode**: a draft claim comment, draft reproduction report, or posted comment text for a candidate issue from the repo named in `scope.md`. Gather evidence from the draft text, local environment, and live issue thread.
- **Eval mode**: a reproduction package bundle (a markdown snapshot file containing the issue text, claim comment, reproduction report, and repo facts). Use ONLY the bundle text as evidence.

## Scope and Voice

In live mode, read `scope.md` and `voice-guide.md` in this skill directory. `scope.md` defines the scoped repository (`codepath/pathreview-ai301-fa26-s1`) and house rules (e.g. claim comments promise investigation, do not assert fixes, avoid piggybacking). `voice-guide.md` defines tone, disclosure requirements, and phrase conventions.

## Rubric Checks

Execute every check in `rubric.md`:
1. **Environment recorded**: Verifies OS, Python version, dependency state, and code commit/branch.
2. **Steps complete**: Verifies exact, copy-pasteable commands and setup steps.
3. **Behavior & outcome matching**: Verifies observed behavior is reported accurately against expected behavior (including honest non-reproduction reports).
4. **Honest reporting & non-assertion**: Ensures claims and repro reports promise investigation without prematurely asserting fixes.
5. **Voice & disclosure compliance**: Checks adherence to `voice-guide.md` rules and repo AI policies.

## Output Format

Emit a fenced JSON block as the final element of your output:

```json
{
  "item": "<package ID or issue URL>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear", "evidence": "<one line fact or quote>"}
  ],
  "verdict": "ready|hold"
}
```

Verdict is `ready` only if all required checks grade `pass`. Any `fail` or `unclear` yields `hold`.
