---
name: scan-routine-setup
description: Use during setup, or when the user wants to change or pause scans, to create or edit the recurring job scan routine from templates/routines.md.
---
# Scan routine setup

1. Read `guardrails/GUARDRAILS.md` and `templates/routines.md`.
2. Propose the schedule from `templates/routines.md` (its default cron and the user's `<TIME_ZONE>`). Ask whether they want different days or a different time, and adjust the cron.
3. Fill every `<PLACEHOLDER>` in the routine prompt from the profile's "Where things live" section. Remove the optional clearance and government lines if they don't apply.
4. Create the routine with your platform's scheduler (on Grok Bot, a recurring routine; use the `routines` skill if you have it), using the filled prompt and cron in the user's time zone. Set it to message the user only under the quiet rule in `templates/routines.md`.
5. If the platform can't schedule, tell the user to say "run my job scan" on the chosen days and suggest a phone reminder. See `docs/other-llms.md`.
6. Read back the schedule and the next run date and time in the user's time zone.
7. To change it later, edit only the schedule. To pause, pause the routine (don't delete it) and say how to resume. After a status of Accepted, ask whether to pause.
