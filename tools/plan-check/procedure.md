# Procedure: plan execution and evaluation workflow

This document specifies the exact 4-stage procedure that the `plan-check` skill follows when evaluating a planning package.

## Stage 1: Read Order

Read package elements strictly in this sequence:
1. **Issue Context**: Understand the reported bug or feature request.
2. **Reproduction Evidence**: Review the verified terminal traceback, environment facts, and failing test logs from Unit 2.
3. **Plan Document (`plan.md`)**: Read the proposed diagnosis, scope pair, targeted files, approach, test plan, and risks.
4. **Draft Plan Comment**: Read the comment text intended for posting upstream.

## Stage 2: Evidence Gathering

For each check defined in `rubric.md`, extract exact supporting lines or facts:
- Extract the root cause stated in the plan and compare it against the reproduction stack trace.
- Identify the explicit `In Scope` and `Not In Scope` boundaries.
- Verify targeted files exist and match the reproduction failure location.
- Confirm test plan specifies exact re-run commands and expected post-fix outcomes.

## Stage 3: Check Execution

Grade each check in `rubric.md` as `pass` (`P`), `fail` (`F`), or `unclear` (`?`):
- `pass`: Evidence explicitly satisfies the pass condition.
- `fail`: Evidence visibly violates the pass condition or is inadequate.
- `unclear`: Required evidence is absent from the bundle (treated as `fail`).

## Stage 4: Verdict Assembly

Apply the verdict rule from `rubric.md`:
- Verdict is `accept` if and only if **all required checks** grade `pass`.
- Verdict is `reject` if any required check grades `fail` or `unclear`.
