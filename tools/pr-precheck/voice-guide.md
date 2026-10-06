# Voice Guide: pull request communication guidelines

## Required PR Description Structure

Pull request descriptions must adhere to the repository template structure:

- `### Summary`: Concise overview of the fix and the problem addressed.
- `### Related Issue`: Reference to the fixed issue (`Fixes #<issue-number>`).
- `### Proposed Changes`: Bulleted list describing specific code edits made in the diff.
- `### Test Evidence`: Verbatim before/after test execution results.
- `### AI Assistance Disclosure`: Explicit statement disclosing AI coding assistance, human review, and local test verification.

## Tone & Style Rules

- **Clear and professional**: Describe actual changes in the diff without exaggeration.
- **No unreviewed promises**: Do not claim features or fixes not contained in the diff.
- **Explicit disclosure**: State clearly how AI tools were used during development.
