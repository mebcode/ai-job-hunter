# Routines

The job hunter has one scheduled routine: the **job scan**. Set it up with `skills/scan-routine-setup`. Each run, it calls these skills in order: `tracker-updates-and-followups` → `job-scan` → `job-scoring` → `job-report`.

## Job scan

| Setting | Value |
|---|---|
| Name | `<YOUR_NAME>`'s job scan |
| Schedule (cron) | `0 7 * * 1,3,5`, which means 7:00 AM every Monday, Wednesday, and Friday |
| Time zone | `<TIME_ZONE>` (e.g. `America/New_York`). The cron runs in this zone, not UTC |
| Runs skills | `tracker-updates-and-followups`, `job-scan`, `job-scoring`, `job-report` |
| Delivers to | `<WHERE_REPORTS_GO>` (e.g. this chat, or an email address the agent can send to) |
| Messages the user | Only when there's a 7+ hit, a due follow-up, or a ⭐ Favorite change |

Other schedules:
- Every weekday at 7 AM: `0 7 * * 1-5`
- Mondays and Thursdays at 8 AM: `0 8 * * 1,4`

Monday's run should cover the weekend, so the prompt below says to search since the previous run.

If your agent can't schedule tasks, set a phone reminder for the same days and say "run my job scan."

### Prompt

Fill in every `<PLACEHOLDER>` and use this as the routine's prompt.

```
Run <YOUR_NAME>'s job scan. Follow guardrails/GUARDRAILS.md.

Context
- Candidate profile: <PROFILE_LOCATION>
- Company watchlist: <WATCHLIST_LOCATION>
- Tracker: the Notion database "Job Hunt Tracker" (<TRACKER_LINK>)
- Email to check for replies (optional): <EMAIL_CONNECTOR_OR_NONE>
- Time zone: <TIME_ZONE>. Search postings since the previous run. On Monday, include the weekend.

Steps
1. Read the profile, the watchlist, and all tracker rows.
2. Follow-ups first (skill: tracker-updates-and-followups). List rows whose Next Follow-up is
   due today or earlier, ⭐ Favorite rows first. Apply the 45-day stale rule, checking
   email for real replies if email is connected.
3. Scan (skill: job-scan). Search LinkedIn, Indeed, and the watchlist career pages<, plus ClearanceJobs
   and USAJobs if turned on in the profile>, and run 2 to 4 discovery searches for new
   employers. Skip duplicates, and always skip Not interested rows.
4. Score (skill: job-scoring), 1 to 10 using the rubric and the profile's soft factors.
   - 7+: add to the tracker as Surfaced and report.
   - 5 to 6: add as Surfaced with "Wildcard" at the start of Notes. Don't report.
   - Below 5: drop.
5. Report (skill: job-report). Follow-ups and Favorite changes first, then hits, best first,
   in templates/report-format.md. Count the wildcards in one line. Suggest new watchlist
   companies. End with one recommended next step.

Quiet rule: if there are no 7+ hits, no follow-ups due, and no Favorite changes,
send no message. Still save wildcards and stale updates to the tracker.

Never apply, create accounts, fill out forms, or message anyone during this routine.
```
