# Using ai-job-hunter with other AI agents

This package is plain Markdown, so any capable agent can follow it. It was built and tested on Grok Bot, which has everything the pipeline uses: web search, a browser, connectors, skills, memory, and scheduled routines. Other agents vary. Here's how to map each piece.

## What each piece needs

| Piece | Needs | If your agent lacks it |
|---|---|---|
| Persona (`templates/persona.md`) | A place for standing instructions | Paste it at the start of each chat |
| Skills (`skills/*/SKILL.md`) | A way to load instruction files | Upload them as files, or paste the one you need |
| Tracker | A Notion connector or integration | Update Notion by hand from the agent's output |
| Scan | Web search | Paste postings in yourself and ask the agent to score them |
| Apply | A browser the agent can drive | The agent prepares every answer and the resume; you fill out the form |
| Schedule | Scheduled tasks | Start each scan yourself: "Run my job scan" |
| Stale check | An email connector | The agent asks you whether you've heard back |

## Claude (claude.ai Projects or Claude Desktop)
- Make a Project. Paste the filled persona into the project instructions.
- Upload `guardrails/GUARDRAILS.md`, the `skills/` files, `PROCESS.md`, your profile, and your watchlist as project knowledge.
- Connect Notion through Claude's connectors or a Notion MCP server.
- Turn on web search. Browser steps depend on your setup; without a browser, you do the form filling.
- If you have no scheduler, start scans by hand.

## ChatGPT
- Make a custom GPT or a Project. Put the persona in its instructions, and upload the skills and guardrails as knowledge files.
- Turn on web search. Use a Notion connector if your plan has one; otherwise copy results into Notion yourself.
- Use scheduled tasks if your plan offers them, with the filled prompt from `templates/routines.md` as the task prompt and its schedule (e.g. Mon/Wed/Fri at 7 AM).
- Agent or browser modes can fill out forms. The stop-at-Submit rule still applies.

## Cursor and other coding agents
- Clone the repo. Put the persona in your rules or agent instructions file, and keep the skills in the repo where the agent can read them.
- Add a Notion MCP server for the tracker.
- Schedule scans with your platform's background or scheduled agents if it has them, or a reminder to start one.

## Rules that never change
Whatever the platform, the guardrails apply: nothing gets submitted without your yes, nothing is fabricated, recruiters hear from you rather than the agent, and passwords and SSNs stay out of chat.
