# FAQ

**Will it apply to jobs without asking me?**
No. It stops at the Submit button for every application and waits for your yes for that specific posting. It also never creates job-site accounts for you.

**Will it make up experience to get me past filters?**
No. It only uses facts from your profile and resume, and it keeps your skill levels as you stated them. If something isn't clear, it asks.

**Why didn't I hear anything today?**
The scan stays quiet when nothing new scores 7 or higher and no follow-up is due. Check "New matches to review" in Notion for wildcards (5–6).

**I keep getting jobs I don't want.**
Mark them Not interested and tell the agent why ("too much travel," "too senior"). Ask it to update your profile or tighten the scoring. You can also raise the report threshold.

**I'm not getting enough matches.**
Widen your commute radius or role list, lower the threshold to 6, or add more companies to your watchlist.

**Why doesn't the "#" column start at 1 in each view?**
Notion has no row counter that renumbers per view. "#" is a fixed ID in the order rows were added. Sort a view by "#" ascending if you want the lowest number at the top.

**A captcha stopped the application. Now what?**
The agent tries once, then sends you the link, your approved answers, and the resume, and marks the row "<your name> to submit." Paste the answers in and submit it yourself.

**Can it message recruiters for me?**
It writes the message. You send it.

**Do I need a clearance section?**
Only if you're looking for cleared or government work. Otherwise delete that part of the profile, and the scan skips those boards.

**Does it work outside the US?**
The method does. The standard application answers and default job boards are US-focused, so edit the profile template and the sources in `skills/job-scan` for your country.

**Is my data shared?**
Your profile, resume, and tracker stay in your agent and your Notion workspace. The `.gitignore` keeps your filled-in profile, watchlist, and resumes out of git if you fork this repo. Don't commit them to a public repo.

**How do I pause it?**
Tell the agent "pause my job scan." It pauses the routine without deleting it.
