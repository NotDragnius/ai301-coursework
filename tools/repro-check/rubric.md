# Rubric: is this reproduction package ready to post?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Environment recorded | `### Environment` section in reproduction report or draft | Fails if OS, Python version, or dependency/commit state is missing or vague ("on Linux"). Passes when exact OS, Python version, and commit/branch are explicitly listed. | required |
| Steps complete | `### Reproduction Steps` section in report or draft | Fails if steps rely on unstated assumptions, missing files, or vague commands ("run the script"). Passes when steps provide copy-pasteable, self-contained shell/python commands. | required |
| Outcome evidenced | `### Observed Outcome` section and stack trace/output | Fails if the observed behavior is summarized without actual output/error logs, or if expected vs observed results are omitted. Passes when exact terminal output, pytest failures, or stack traces are provided. | required |
| Honest non-assertion | Claim comment and reproduction report body | Fails if claim comment asserts a pre-determined fix before testing, or if repro report claims success without running code. Passes when claims state intent to investigate and repro reports state observed facts truthfully. | required |
| Voice & disclosure compliance | Comment text and `contribution policy` in repo facts | Fails if comments contain piggybacking ("+1"), violate `voice-guide.md` structure, or omit required AI disclosures when mandated by repo policy. Passes when voice guidelines and repo AI policies are respected. | required |

## Verdict rule

Verdict is `ready` if and only if all `required` checks grade `pass`. Any `required` check that grades `fail` or `unclear` causes the verdict to be `hold` (`unclear` is treated as `fail` / `hold`).
