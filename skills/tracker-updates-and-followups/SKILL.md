---
name: tracker-updates-and-followups
description: Use when the user reports news on an application, on each scheduled scan to surface due follow-ups, and to mark applications Stale after 45 days with no real reply.
---
# Tracker updates and follow-ups

1. Read `guardrails/GUARDRAILS.md`.
2. When the user reports news, find the row by company and role, ignoring capitalization. If several match, ask which one. If none match, offer to add it.
3. Set the Status and dates:

   | User says | Status | Also |
   |---|---|---|
   | "I applied to X" | Applied | Date Applied = that day; Next Follow-up ≈ a week later |
   | "I'm interested in X" | Interested | Offer to tailor and apply |
   | "Not interested in X" | Not interested | Never show it again |
   | "Had my first interview" | First interview completed | Next Follow-up 3 to 5 business days out; offer a thank-you draft |
   | "They want more interviews" | Interviewing | Note dates; offer a prep checklist |
   | "Got an offer" | Offer | Note the deadline in Notes and Next Follow-up |
   | "I accepted" | Accepted | Ask whether to pause the scan routine |
   | "Rejected" / "Not selected" | Rejected (or Not selected) | Clear Next Follow-up |

4. Confirm each change in one line, e.g. "Updated: Acme Analyst → Interviewing, follow-up Nov 20."
5. On each scheduled run, list rows whose Next Follow-up is today or earlier and whose Status is still active, ⭐ Favorite rows first, each with one suggested action (check the portal, send a follow-up draft, or wait).
6. For rows still Applied 45+ days after Date Applied, check `<EMAIL_CONNECTOR_OR_NONE>` for a real reply from that company (an interview request, a rejection, or a recruiter message; automated receipts don't count).
   - Real reply: update the Status to match and tell the user.
   - No reply: set Stale/No response and mention it once in the report.
   - No email connected: ask the user once whether they've heard anything before marking it Stale.
7. Never resurface rows marked Not interested.
