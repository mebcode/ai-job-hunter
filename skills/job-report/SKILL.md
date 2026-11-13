---
name: job-report
description: Use at the end of a scan to send the user the 7+ jobs and any due follow-ups in the standard short format; sends nothing when there's nothing to report.
---
# Job report

1. Read `guardrails/GUARDRAILS.md` and `templates/report-format.md`.
2. If no posting scored 7+, no follow-up is due, and no ⭐ Favorite row changed, send nothing at all, not even a "nothing today" note. Stop here.
3. Start with follow-ups that are due and changes on Favorite rows, Favorites first.
4. List the hits by score, highest first, each in this format:
   ```
   **<Title>, <Company>** (<Location>, <work mode>). Score <N>/10
   Posted <date> · <Salary range or "salary not listed"> · <Clearance needed, if relevant>
   Fits: <one line>
   Gap: <one line>
   <link to the posting itself>
   ```
   Add one more line only when the posting says it: tuition help, a development program, or flexible hours.
5. Keep it to a few lines per hit, with no padding or hype. Say plainly when a role is a stretch.
6. Don't repeat a posting you already reported unless something changed, such as a deadline coming up, and then say what changed.
7. Mention wildcards only as a count with a pointer to the Dashboard ("3 wildcards added to New matches to review"), plus any "Suggested for watchlist" employers.
8. End with one recommended next step, e.g. "I'd apply to #1 first. Want me to start?"
9. Send it to `<WHERE_REPORTS_GO>`. Then make sure every reported hit is in the tracker as Surfaced, with Score, Link, Location, Salary Range, and the fit and gap in Notes.
