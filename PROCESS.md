# Process

The full method, from first setup to an accepted offer. Each step names the skill that does it. All steps follow `guardrails/GUARDRAILS.md`.

## Inputs
- The user's current resume.
- Answers from the intake interview, saved as the **candidate profile**: target roles, location and radius, remote preference, salary floor, start date, schedule limits, skill levels, deal-breakers, standard application answers, and optional clearance details.
- A **company watchlist** of employers the user wants to work for.
- A Notion account connected to the agent.

## Outputs
- A Notion **Job Hunt Tracker** database and a **Job Hunt Dashboard** page.
- Scan reports sent to the user on a schedule, only when something clears the bar.
- Tailored resumes (Google Doc or PDF), and cover letters when needed.
- Filled-out applications, submitted only after the user's yes.
- Follow-up reminders and draft messages for the user to send.

## Steps

### 1. Intake (`job-hunter-setup`)
Interview the user and write the candidate profile. Pull what you can from the resume first, then ask about the gaps.
- **Decision:** does the user need clearance or government jobs? If no, turn off that section and those sources.
- **Done when** the user confirms a read-back of the profile.

### 2. Tracker setup (`notion-tracker-setup`)
Create the database, its columns and status options, and the Dashboard with the "In play" and "New matches to review" views.
- **Done when** the user can open the Dashboard on their own device.

### 3. Schedule (`scan-routine-setup`)
Create the recurring scan from the prompt and cron in `templates/routines.md` (default `0 7 * * 1,3,5` in the user's time zone).
- **Done when** the routine exists and its next run time has been confirmed with the user.

### 4. Scan (`job-scan`)
Each run:
1. Read the profile, the watchlist, and the tracker.
2. Search the job boards, the watchlist companies' career pages, and (if turned on) clearance and government boards. Run a few discovery searches for employers not yet on the watchlist.
3. Keep only postings that are new since the last run, in the user's location or remote, and at the right level.
4. Drop duplicates already in the tracker, matching on company plus role title, or on the posting link or req number. Never bring back a row marked Not interested.
- **Decision:** a posting already in the tracker comes back only if something important changed, like a deadline coming up or a reopened req.

### 5. Score (`job-scoring`)
Score each new posting 1 to 10 against the profile, using the rubric.
- **Decision:**
  - **7 or higher:** report it and add it to the tracker as Surfaced.
  - **5 to 6:** add it to the tracker as Surfaced with "Wildcard" in Notes. Don't report it.
  - **Below 5:** drop it.

### 6. Report (`job-report`)
Send the user the 7+ hits, best first, in the standard format (`templates/report-format.md`). Add due follow-ups and changes on ⭐ Favorite rows at the top.
- **Decision:** if there are no hits and nothing is due, send nothing.

### 7. User decides
In the Dashboard, the user sets Status to **Interested** or **Not interested**, or asks in chat.
- Not interested rows are never shown again.
- Interested rows: offer to tailor and apply.

### 8. Tailor (`resume-tailoring`)
Reorder and reword the resume for the posting using only true facts. Write a short fit-and-gaps note and questions for anything unclear. Export a Google Doc or one-page PDF.
- **Done when** the user approves the resume.

### 9. Apply (`apply-to-job`)
Five stages: read the posting on the employer's site, tailor (step 8), fill the form, confirm every answer with the user, and track.
- **Decision:** submit only after an explicit yes for this posting.
- **Decision:** if a captcha or bot check blocks the form, retry once at most. Then hand off: give the user the direct link, the approved answers, and the resume file, and set Status to "<YOUR_NAME> to submit."
- **Done when** a confirmation is captured and the tracker row reads Applied, with today's Date Applied and a Next Follow-up about a week out.

### 10. Follow up (`tracker-updates-and-followups`, `recruiter-message-draft`)
- Update Status whenever the user reports news: interview, rejection, offer.
- Remind the user of follow-ups that are due during the scheduled run.
- After 45 days as Applied with no real reply, check the user's email for one, if email is connected. If there's none, set Status to Stale/No response.
- When a message to a recruiter would help, draft it. The user sends it.

## Done criteria for the whole system
- The profile is confirmed, the tracker and Dashboard exist, the routine is scheduled, and one dry-run scan has been reviewed with the user.
- Every reported job has a working link and an honest gap.
- No application has gone out without a recorded yes.
- Every row the user has acted on has a current Status.
