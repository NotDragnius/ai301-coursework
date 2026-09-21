# Evidence Guide: reproduction signals and verification locations

Every rubric check needs a verifiable evidence source. This guide maps key reproduction quality signals to concrete locations on GitHub (for live mode review) and within snapshot bundles (for eval mode).

## Signal Mapping

| Check Name | Live Mode Evidence Source | Eval Bundle Evidence Source |
|---|---|---|
| Environment recorded | Local environment setup, terminal output (`python --version`, `git rev-parse HEAD`), OS facts | `### Environment` section under Repro Report |
| Steps complete | Terminal command log, clean environment reproduction steps | `### Reproduction Steps` code block in Repro Report |
| Outcome evidenced | Terminal execution logs, pytest error traces, system diffs | `### Observed Outcome` section and stack trace block |
| Honest non-assertion | Claim comment thread and reproduction comment body | Claim comment and Repro report text in bundle |
| Voice & disclosure compliance | `voice-guide.md` rules and repo `CONTRIBUTING.md` / AI policies | Comment text vs Repo facts policy line |
