# Contract: PR Pre-Check Tool Specification

This document defines the interface contract that the `pr-precheck` tool must satisfy.

## Modes & Inputs

1. **Live Mode**: Reads a candidate pull request draft (title, description, diff relative to default branch, test evidence) against the live repository defined in `scope.md`.
2. **Eval Mode**: Reads snapshot package bundles from the evaluation suite (`pkg-01.md` through `pkg-20.md`).

## Swappable Components

- `scope.md`: Specifies the target repository (`codepath/pathreview-ai301-fa26-s1`).
- `voice-guide.md`: Specifies required PR title formats, description template sections, and AI disclosure requirements.

## Failure Categories Evaluated

1. **silent drift** (plan fidelity): Diff matches the posted plan or carries an honest deviation note.
2. **not tested** (test evidence): Evidence shows observable before/after outputs and repo checks were run.
3. **unreviewable** (diff quality): Diff is free of debris (no working notes, `plan.md`, or unrelated edits).
4. **standards wall** (standards & comms): Required repo template sections and AI-assisted disclosures are present.

## Verdict Output

- `accept`: All required checks grade `pass`.
- `reject`: One or more required checks grade `fail` or `unclear`.
