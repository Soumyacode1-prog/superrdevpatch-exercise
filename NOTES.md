# Notes

## Summary of changes

I fixed four issues in the task tracker. I corrected the SQL grouping so archived and status filters work correctly. I removed the artificial delay from search requests. I added validation for invalid pagination values and invalid task statuses.

## Why I selected these fixes

These issues affected correctness, response time, and API reliability. They were reproducible with simple API requests and could be fixed without rewriting the application.

## What I did not change

I did not replace the in-memory pagination with database-level pagination. This would require a larger repository and API refactor. I also did not change unrelated frontend behavior because it was outside the focused patch.

## Biggest remaining risk

The backend still loads all matching tasks before applying pagination. This could become inefficient if the database grows significantly.

## Tools used

I used curl to test the API, Maven to build the backend, and AI assistance to review the code and identify possible bugs. I verified the fixes by running the backend and repeating the API tests.
