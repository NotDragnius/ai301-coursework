# Contribution: Route query parameter validation defect in FastAPI

Path: `beat-2-contribution/contribution-story.md`

This file is Assignment 5, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. **Keep every section header below under its exact name** — the
format criteria grade exactly that. Your course repo link is the whole submission: no tool
files and no evidence uploads are part of Assignment 5.

**Contribution Number:** [1]
**Student:** Tabai
**GitHub Username:** NotDragnius
**Issue:** https://github.com/tiangolo/fastapi/issues/11245
**Pull Request:** [GitHub PR link, once opened]

One repository, built across units 5 to 8, telling the whole story of your real
contribution. Fill it as you work, not at the end — the sections below ask for evidence that
is far easier to write down as it happens than to reconstruct in the last weekend.

Contribution Number stays `[1]` unless you make more than one contribution this term; it
just numbers them.

---

## Toolkit

Every story section below, from Why I Chose This Issue through Pull
Request, ends with a Toolkit block: which tool did that phase's work
and how you used it, what it produced, what difficulties or
shortcomings it presented, and what you changed or would change
because of them. Together the blocks are the thread the rubric's
Toolkit points read, and they are the raw material for your unit-9
portfolio, so keep them current as you work rather than
reconstructing them later.

A Toolkit block looks like this (copy it into each story section and
fill it there):

```text
**Toolkit**

- Tool: [which tool did this phase's work, and how you used it]
- What it produced: [described in a sentence or a short excerpt]
- Difficulties: [what fought you or fell short, or "none met"]
- What changed: [the patch, revision, or workaround, what you would
  update, or "nothing"]
```

This section also keeps one short dated entry per week of tool work,
starting below: what you built or changed that week, what broke, and
what you changed because of it. The blocks tell the story where it
happened; these entries are the toolkit's own timeline.

All four entries are graded. Keep every heading below, and fill each
one in the week it belongs to.

**Unit 5: Built issue-scout and ran first wild scans**

2026-10-11: I adapted the Unit 1 issue-select skill into issue-scout, preserving my core evaluation rubric and evidence guide while adding an autonomous GitHub issue-discovery pipeline. I authored a search strategy targeting Python backend logic, API endpoints, and data/JSON parsing libraries (FastAPI, Pydantic, HTTPX). The scout scanned and graded 5 candidates, accepting two (FastAPI and Pydantic) and rejecting three due to unresolved architectural debates and active claims in comment threads. I patched my rubric to clarify live maintainer commit evidence sources and updated ranking filters to prioritize threads without recent rival claim activity.

**Unit 6: Installed the voice-guard and drafted my claim for FastAPI**

2026-10-18: I set up the voice-guard hook on my outgoing comments and merged my earlier voice guides into one canonical file at `~/.claude/voice-guard/voice-guide.md`. I added upstream rules for claims, questions, and pings, each with a wrong/right example from how I actually write. The guard stopped my first claim draft because I promised a quick fix before testing it locally, so I rewrote it to focus strictly on reproducing the behavior first. On Windows, symlinks between skill folders created separate file copies, so I used pointer lines in repro-check, plan-check, and pr-precheck to make sure all tools read the same guide. I also set up `CLAUDE.local.md` for FastAPI with its test commands and routing subsystem notes, kept it under 60 lines, and added it to `.git/info/exclude`.

**Unit 7: [one line on the tool work]**

[2-4 sentences: the ship-gate and your gate manifest. What it produced
on your real branch, what fought you, what changed because of it.]

**Unit 8: [one line on the tool work]**

[2-4 sentences: the PR-monitor and your playbook. What it read, what it
drafted, what you did with the draft.]

---

## Why I Chose This Issue

I picked an issue in FastAPI around query parameter parsing in `fastapi/routing.py` (`https://github.com/tiangolo/fastapi/issues/11245`). When certain query parameter combinations with defaults are passed into a route handler, FastAPI throws unexpected validation errors instead of properly converting them into the expected parameter types. The reporter included a clear reproduction script that triggers the failure on clean Python 3.12 installs, and the whole bug is isolated to route dependency resolution without needing databases or external network services.

My scan on 2026-10-18 evaluated five issues using the patched rubric with `scope-feasible` and difficulty notes. It accepted two candidates: this FastAPI issue with a straightforward difficulty note, and a Pydantic schema serialization issue with a moderate difficulty note. I chose the FastAPI issue because it sits right where I want to focus my coursework—Python backend routing, request validation, and parameter handling. I want to learn how FastAPI connects route declarations with Pydantic's internal validators, and how maintainers test and review changes to core routing logic.

The scout held up well during this run. Swapping my old scope check for `scope-feasible` stopped the scout from rejecting good issues just because the writeup described multiple parameter combinations, and correctly labeled this one straightforward because the logic lives in `fastapi/routing.py`. At the same time, the floor check still caught and rejected marshmallow#2144 (which turned out to be an open-ended discussion about a v4 refactor), while the unclaimed check rejected httpx#3110 and werkzeug#2890 because other contributors were already working on them.

Claim comment: `claim pending (2026-10-18)` — drafted in `claim-draft.md`, verified through `check_voice.py`, and ready to post:
> "I would like to work on reproducing and resolving this issue. My first step is setting up an isolated test case in `tests/test_query_params.py` to reproduce the query parameter validation behavior in `fastapi/routing.py` on Python 3.12. I will follow up here with a reproduction report and environment details once verified against the existing test suite."

**Toolkit**

- Tool: issue-scout with patched rubric (`scope-feasible` and difficulty notes), run in live scan mode.
- What it produced: Scan 2 accepted FastAPI #11245 with a straightforward difficulty note, confirming recent commits within 3 days, zero assignees, zero open PRs, and bounded logic in `fastapi/routing.py`.
- Difficulties: In earlier scans, the old scope check was too rigid and failed real bug reports that mentioned multiple edge cases. Shifting scope from a binary gate to a difficulty note fixed that without letting big umbrella issues through.
- What changed: Replaced the scope check with `scope-feasible`, added the difficulty note section, and added tie-break ranking filters to skip threads bumped by recent claim comments.

---

## Understanding the Issue

**Problem Description**

[In your own words, what is broken or missing?]

**Expected Behavior**

[What should happen?]

**Current Behavior**

[What actually happens?]

**Affected Components**

[Which parts of the codebase are involved?]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Reproduction Process

**Environment Setup**

[What a stranger would need to stand this up: your operating system,
the relevant versions (language, runtime, package manager, the project
itself), and how you set the project up. Then the challenges you faced
and how you solved them, or that none came up.]

**Steps to Reproduce**

1. [Step 1]
2. [Step 2]
3. [Observed result]

**Reproduction Evidence**

- **Commit showing reproduction:** [link to commit in your fork]
- **Screenshots/logs:** [if applicable]
- **My findings:** [what you discovered during reproduction; an
  honest, evidenced cannot-reproduce that led you to re-pick or ask
  the maintainer belongs here and costs you nothing]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Solution Approach

**Analysis**

[Your analysis of the root cause: what is causing the issue, traced
to the files and functions involved.]

**Proposed Solution**

[High-level description of your fix approach, and what you are
deliberately NOT changing.]

**Implementation Plan**

1. [Modify file X to do Y]
2. [Add or change Z]
3. [Update tests]

[Record deviations here as they happen: what changed mid-build and
why. A recorded deviation is honest work; silent drift is not.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Testing Strategy

[What observable checks prove the fix: your reproduction steps re-run
against the built change (before and after), and the repo's own test
suite or checks with the outcome shown. "Tests pass" with nothing
observable named is not a strategy.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Implementation Notes

[A running log, added to as you work. Date each entry. What you
built, decisions you made when you made them, wrong turns included.]

**[Date]**

[Entry]

**[Date]**

[Entry]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Pull Request

**PR Link:** [GitHub PR URL when opened]

**PR Description:** [what the PR says; much of the content above
adapts into it]

**Maintainer Feedback:**

- [Date]: [feedback received, or "none yet"; silence is a normal
  state and costs you nothing]
- [Date]: [how you addressed it]

**Status:** [Awaiting review / Iterating / Merged / Closed. The
status is a fact you record, never a grade: the PR is graded as
opened.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Learnings and Reflections

**Technical Skills Gained**

[What you learned technically, named concretely.]

**Challenges Overcome**

[What was hard and how you solved it; point at the real events, the
Toolkit blocks above are full of them.]

**What I'd Do Differently Next Time**

[Reflection on your process.]

---

## Resources Used

[What actually helped, not a reading list. List things this story
already shows you using: the doc you followed to set the environment
up, the thread that explained the bug, the person who answered you.
One real entry beats ten plausible ones.]

- [Link to documentation that helped]
- [Discussion, issue, or post that helped]
