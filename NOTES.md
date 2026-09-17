# Notes

## What I changed

- Fixed the task search so the status and archived filters work correctly. The `AND` and `OR` conditions were not grouped correctly before.
- Removed an unnecessary `Thread.sleep()` from the controller. It was making some searches slower.
- Added checks for invalid page and page-size values.
- Added a proper `400 Bad Request` response when an unknown status is sent.
- Updated the SQL reference files so they match the application query.
- Added backend integration tests for filtering and invalid request parameters.
- Added debounced, cancellable frontend searches and reset pagination when filters change.

## Why I made these fixes

I tested the API with different status, search, and pagination values. Some requests returned incorrect results, some were slow, and some turned bad input into a server error instead of returning a clear message. These fixes were small and did not require major changes to the application.

## What I did not change

The application still loads all matching tasks and applies pagination in memory. Moving pagination into the database would be better in the long run, but it is a larger change that would need more testing. I did not add task editing or creation because this exercise is focused on the existing search flow.

## Biggest remaining risk

If the number of tasks grows significantly, applying pagination in memory could make the application slower and use more memory. The next production improvement would be database-level pagination with a count query.

## Tools I used

I used the application, `curl`, Maven tests, and the Vite production build to verify the fixes. I used AI to review possible bugs and draft ideas, then checked and adjusted the implementation myself.
