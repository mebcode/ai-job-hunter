# SETUP: instructions for the AI agent

**This file is written to you, the AI agent.** The person you're helping wants an automated job hunter. Assume they have never used Notion or an AI agent before. Walk them through the steps below in order, one step at a time.

## How to run this setup
- Explain each step in one or two plain sentences before doing it. No jargon. If you must use a term like "connector," say what it means.
- Ask one question at a time. Wait for the answer.
- At each **Checkpoint**, confirm the step worked before moving on. If it didn't, fix it or explain the problem plainly.
- Do every step you can do yourself. Only ask the user to act when it truly needs them: signing in, approving access, or a choice only they can make.
- Read `guardrails/GUARDRAILS.md` now and follow it for the whole setup and after.
- If you are not Grok Bot, also read `docs/other-llms.md`. Where a step says "Grok Bot," do the closest thing your platform supports, or tell the user it needs to be done by hand.

---

## Step 0: Welcome
Say what the finished system will do, in about three sentences:
1. It checks job sites a few mornings a week and messages them only when it finds a good match.
2. Everything goes into a Notion tracker they can open from their phone or computer.
3. When they like a job, you tailor their resume and fill out the application, but **nothing is submitted until they say yes**.

Tell them setup takes 30 to 60 minutes and they can stop and come back anytime.

Ask: "Ready to start?"

## Step 1: Create a Notion account
Explain: Notion is a free app for notes and tables. Their job tracker will live there.

1. Ask whether they already have a Notion account.
2. If not, send them to https://www.notion.com/signup and tell them to sign up with the email they use most. The free plan is enough. They do this part themselves; never create the account for them.
3. Ask them to tell you when they can see their Notion home page.

**Checkpoint:** the user confirms they're signed in to Notion.

## Step 2: Connect Notion to you
Explain: a connector is a permission that lets you read and edit their Notion pages. They can remove it anytime.

1. **Grok Bot:** open the connector settings and add the Notion connector (use the `add-connector` skill if you have it). The user signs in to Notion and approves access in the window that opens.
2. **Other agents:** use your platform's Notion integration or MCP server. See `docs/other-llms.md`.
3. Test it: search their Notion workspace or create and then delete a page called "Connection test."

**Checkpoint:** you can read and write in their Notion. If you can't, stop and help them fix the connection. Nothing later works without it.

## Step 3: Intake interview
Run `skills/job-hunter-setup`. It interviews the user and writes their candidate profile from `templates/candidate-profile.template.md`.

Before you start, ask them to share their current resume (a file or pasted text). Fill in what you can from it, then ask only about what's missing.

Ask early: "Do any of the jobs you want require a security clearance or government work?" If not, skip the clearance section and the clearance and government job boards entirely.

**Checkpoint:** read a short summary of the profile back to them (target roles, location, salary floor, start date, deal-breakers) and ask, "Is this right?" Fix anything wrong.

## Step 3b: Save personal info and logins in the vault

Contact details and logins never go in the profile file or in chat.

1. **Grok Bot:** open the Vault form and have the user enter their application email, phone, and mailing address there. When a job site needs a login, save it to the Vault the same way, with the user typing the password into the vault form or into the site, never into chat.
2. **Other agents:** have the user keep these in a password manager they control, or type them straight into each site when asked.
3. Confirm the profile file has no email, phone, address, SSN, birthdate, or password in it.
4. Tell them plainly: "I'll fill forms from the vault, but I won't submit anything, create an account, or apply anywhere without your yes for that specific job."

## Step 4: Build the tracker
Run `skills/notion-tracker-setup`. It creates the "Job Hunt Tracker" database and a "Job Hunt Dashboard" page with two views.

Then give them a two-minute tour:
- **New matches to review** shows jobs the scan found. This is where they decide.
- **In play** shows jobs they're pursuing or have applied to.
- To decide on a job, click its **Status** and pick **Interested** or **Not interested**.
- Tick **⭐ Favorite** on the ones they care about most. Those get updates first.

**Checkpoint:** the user opens the Dashboard link on their own device and sees both views. Suggest they add it to their favorites in Notion or bookmark it.

## Step 5: Create the bot persona
Explain: the persona is a short set of instructions that tells you who they are, what to look for, and what you must never do.

1. Fill in `templates/persona.md` from their profile. Replace every `<PLACEHOLDER>`. Delete any line that doesn't apply, such as the clearance lines.
2. Show them the filled-in persona and ask if anything should change.
3. **Grok Bot:** save it as this bot's description/instructions (or create a dedicated bot for the job hunt and paste it there). **Other agents:** paste it into the system prompt, custom instructions, or project instructions.

**Checkpoint:** they approve the persona and it's saved.

## Step 6: Install the skills
Explain: skills are short instruction files, one for each job you do (scan, score, tailor, apply...).

1. **Grok Bot:** save each `skills/<name>/SKILL.md` as a skill on this bot, keeping the same name and description. Also make `guardrails/GUARDRAILS.md` available, since every skill refers to it.
2. **Other agents:** add the files to the project or knowledge base, or keep them in a folder you can read. See `docs/other-llms.md`.
3. Save their company watchlist at the location they chose (record it in the profile's "Where things live" section): fill `templates/company-watchlist.template.md` with 10 to 30 employers they'd like to work for. Suggest some based on their field and location, and ask them to add or remove.

**Checkpoint:** list the installed skills back to them.

## Step 7: Schedule the scan
Run `skills/scan-routine-setup`. It uses the prompt and default cron in `templates/routines.md` (Monday, Wednesday, and Friday mornings in their time zone). Ask if they want different days or times.

Tell them: "On days with nothing good, you won't hear from me. Silence means nothing new cleared the bar."

**Checkpoint:** the routine exists and shows the next run time. Tell them the date and time in their own time zone.

## Step 8: Dry-run scan
Run one scan now, while they watch:
1. Run the routine prompt from `templates/routines.md` once by hand (it calls `tracker-updates-and-followups`, `job-scan`, `job-scoring`, and `job-report`).
2. Add results to the tracker as the scan normally would.
3. Show the report, then have them open the Dashboard and find the same rows.

If nothing scores 7 or higher, say so and show the best two or three wildcards instead, so they can see what the scan found. Ask whether the scoring feels right: too strict, too loose, or wrong kinds of jobs. Adjust the profile or rubric and rerun if needed.

**Checkpoint:** they've seen a report and the matching tracker rows, and they're happy with how jobs are scored.

## Step 9: Show them how to use it day to day
Practice with one real row from the dry run:
1. Have them set it to **Interested** or **Not interested** in Notion.
2. Explain: **Not interested** means you'll never show that job again. **Interested** means you'll offer to tailor their resume and apply.
3. Explain the apply flow in one breath: "Say 'apply to <company> <role>.' I'll tailor your resume and show it to you, fill out the employer's form, and show you every answer. Nothing gets submitted until you say yes."
4. Explain updates: "Tell me when you apply somewhere yourself, get an interview, or hear back, and I'll update the tracker and remind you about follow-ups."
5. Tell them what you will never do: message recruiters, submit without their yes, make up experience, or ask for passwords in chat.

**Checkpoint:** they've marked at least one row and know how to ask you to apply.

## Step 10: Wrap up
Send a short summary:
- the Dashboard link
- when the next scan runs, in their time zone
- the three things they'll do most: mark rows Interested or Not interested, say "apply to...", and tell you about replies and interviews
- how to change their profile later ("Tell me what changed and I'll update your profile.")

Setup is done.
