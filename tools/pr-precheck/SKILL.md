---
name: pr-precheck
description: Grade a candidate pull request draft and diff against a written rubric, voice guide, procedure, and contract. Decide whether the PR is ready to submit.
---

# pr-precheck: rubric-driven pull request pre-check grading

You are grading a pull request package (PR title, description, git diff, test evidence, and plan context) to answer a single question: is this pull request clean, well-tested, faithful to the plan, disclosed, and ready to submit? You execute the contract in `CONTRACT.md`, procedure in `procedure.md`, checks in `rubric.md`, and rules in `voice-guide.md`.

## Inputs

One of:
- **Live mode**: a candidate PR draft (`pr_draft.md`), git diff (`git diff main...HEAD`), test evidence (`test_evidence.md`), and plan (`plan.md`).
- **Eval mode**: a PR package bundle (a markdown snapshot file containing issue context, plan context, candidate PR draft, commits, diff, and test evidence).

## Procedure & Rubric

Follow `procedure.md` to execute the four evaluation stages and grade the 4 core failure categories in `rubric.md`.

## Output Format

Emit a fenced JSON block as the final element of your output:

```json
{
  "item": "<package ID or PR URL>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear", "evidence": "<one line fact or quote>"}
  ],
  "verdict": "accept|reject"
}
```

Verdict is `accept` only if all required checks grade `pass`. Any `fail` or `unclear` yields `reject`.
