---
name: job-scan
description: Use on each scheduled scan, or when the user says "find me jobs," to search boards and company career pages for new postings that fit the profile and aren't already in the tracker.
---
# Job scan

1. Read `guardrails/GUARDRAILS.md`. Load the candidate profile (roles, location, level, salary floor, sources, clearance on/off), the company watchlist at `<WATCHLIST_LOCATION>`, and every tracker row's Company, Role, Link, Status, and Notes.
2. Work out the search window: since the previous run. On Mondays, include the weekend.
3. Search the default sources:
   - LinkedIn job search (public listings; use a LinkedIn site playbook if your agent has one), filtered by location, date posted, and level.
   - Indeed.
   - Each watchlist employer's own careers page, searched by role keywords and location.
4. Search the optional sources only if the profile turns them on: ClearanceJobs (cleared roles), USAJobs (federal roles), and any field-specific boards the user listed. No social media or forums unless the user asks.
5. Run two to four discovery searches for employers not yet on the watchlist, e.g. `<ROLE_KEYWORDS> jobs <HOME_CITY>`, `<ROLE_KEYWORDS> companies hiring near <HOME_CITY>`, `site:greenhouse.io <ROLE_KEYWORDS> <HOME_CITY>` (also lever.co, myworkdayjobs.com). Employers that keep showing up go in the report as "Suggested for watchlist." Add them only if the profile says to add automatically or the user agrees.
6. Keep a posting only if it's in the location radius (or acceptable remote), its level fits, it isn't a deal-breaker, and it's open and new since the last scan.
7. De-duplicate against the tracker: same link or req number, or same company with the same or nearly the same title.
   - Not interested: always skip.
   - Any other status: skip, unless something material changed (deadline coming up, reopened req, new location or salary). Then flag the change.
   - Same role on several sites: keep the employer's own link.
8. For each kept posting, capture title, company, location and work mode, posted date, salary if listed, clearance if relevant, req number, link, and key requirements (degree, years, must-have skills). Note tuition help, development programs, or flexible hours when the posting mentions them.
9. Hand the list to `job-scoring`. If nothing new turned up, report that to the routine so it stays quiet.
