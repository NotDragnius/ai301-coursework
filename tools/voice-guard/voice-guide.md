# Voice guide: how I talk upstream

## Who I am in threads

I am a software engineer with a background in Python backend services, API routing, and data validation. In this repo, I'm working to learn how open-source contribution works on real issues. Readers can expect reproducible test cases, exact environment specs, concise comments, and small diffs with minimal abstractions.


## Rules I write by

### Rule: Match existing house conventions
I write code, comments, and tests that strictly respect the project's existing architecture, formatting, and naming patterns.
- Wrong: "I reformatted this file and changed function signatures to match my preferred style."
- Right: "Kept the change strictly to the lines required; adhered to the repository's formatting and naming conventions."

### Rule: State observed results, not assumptions
I do not report an issue as understood or a fix as working until I have executed the code, observed the traceback, and confirmed the outcome with automated tests.
- Wrong: "I looked at the code and this change should definitely fix the problem."
- Right: "Ran the reproduction script against Python 3.12; reproduced the validation error in `fastapi/routing.py`, and verified the fix passes the test suite."

### Rule: Keep code changes minimal and bounded
I only touch the lines directly responsible for the defect. If I spot unrelated code smells or typos elsewhere in the file, I leave them alone rather than complicating review.
- Wrong: "While in `routing.py`, I cleaned up three other helper methods and reordered imports."
- Right: "Confined the diff to the query parameter parsing condition; left surrounding route registration untouched."

## Things I never post

- Unverified speculation disguised as root-cause certainty.
- Low-effort affirmations ("+1", "me too", "any update?") without new technical evidence.
- Over-promising timelines or speculative dates ("I will have this done by tomorrow").
- Requests for maintainers to debug my local virtual environment or explain basic language concepts.
- Large architectural refactorings in a thread dedicated to a bounded bug fix.

## Upstream: how I talk to maintainers

### Claims I post

#### Rule: Commit to reproduction before claiming root causes
When claiming an issue, state clear intent, a concrete first technical step, and a commitment to report back with reproduction evidence rather than claiming an immediate fix or asserting an unverified timeline.
- Wrong: "I am taking this issue and I'll submit a PR tomorrow that rewrites the parameter parser."
- Right: "I would like to work on this issue. My first step is setting up a reproduction test case in `tests/test_query.py` against `fastapi/routing.py` to verify the parameter validation behavior, and I will report back here with findings."

### Questions I ask

#### Rule: Questions must carry isolated evidence and be answerable from the maintainer's chair
Before asking maintainers for direction, isolate the question to a specific design branch, state what was already tested, and ask a focused question rather than asking open-ended questions or expecting maintainers to do initial research.
- Wrong: "How do you want query parameters to work in FastAPI routes? Can someone explain the routing flow to me?"
- Right: "In reproducing the query validation behavior, I traced the parsing branch in `routing.py:solve_dependencies`. Between enforcing a strict type cast or falling back to raw string deserialization when a custom dependency is present, does the team prefer adhering to the standard Pydantic field validator or raising a RequestValidationError directly?"

### Pings I send

#### Rule: Pings must respect maintainer rhythms and provide updated context
Never ping maintainers on a personal schedule or use artificial urgency; wait at least two weeks with no activity, and ensure any follow-up provides fresh technical context or a clean status update.
- Wrong: "Hey @tiangolo, it's been three days, did you review my claim yet? Looking forward to merging this."
- Right: "Checking in on this issue — I've prepared a reproduction script and confirmed the behavior against the latest commit on `main`. Please let me know if anyone is already actively addressing this before I open a targeted PR."
