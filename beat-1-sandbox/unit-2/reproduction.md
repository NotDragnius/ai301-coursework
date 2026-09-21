# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

tabai

---

## Posted upstream

**Claim comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/69#issuecomment-2350111222

I am claiming this issue to investigate the top-level JSON array fallback crash in `rag/generator/output_parser.py`. I will set up a local environment on Windows 11 / Python 3.11, run the existing parser test suite, and follow up with a detailed reproduction report and stack trace.

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/69#issuecomment-2350222333

### Environment
- OS: Windows 11 Home (x86_64)
- Python: 3.11.9 (`venv`)
- Repository State: `codepath/pathreview-ai301-fa26-s1` at commit `a8f9c1b` (main branch)

### Reproduction Steps
1. Clone repository and set up virtual environment:
   ```bash
   git clone https://github.com/codepath/pathreview-ai301-fa26-s1.git
   cd pathreview-ai301-fa26-s1
   python -m venv venv
   source venv/Scripts/activate
   pip install -r requirements.txt
   ```
2. Execute the output parser test targeting top-level JSON array fallback:
   ```bash
   pytest tests/rag/test_output_parser.py -k "test_json_array_fallback"
   ```

### Observed Outcome
The test suite fails with an unhandled `TypeError` in `rag/generator/output_parser.py` at line 48:
```
FAILED tests/rag/test_output_parser.py::test_json_array_fallback - TypeError: string indices must be integers, not 'str'
Traceback (most recent call last):
  File "rag/generator/output_parser.py", line 48, in parse_fallback
    return [item["text"] for item in parsed_json]
TypeError: string indices must be integers, not 'str'
```
When LLM output produces a top-level array of strings `["item1", "item2"]` instead of dictionaries, indexing `item["text"]` raises a `TypeError`.

### Expected Outcome
The fallback parser should detect string elements within top-level JSON arrays and return a list of formatted response objects without raising a `TypeError`.

---

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

1. Initial draft run: 15/20 agreement. `Environment recorded` check failed packages that specified OS and Python versions but lacked commit hashes, while `Outcome evidenced` falsely passed packages with summarized text summaries.
2. Tightened `Environment recorded` to explicitly require commit/branch context, and updated `Outcome evidenced` to demand verbatim pytest/stack trace outputs. Re-ran disagreement set via `--only`: 4/5 matched.
3. Added `Voice & disclosure compliance` check to enforce `voice-guide.md` structure and catch missing AI disclosures when required by repository policies. Re-tested with `--only`: 5/5 matched.
4. Final full confirming run (`--save-run eval-run.txt`): 20/20 agreement (bar: 18/20: PASS).

**Package analysis**

`pkg-02`: Rubric verdict `hold`, matching the gold label (`hold`).
The contributor posted a reproduction comment stating "Reproduced on Windows, error confirmed," but provided no terminal output, pytest stack trace, or environment version specifics. My rubric's `Environment recorded` check graded `fail` due to vague environment details, and `Outcome evidenced` graded `fail` because no actual terminal traceback was attached. The gold rationale confirms that an un-evidenced reproduction report cannot be verified by maintainers and must be placed on hold until complete reproduction logs are attached.

**Check rationale**

Quoting `Environment recorded` (weight: required) from `rubric.md`:

> Fails if OS, Python version, or dependency/commit state is missing or vague ("on Linux"). Passes when exact OS, Python version, and commit/branch are explicitly listed.

This check ensures that maintainers and reviewers have exact system context to reproduce failures reliably. Vague environment reports ("on Windows") frequently obscure version-specific dependency bugs or OS path separator issues, so enforcing explicit versioning is essential before posting upstream.

**Trade-offs**

Requiring explicit commit hashes and full terminal tracebacks in `Environment recorded` and `Outcome evidenced` creates a strict threshold that flags incomplete draft reports as `hold`. While this prevents premature or low-quality posts from landing upstream, it requires contributors to run complete local executions before generating reports. This trade-off prioritizes report reliability and maintainer confidence over draft speed.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
