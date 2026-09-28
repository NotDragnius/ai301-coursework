# Evidence Guide: implementation plan signals and verification locations

Every rubric check needs a verifiable evidence source. This guide maps key plan quality signals to concrete locations on GitHub (for live mode review) and within snapshot bundles (for eval mode).

## Signal Mapping

| Check Name | Live Mode Evidence Source | Eval Bundle Evidence Source |
|---|---|---|
| Diagnosis follows from repro | `plan.md` Diagnosis section citing repro terminal output | `## Diagnosis` block vs Repro Evidence block in bundle |
| Bounded scope pair | `plan.md` Scope Pair section (`In Scope` / `Not In Scope`) | `## Scope Pair` section in `plan.md` |
| Actionable execution steps | `plan.md` Proposed Approach & Targeted Files sections | `## Proposed Approach` section in bundle |
| Observable test plan | `plan.md` Test Plan section (`Before` & `After` commands) | `## Test Plan` code block in bundle |
| Honest risks & unknowns | `plan.md` Risks & Unknowns section | `## Risks & Unknowns` section in bundle |
| Voice & thread compliance | Draft plan comment text and repo `CONTRIBUTING.md` / AI policies | Draft plan comment text vs Repo facts policy line |
