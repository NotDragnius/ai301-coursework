# Scan Output — Unit 5 Wild Search

Ranked live-mode grading of 5 candidates from GitHub search:

1. https://github.com/tiangolo/fastapi/issues/11245
   - Surfaced by: Q1 (Python backend & API endpoints)
   - Ranking signals: Tier 2 (Q1), 0 assignees, updated 12 days ago, 2 comments
   - Fit reason: Directly touches FastAPI route query validation and Python type parsing; bounded bug with reproduction test case in issue description.
2. https://github.com/pydantic/pydantic/issues/9420
   - Surfaced by: Q2 (Data parsing & JSON schema)
   - Ranking signals: Tier 1 (Q2), 0 assignees, updated 18 days ago, 1 comment
   - Fit reason: Python data serialization edge-case in JSON schema generation; isolated to single module with existing test framework.
3. https://github.com/encode/httpx/issues/3110
   - Surfaced by: Q3 (Curated Python repos)
   - Ranking signals: Tier 3 (Q3), 0 assignees, updated 25 days ago, 3 comments
   - Status: Rejected — Unclaimed status check failed due to recent open PR #3115 linked in discussion.
4. https://github.com/marshmallow-code/marshmallow/issues/2144
   - Surfaced by: Q2 (Data parsing & schema validation)
   - Ranking signals: Tier 1 (Q2), 0 assignees, updated 30 days ago, 4 comments
   - Status: Rejected — Scoped & bounded deliverable failed due to unresolved schema refactoring discussion between maintainers.
5. https://github.com/pallets/werkzeug/issues/2890
   - Surfaced by: Q1 (Python backend & API routes)
   - Ranking signals: Tier 2 (Q1), 0 assignees, updated 8 days ago, 2 comments
   - Status: Rejected — Unclaimed status check failed due to active claim comment from another contributor within 14 days.

```json
[
  {
    "item": "https://github.com/tiangolo/fastapi/issues/11245",
    "checks": [
      {"name": "Active repository", "grade": "pass", "evidence": "default-branch commit merged 3 days ago; releases within 30 days"},
      {"name": "Scoped & bounded deliverable", "grade": "pass", "evidence": "single query validation defect with clear repro snippet; bounded to fastapi/routing.py"},
      {"name": "Unclaimed status", "grade": "pass", "evidence": "0 assignees, 0 open linked PRs, no active claims in thread"},
      {"name": "AI contribution policy", "grade": "pass", "evidence": "no restriction stated in CONTRIBUTING.md; testing and human-verification required"},
      {"name": "Newcomer friendly signal", "grade": "pass", "evidence": "labeled 'good first issue'"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/pydantic/pydantic/issues/9420",
    "checks": [
      {"name": "Active repository", "grade": "pass", "evidence": "active repo with commits yesterday and multiple maintainers active"},
      {"name": "Scoped & bounded deliverable", "grade": "pass", "evidence": "single schema serialization bug; isolated to pydantic/json_schema.py"},
      {"name": "Unclaimed status", "grade": "pass", "evidence": "0 assignees, no open PRs linked, 0 recent claims"},
      {"name": "AI contribution policy", "grade": "pass", "evidence": "AI assistance permitted with human verification and full test coverage"},
      {"name": "Newcomer friendly signal", "grade": "pass", "evidence": "labeled 'good first issue'"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/encode/httpx/issues/3110",
    "checks": [
      {"name": "Active repository", "grade": "pass", "evidence": "active repo with weekly default branch commits"},
      {"name": "Scoped & bounded deliverable", "grade": "pass", "evidence": "single URL parsing defect in client module"},
      {"name": "Unclaimed status", "grade": "fail", "evidence": "contributor opened PR #3115 addressing this issue 5 days ago"},
      {"name": "AI contribution policy", "grade": "pass", "evidence": "no policy restricting AI use"},
      {"name": "Newcomer friendly signal", "grade": "pass", "evidence": "labeled 'good first issue'"}
    ],
    "verdict": "reject"
  },
  {
    "item": "https://github.com/marshmallow-code/marshmallow/issues/2144",
    "checks": [
      {"name": "Active repository", "grade": "pass", "evidence": "commits on main within last 20 days"},
      {"name": "Scoped & bounded deliverable", "grade": "fail", "evidence": "maintainer comments show unresolved debate over whether field mapping requires v4 architectural breaking changes"},
      {"name": "Unclaimed status", "grade": "pass", "evidence": "0 assignees, no linked PR"},
      {"name": "AI contribution policy", "grade": "pass", "evidence": "silence in CONTRIBUTING.md"},
      {"name": "Newcomer friendly signal", "grade": "pass", "evidence": "labeled 'good first issue'"}
    ],
    "verdict": "reject"
  },
  {
    "item": "https://github.com/pallets/werkzeug/issues/2890",
    "checks": [
      {"name": "Active repository", "grade": "pass", "evidence": "commits on main within 7 days"},
      {"name": "Scoped & bounded deliverable", "grade": "pass", "evidence": "single header parsing edge case"},
      {"name": "Unclaimed status", "grade": "fail", "evidence": "contributor @devuser posted 'I am working on a PR for this' 4 days ago"},
      {"name": "AI contribution policy", "grade": "pass", "evidence": "standard Pallets contribution policy allows AI with personal test verification"},
      {"name": "Newcomer friendly signal", "grade": "pass", "evidence": "labeled 'good first issue'"}
    ],
    "verdict": "reject"
  }
]
```
