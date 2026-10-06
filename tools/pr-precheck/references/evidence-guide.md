# Evidence Guide: PR signals and failure category verification

## Signal Mapping Across Failure Categories

| Category | Check Name | Evidence Source |
|---|---|---|
| **silent drift** | Plan fidelity & silent drift prevention | Diff hunk comparison vs `plan.md` scope pair & PR description |
| **not tested** | Test evidence & verification | `### Test Evidence` block in PR description & `pytest` output logs |
| **unreviewable** | Clean diff & reviewability | Git diff file list (checking for `plan.md`, IDE files, debris) |
| **standards wall** | Standards & disclosure compliance | PR description template sections & AI assistance disclosure line |
