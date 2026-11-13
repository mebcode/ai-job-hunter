---
name: notion-tracker-setup
description: Use once during setup, or when the tracker is missing or broken, to create the Notion Job Hunt Tracker database and the Job Hunt Dashboard with its two views.
---
# Notion tracker setup

1. Read `guardrails/GUARDRAILS.md`. Confirm the Notion connector works (you can read and write a page). If it doesn't, stop and fix the connection first.
2. Create a database called **Job Hunt Tracker** in the user's workspace, at the top level or under a "Job Hunt" page, with these columns:

   | Column | Type | Notes |
   |---|---|---|
   | Role | Title | Job title as posted |
   | Company | Text | |
   | Link | URL | The posting itself, preferably on the employer's site |
   | Score | Number | 1 to 10 |
   | Status | Select | Options in step 3 |
   | Date Applied | Date | |
   | Next Follow-up | Date | |
   | Notes | Text | Req number, fit, gaps, "Wildcard," route used to apply |
   | Location | Text | City, state, and on-site/hybrid/remote |
   | Salary Range | Text | As posted; hourly as annual equivalent, e.g. "$72,800/yr ($35/hr)" |
   | ⭐ Favorite | Checkbox | The user's top picks; their updates go first |
   | # | Unique ID | Auto-number in the order rows were created |
   | Type | Select (optional) | Full-time, Internship, Contract |

3. Add these Status options, with colors that are easy to tell apart: Surfaced (gray), Interested (yellow), Not interested (pink), `<YOUR_NAME>` to submit (purple), Applied (blue), First interview completed (yellow), Interviewing (orange), Offer (green), Accepted (green), Rejected (red), Stale/No response (gray). Optional: Not selected, Position closed, Withdrawn. Replace `<YOUR_NAME>` with the user's first name, e.g. "Jane to submit." Always match status values with capitalization ignored.
4. Create a page called **Job Hunt Dashboard** with a linked table view named **In play**:
   - Filter: Status is any of Accepted, Offer, Interviewing, First interview completed, Applied, Interested, `<YOUR_NAME>` to submit.
   - Sort: Date Applied (newest first), then ⭐ Favorite (checked first), then Score (highest first).
   - Columns: #, Role, Company, Status, ⭐ Favorite, Date Applied, Next Follow-up, Score, Location, Salary Range, Link.
5. Add a second linked table view named **New matches to review**:
   - Filter: Status is Surfaced.
   - Sort: Score (highest first).
   - Columns: #, Role, Company, Score, Status, ⭐ Favorite, Location, Salary Range, Notes, Link.
6. Make "#" the first, narrow column in both views. Tell the user plainly that Notion has no counter that restarts at 1 per view: "#" is a fixed creation-order ID. If they want the lowest number on top, sort that view by "#" ascending, which replaces the other sorts.
7. Add a test row, check it appears in "New matches to review," then delete it.
8. Save the tracker and Dashboard links as `<TRACKER_LINK>` and `<DASHBOARD_LINK>` in the profile's "Where things live" section. Never publish them.
9. Have the user open the Dashboard on their own device and confirm they see both views.
