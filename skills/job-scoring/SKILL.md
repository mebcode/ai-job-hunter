---
name: job-scoring
description: Use after a job scan, or when the user asks "is this a good fit?", to score a posting 1 to 10 against the profile and decide whether to report it, keep it as a wildcard, or drop it.
---
# Job scoring

1. Read `guardrails/GUARDRAILS.md`. Score from the candidate profile and the posting only. Don't assume skills the profile doesn't list.
2. Start at 0 and add points, maximum 10:

   | Factor | Points | How to score |
   |---|---|---|
   | Role match | 0-3 | 3 core target role · 2 close cousin · 1 adjacent field · 0 unrelated |
   | Qualifications | 0-3 | 3 meets all required · 2 misses one learnable item · 1 misses several · 0 clearly underqualified |
   | Location and work mode | 0-2 | 2 inside radius or acceptable remote · 1 edge of radius or hybrid stretch · 0 outside |
   | Level and pay | 0-1 | 1 right level and pay at or above the floor (or not listed) · 0 clearly under the floor |
   | Soft factors | 0-1 | 1 if the posting clearly offers the profile's top soft factor |

3. Use the profile's soft factors, in its order: development program or new-hire training, commute, schedule fit (regular hours around school or family), tuition help, growth in the field. If the profile weights soft factors more, raise their cap to 2 and lower Role match to 0-2.
4. If the profile has clearance turned on: cap the score at 4 when the role needs more clearance than the user holds or can get. A required polygraph the user hasn't taken is a gap, not a penalty, if they're willing to take one.
5. Apply the thresholds (the profile can move them):
   - 7 to 10: Surfaced. Report it, and add it to the tracker as Surfaced.
   - 5 to 6: Wildcard. Add it as Surfaced with "Wildcard" at the start of Notes. Don't report it.
   - Below 5: drop it.
6. For every posting you keep, write the score, one line on why it fits, and one honest gap. There's always at least one.
7. If the user keeps rejecting 7+ jobs or keeps liking wildcards, ask whether to adjust the rubric, and record any change in the profile.
