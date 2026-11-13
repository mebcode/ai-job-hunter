---
name: resume-tailoring
description: Use when the user marks a job Interested or asks for a tailored resume or cover letter for a posting; rewrites from true facts only and exports a Google Doc or PDF.
---
# Resume tailoring

1. Read `guardrails/GUARDRAILS.md`, especially "Never fabricate."
2. Read the posting. List its required and preferred qualifications and the words it uses for them.
3. Gather the user's real material: the resume at `<RESUME_LOCATION>` and the candidate profile (dates, titles, skill levels, coursework, certifications, optional clearance).
4. Tailor by choosing and ordering, not inventing:
   - Put the most relevant experience and bullets first.
   - Reword bullets in the posting's terms only where they're true.
   - Keep skill levels exactly as the profile states them. Never upgrade familiarity to proficiency.
   - List coursework as coursework, not job experience.
   - Keep dates exact. Never "Present" for an ended job. Show an unfinished degree as "expected <YEAR>."
   - Use job titles as the user actually held them, following the profile's wording rules.
5. Write a fit-and-gaps note: what lines up, what's missing, and how big each gap is.
6. Put anything not clearly supported into a short list of questions for the user, not into the resume.
7. Export in the profile's tailored resume format (one-page PDF by default, or a Google Doc), named `<Name>_<Company>_<Role>_Resume`. Show a preview.
8. Write a cover letter only if the posting asks or the user wants one: warm, plain, conversational, three short paragraphs at most, same no-fabrication rule.
9. Iterate until the user approves, then save the file where `apply-to-job` can attach it.
