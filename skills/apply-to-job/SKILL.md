---
name: apply-to-job
description: Use when the user says yes to applying for one specific posting; reads it, tailors the resume honestly, finds the employer's own application, and submits only after an explicit yes.
---
# Apply to a job

Follow `guardrails/GUARDRAILS.md`. The user has said yes to ONE specific posting. Stop after each stage for feedback; never submit, create an account, or send anything without an explicit yes for this posting.

## Stage 1: Read the posting
1. Open the posting link from the tracker. Then find the SAME role on the employer's own site: web-search `<company> <role keywords> <city>` and open the employer-domain result (its careers page), not a job board copy.
2. Capture: responsibilities, required and preferred quals, degree, clearance (if relevant), on-site, hybrid or remote, travel, salary (fill the tracker's Salary Range), tuition help or flexible hours if stated, posted date, req number, and whether there's a senior or junior twin posting (target the right level).
3. Find the apply route, in this order of preference:
   - The employer's own online application form (often an "Apply" or "Position Application" page linked from the posting). Note every field on it.
   - An external applicant tracking system (Workday, iCIMS, Greenhouse, etc.). If it needs a new account, that sign-up is the user's to do.
   - LinkedIn Easy Apply (check which resume file it would send).
   - Emailing HR, only when the employer gives no form.
   Don't conclude there's no online form until you've checked the employer's own posting page for an Apply link.

## Stage 2: Tailor the resume
1. Start from the user's current resume and their saved facts in the candidate profile (coursework, dates, clearance if any, skill levels).
2. Reorder and reword to emphasize what the posting asks for, following `skills/resume-tailoring`. Use ONLY true facts. State skill levels honestly (e.g. "familiarity, undergraduate coursework"), list coursework as coursework, and keep end dates accurate (never "Present" for a past job).
3. Write an honest fit-and-gaps note and a short list of questions for the user. Anything not clearly supported goes in the questions, not the resume.
4. Export a clean one-page PDF (or the user's preferred format) and show a preview. Iterate on the user's feedback.
5. Write a cover letter only if the posting asks for one or the user wants it. Keep it warm, plain, and conversational, not stiff or list-like. Any email written in the user's name is short and casual, with plain asks and a first-name sign-off.

## Stage 3: Fill the application
1. Open the application form in the browser. Upload the tailored resume and fill fields from saved facts: name, contact info, and the availability date the user stated.
2. Anything not on file (salary expectations, work authorization, demographic or EEO questions, references) goes to the user through a secure form or chat, or stays blank for them. Never pick demographic answers.
3. Stop at the final review step, before Submit. Take a screenshot.
4. A passive captcha badge (the small "protected by reCAPTCHA" logo in a corner) is not a blocker; keep filling. Only an actual challenge, such as a checkbox, puzzle, image grid, or an error that stops the form, counts as a captcha.

## Stage 4: Confirm and submit
1. Send one confirmation restating the posting, the file attached, and every answer that will be submitted. A dismissed or unclear reply is a no.
2. Submit only after a yes. Capture the confirmation page or message.
3. If a captcha, "I'm human" check, or bot or authenticity error blocks the form or the submission, retry once at most. Then stop: send the user the direct application link, the approved answers in one copy-ready list, and the resume file, and set the tracker row to "`<YOUR_NAME>` to submit." Don't keep retrying or hand the screen over repeatedly.

## Stage 5: Track
1. Update the tracker row: Status Applied, Date Applied today, Next Follow-up about one week out, and Notes with the route used and the file sent.
2. Report the confirmation and what happens next in one or two lines.
