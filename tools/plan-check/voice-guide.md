# Voice Guide: upstream communication rules for planning

## Tone and Style

- **Technical and precise**: State diagnosis details, specific code paths, and targeted file changes without generic summaries.
- **Evidence-grounded**: Root every diagnosis directly in the reproduction evidence and stack trace obtained in Unit 2.
- **Bounded and honest**: Clearly state boundaries (`In Scope` vs `Not In Scope`) and flag any technical unknowns.

## Required Phrasing & Patterns

- **Plan comments**: Must structure information clearly under standard headers:
  - `### Diagnosis`
  - `### Scope Pair`
  - `### Proposed Approach`
  - `### Test Plan`

## Forbidden Patterns

- Do not include vague promises ("I will fix the bug"). Name exact functions and file paths.
- Do not propose out-of-scope architectural refactoring or unrelated feature additions.
- Do not assert completion before building or running tests.
