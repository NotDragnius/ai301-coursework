# Implementation Plan — Issue #69: JSON Array Fallback Crash

Path: `beat-1-sandbox/unit-3/plan.md`

## Problem Diagnosis

During fallback output parsing in `rag/generator/output_parser.py`, the function `parse_fallback()` assumes that top-level JSON arrays always contain dictionary objects with a `"text"` key (`return [item["text"] for item in parsed_json]`). When the LLM outputs a top-level array of raw strings (such as `["summary point 1", "summary point 2"]`), indexing `item["text"]` on string elements raises an unhandled `TypeError: string indices must be integers, not 'str'`.

This behavior was reproduced in Unit 2 via `pytest tests/rag/test_output_parser.py -k "test_json_array_fallback"`.

## Scope Pair

- **In Scope**:
  - Updating `parse_fallback()` in `rag/generator/output_parser.py` to safely handle top-level JSON arrays containing string elements or dictionaries.
  - Adding/verifying regression test coverage in `tests/rag/test_output_parser.py`.
- **Not In Scope**:
  - Modifying LLM prompt templates or generator configuration.
  - Refactoring unrelated output formatters or vector retrieval components.
  - Altering public API route schemas outside `output_parser.py`.

## Targeted Files & Areas

1. `rag/generator/output_parser.py`: `parse_fallback()` function (lines 40–55).
2. `tests/rag/test_output_parser.py`: Unit tests for fallback JSON array handling.

## Proposed Approach

1. Inspect elements in `parsed_json` within `parse_fallback()`:
   - If an element `item` is a `str`, wrap it directly into a response object dictionary `{"text": item}` (or return string list as expected by caller).
   - If `item` is a `dict`, safely extract `item.get("text", str(item))`.
   - Handle mixed array structures gracefully without raising `TypeError`.
2. Ensure non-array JSON fallbacks and dict responses retain their existing behavior.

## Test Plan

- **Before Execution**:
  ```bash
  pytest tests/rag/test_output_parser.py -k "test_json_array_fallback"
  # Observed Output: FAILED - TypeError: string indices must be integers, not 'str'
  ```
- **After Execution**:
  ```bash
  pytest tests/rag/test_output_parser.py -k "test_json_array_fallback"
  # Expected Output: 1 passed in 0.04s
  ```
- **Full Test Suite Verification**:
  ```bash
  pytest tests/rag/
  # Expected Output: all tests pass with zero regressions
  ```

## Risks & Unknowns

- **Risk**: Over-wrapping dictionary items if `isinstance(item, dict)` is not checked first.
- **Mitigation**: Add explicit type checking (`isinstance(item, str)` vs `isinstance(item, dict)`) and run the full `test_output_parser.py` suite.

## Deviations

nothing changed; the plan held
