# Notes

## What I changed

- Fixed the task search query. The status and archived filters were not always being applied because the `AND` and `OR` conditions were not grouped correctly.
- Removed an unnecessary `Thread.sleep()` from the controller. It was making some searches slower than they needed to be.
- Added checks for invalid page and page-size values.
- Added a proper `400 Bad Request` response for unknown status values.
- Updated the SQL reference files to match the application query.

## Why I chose these fixes

I found these issues by running the API with different status, search, and pagination values. They either returned incorrect results, made the API slower, or turned bad input into a server error. The fixes were small and did not require changing the overall design.

## What I did not change

The repository still loads all matching tasks and applies pagination in memory. Moving pagination into the database would be a better long-term solution, but it would require a larger change and more testing. I also left unrelated frontend improvements for later.

## Biggest remaining risk

In-memory pagination may become slow and use too much memory if the number of tasks grows significantly.

## Tools used

I used the application, `curl`, and Maven to investigate and verify the changes. I also used AI assistance to help review possible bugs, then checked the behavior myself.
