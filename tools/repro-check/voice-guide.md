# Voice Guide: upstream communication rules

## Tone and Style

- **Professional and concise**: State environment facts, execution steps, and observed error tracebacks clearly without filler.
- **Evidence-first**: Lead with environment details (OS, Python version, commit hash) and exact command line invocation rather than narrative descriptions.
- **Constructive & respectful**: Use neutral technical phrasing ("Observed behavior:", "Expected behavior:", "Steps to reproduce:").

## Required Phrasing & Patterns

- **Claim comments**: Must use active forward-looking language: "I am working to reproduce this issue on [OS/Python version]. I will test [specific module/path] and follow up with a reproduction report."
- **Reproduction reports**: Must include structured headings:
  - `### Environment`
  - `### Reproduction Steps`
  - `### Observed Outcome`
  - `### Expected Outcome`

## Forbidden Patterns

- Do not assert root causes or fixes in claim comments before testing ("I will fix this by changing line 42").
- Do not post low-effort affirmations ("+1", "me too", "same here").
- Do not omit environment specifications or rely on vague descriptions ("on Windows", "latest version").
