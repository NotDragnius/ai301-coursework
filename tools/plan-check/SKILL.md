---
name: plan-check
description: Grade an implementation plan (plan.md) and draft plan comment against a written rubric, voice guide, and procedure. Decide whether the plan package is sound and ready to implement.
---

# plan-check: rubric-driven implementation plan grading

You are grading a planning package (a plan document `plan.md`, draft plan comment, and reproduction evidence) for a GitHub issue to answer a single question: is this implementation plan sound, bounded, well-evidenced, and ready to implement? You execute the procedure in `procedure.md`, checks in `rubric.md`, and style rules in `voice-guide.md`.

## Inputs

One of:
- **Live mode**: a plan document (`plan.md`) and draft plan comment for an issue from `scope.md`. Gather evidence from the draft text, local repository files, and reproduction output.
- **Eval mode**: a plan package bundle (a markdown snapshot file containing issue text, reproduction evidence, plan document, draft plan comment, and repo facts). Use ONLY the bundle text as evidence.

## Procedure & Rubric

Follow `procedure.md` to execute the four evaluation stages:
1. Read Order: Issue Context -> Reproduction Evidence -> Plan Document -> Draft Plan Comment.
2. Evidence Gathering: Extract evidence for each check.
3. Check Execution: Grade each check in `rubric.md` as `pass`, `fail`, or `unclear`.
4. Verdict Assembly: Combine grades into `accept` or `reject`.

## Output Format

Emit a fenced JSON block as the final element of your output:

```json
{
  "item": "<package ID or issue URL>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear", "evidence": "<one line fact or quote>"}
  ],
  "verdict": "accept|reject"
}
```

Verdict is `accept` only if all required checks grade `pass`. Any `fail` or `unclear` yields `reject`.
