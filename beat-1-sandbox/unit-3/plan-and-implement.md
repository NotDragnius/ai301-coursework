# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

Record of your plan, the branch you built it on, and the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in the
repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Posted upstream

**GitHub username**

tabai

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/69#issuecomment-2361001122

### Diagnosis
During fallback output parsing in `rag/generator/output_parser.py`, `parse_fallback()` assumes top-level JSON arrays contain dictionaries with a `"text"` key (`item["text"]`). When top-level arrays contain string elements, indexing `item["text"]` causes an unhandled `TypeError: string indices must be integers, not 'str'`.

### Scope Pair
- **In Scope**: Type checking array elements in `parse_fallback()` to handle string elements and dictionaries safely, and adding unit test coverage in `tests/rag/test_output_parser.py`.
- **Not In Scope**: Prompt template modifications, vector store schema changes, or refactoring unrelated generator routes.

### Proposed Approach
Update `parse_fallback()` in `rag/generator/output_parser.py` to inspect element types during array iteration. If an item is a string, format it directly; if a dictionary, extract `item.get("text", str(item))`.

### Test Plan
- Re-run `pytest tests/rag/test_output_parser.py -k "test_json_array_fallback"` (Verify failure before, 1 passed after).

---

## Your branch

**Branch**

fix/69-json-array-fallback

**Evidence**

Before (Unit 2 Reproduction Baseline):
```
$ pytest tests/rag/test_output_parser.py -k "test_json_array_fallback"
============================= FAILURES =============================
_____________________ test_json_array_fallback _____________________
    def test_json_array_fallback():
>       res = parse_fallback('["summary point 1", "summary point 2"]')
rag/generator/output_parser.py:48: in parse_fallback
    return [item["text"] for item in parsed_json]
E   TypeError: string indices must be integers, not 'str'
========================= 1 failed in 0.05s =========================
```

After (Built Change Verification):
```
$ pytest tests/rag/test_output_parser.py -k "test_json_array_fallback"
============================== PASSES ==============================
tests/rag/test_output_parser.py::test_json_array_fallback PASSED   [100%]
========================= 1 passed in 0.04s =========================
```

---

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

1. Initial run: 14/20 agreement. `Diagnosis follows from repro` failed plans with generic root cause statements, while `Bounded scope pair` rejected plans that listed `In Scope` items without an explicit `Not In Scope` block.
2. Updated `Bounded scope pair` to mandate explicit `Not In Scope` exclusions, and updated `Diagnosis follows from repro` to require explicit citation of the reproduction error type. Re-ran disagreement set via `--only`: 4/5 matched.
3. Refined `Procedure` in `procedure.md` to establish a strict 4-stage evaluation order (Issue Context -> Repro Evidence -> Plan -> Comment). Re-tested `--only` set: 5/5 matched.
4. Final full confirming run (`--save-run eval-run.txt`): 20/20 agreement (bar: 18/20: PASS).

**Package analysis**

`pkg-04`: Rubric verdict `accept`, matching the gold label (`accept`).
The plan document clearly identifies the root cause from the reproduction stack trace, specifies targeted files (`rag/generator/output_parser.py`), includes an explicit scope pair distinguishing parser logic from prompt template changes, and provides before/after `pytest` execution commands. My rubric graded all required checks as `pass`, aligning perfectly with the gold `accept` verdict.

**Check rationale**

Quoting `Diagnosis follows from repro` (weight: required) from `rubric.md`:

> Fails if the diagnosis contradicts or ignores the reproduction stack trace/evidence. Passes when the diagnosis directly cites the failure mechanism from the reproduction evidence.

This check ensures that proposed fixes are grounded in actual empirical evidence rather than speculative guesses. Grounding the diagnosis in the verified Unit 2 stack trace prevents scope creep and ensures the plan directly addresses the underlying defect.

**Trade-offs**

Enforcing strict scope pair definitions (`In Scope` and `Not In Scope`) and explicit stack trace citations in `Diagnosis follows from repro` creates a higher initial barrier for draft plans. However, this strictness prevents contributors from embarking on unbounded refactoring or addressing unverified symptoms, ensuring maintainer approval and smooth PR review in Unit 4.

---

Related paths: `plan.md` and `eval-run.txt` in this directory; your skill's files in
`tools/plan-check/`.
