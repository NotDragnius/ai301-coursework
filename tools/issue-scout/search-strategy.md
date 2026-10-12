# Search strategy: where your scout looks, and why

## Queries

Q1, Python backend and API endpoints. Traces to fit-profile sentence: "I am looking for beginner-friendly tasks that touch Python backend logic, API endpoints, or data parsing (such as JSON/LLM output handling)." Targets popular Python backend frameworks and libraries known for structured first issues.

```
gh search issues --label "good first issue" --language Python --state open --sort updated --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url -- "backend OR api OR endpoint OR route"
```

Q2, Data parsing, JSON schemas, and LLM output parsing. Traces to fit-profile sentence: "I am looking for beginner-friendly tasks that touch Python backend logic, API endpoints, or data parsing (such as JSON/LLM output handling)." Focuses on data parsing, structured outputs, serialization, and RAG/LLM output handling tools.

```
gh search issues --label "good first issue" --language Python --state open --sort updated --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url -- "json OR parser OR parsing OR schema"
```

Q3, Targeted Python AI/ML ecosystem repositories. Traces to fit-profile sentence: "I am a computer science student comfortable with Python, backend development, and basic AI/ML workflows." Searches vetted open-source AI developer tools and data libraries that offer newcomer-friendly issues.

```
gh search issues --label "good first issue" --repo pydantic/pydantic --repo tiangolo/fastapi --repo encode/httpx --repo pallets/flask --repo psf/requests --state open --sort updated --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url
```

Q4, Alternative newcomer label for Python backend projects. Traces to fit-profile sentence: "I prefer issues with pre-existing failing tests or clear reproduction instructions, estimated at 2-4 hours of work." Catches repositories using alternative beginner-friendly label names.

```
gh search issues --label "help wanted" --language Python --state open --sort updated --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url -- "test OR bug OR fix"
```

## Ranking filters

Apply these filters in order over the fields returned by the search:

1. **Drop assigned issues**: Drop any result with one or more assignees.
2. **Drop stale issues**: Drop any result whose `updatedAt` is more than 60 days before the scan date.
3. **Drop frontend and UI work**: Traces to "I want to avoid heavy frontend UI/CSS work or complex infrastructure setups." Drop any result whose labels or title include `frontend`, `ui`, `css`, `html`, `react`, `gui`, or `web-ui`.
4. **Drop docs-only and DevOps infrastructure**: Traces to "avoid heavy complex infrastructure setups." Drop any result with labels containing `docs`, `documentation`, `ci`, `devops`, `infra`, `docker`, or `kubernetes`.
5. **Drop previously rejected URLs**: Drop any result whose URL was graded `reject` in a previous scan within the last 30 days.
6. **Tier ordering**: Order by query tier: Q2 first (data parsing & JSON handling), then Q1 (backend & APIs), then Q3 (curated repos), then Q4.
7. **Thread length**: Within a tier, prefer fewer `commentsCount` (indicates unclaimed, low-debate issues).
8. **Recency tie-break**: Tie-break by older `updatedAt` within the 60-day window (avoids threads bumped by fresh rival claim comments).
9. **Repository cap**: Cap at 2 results per repository in the top N to prevent one high-volume repo from dominating the scan.

## How many to grade

Grade the top **5** ranked results per scan.
