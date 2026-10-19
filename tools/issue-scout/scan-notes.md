# Scan notes

One dated line per moment the wild surprised my tooling. Each line names the check or filter and quotes what confused it.

## Scan 1 (2026-10-11)

- 2026-10-11, setup: `gh auth status` verified the CLI was logged in, but on Windows, passing multiple search terms in quotes (`-- "term1 OR term2"`) resulted in quote escaping issues. Running them with explicit CLI arguments resolved the search queries.
- 2026-10-11, Q1: The query returned 80+ results, but several popular repos had issues labeled `good first issue` where an external contributor had already commented "Can I take this?" without a maintainer formally assigning them. My initial ranking filter 1 only dropped assigned issues (`assignees` count > 0), letting claimed issues into the top 5.
- 2026-10-11, ranking filter 4: `marshmallow#2144` made it into the top five because it had a `good first issue` label, but the thread discussion revealed maintainers were actively debating whether the fix required breaking changes for an upcoming major version. The filter couldn't see this from metadata alone; the rubric's `Scoped & bounded deliverable` check caught and rejected it.
- 2026-10-11, Active repository check: In the unit-1 sandbox, evidence was gathered from a static `Repo facts` block. In the wild on live GitHub, there is no preassembled facts block. The check had to be adapted to read the repository's default-branch commit recency and release dates directly from GitHub API/CLI outputs.
- 2026-10-11, Unclaimed status check, httpx#3110: The issue showed 0 assignees, but an open linked pull request was mentioned in the comment thread (`PR #3115`). The check correctly failed it, but highlighted that checking the `assignees` field alone on live GitHub is insufficient—linked PRs and thread claim comments must always be inspected.
- 2026-10-11, AI contribution policy, tiangolo/fastapi: CONTRIBUTING.md contains no standalone `AI_POLICY.md` file. It states standard guidelines requiring PRs to have tests and human-reviewed code. The rubric's policy check correctly identified that silence/standard test requirements constitute a pass.

## Patches after Scan 1 (2026-10-11)

Rubric:
- `Active repository`: Clarified evidence source to explicitly cite default-branch commits and releases box on GitHub rather than expecting a static sandbox facts block.
- `Unclaimed status`: Explicitly specified that pull requests mentioned in the thread count as active claims even if not formally linked via GitHub's development sidebar.

Strategy:
- `search-strategy.md`: Refined Query 2 and Query 3 search terms and added filter 8 (recency tie-break) to prefer older `updatedAt` within the 60-day window, avoiding threads recently bumped by fresh rival claim comments.

## Scan 2 — Claim Day (2026-10-18)

- 2026-10-18, rubric patch: Swapped my old scope check for `scope-feasible` and added difficulty notes (straightforward, moderate, ambitious). The old check made sense in the sandbox where issues were artificially bounded, but in the wild it was rejecting good issues just because the reporter listed several edge cases or an extra file. Scope works better now as a difficulty note while the floor still catches real umbrellas.
- 2026-10-18, difficulty notes: Marked `fastapi#11245` as straightforward because the problem is isolated right in `fastapi/routing.py`. Marked `pydantic#9420` as moderate because schema generation touches several model files.
- 2026-10-18, umbrella check: `marshmallow#2144` still failed `scope-feasible` because the discussion is really an open-ended checklist for an upcoming v4 rewrite, which belongs in multiple PRs.
- 2026-10-18, choosing the issue: Picked `fastapi#11245` over `pydantic#9420`. Both passed every check, but FastAPI's route query validation is a cleaner fit for my Python backend focus and already has a short script to reproduce it.


