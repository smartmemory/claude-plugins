---
name: smartmemory-gtm
description: How SmartMemory works prospects in its CRM. Use when researching a prospect, drafting or logging outreach, checking a pipeline or follow-ups, or when anyone asks how SmartMemory outreach works (routes, message variants, who owns a prospect, what to say about missing features). Requires the "SmartMemory CRM" connector, signed in under your own CRM login.
---

# SmartMemory go-to-market process

The CRM is the single record. Use the "SmartMemory CRM" connector tools to read and write it. The connector must be signed in under YOUR OWN CRM login so every record and note is credited to you. If the CRM tools are missing, stop and tell the user to add the connector (see the README).

Status: this process is a draft. Ownership and lanes are set by the team lead, stages may change.

## Ownership
- Whoever first contacts a prospect owns them. Their name goes on the company Account Owner and on the person's notes.
- Lanes: each teammate has a lane value in the CRM. Read the options on the `lane` field. In general one lane covers the general market and social (individual developers, small teams, X, GitHub, communities), one covers enterprise (companies buying for a team or org), and one is for prospects the team lead handles personally.
- Before contacting anyone, search the CRM. If the person or their company already has an owner or a lane that is not yours, hand it to that person instead of contacting.

## Person fields (use exactly these, never invent others)
- `outreachStatus`: QUEUE, DRAFT_READY, SENT, REPLIED, PARKED, SKIPPED
- `lane`: one of the lane options defined on the field in the CRM (the owner of the prospect)
- `channel`: EMAIL, X_DM, REDDIT, OTHER
- Text: `route`, `variant`, `theirWords`, `foundOn`, `messageText`, `response`, `nextStep`, `statusReason`, `subreddit`
- Links (bare URL only): `sourceLink`, `trackingLink`
- Dates: `dateSent`, `nextStepDue`

Fields hold the latest state. The history lives in dated notes on the person.

## Workflow
1. Find. A person describes the pain in their own words (X, dev.to, Reddit, developer forums). Record `theirWords` (verbatim quote), `foundOn` (source and date), `sourceLink`. Status QUEUE.
2. Qualify. SKIPPED with a `statusReason` for: competitor builders, consultants selling services, template engagement threads, product launches, Hacker News. PARKED with a reason for real but closed inbox, thin signal, or a tutorial author (for example "DM if their inbox opens").
3. Route. Published email: EMAIL. X inbox open: X_DM. X inbox closed: a public X reply with no link, and a DM only if they reply or like. Reddit and forums: the teammate drafts, the team lead posts (REDDIT, DRAFT_READY). Forums need an account. Respect each subreddit's rules (usually no links, one disclosure clause), and record the `subreddit`.
4. Draft. Quote their words, name the gap their own fix leaves (usually stale or superseded decisions), one line on SmartMemory, and "we're early".
   - Variant A: offer a 15 minute screen share, or "poke at it and tell me what breaks". For teams and senior people.
   - Variant B: a 6 minute walkthrough link, "no call needed". For indie and small accounts.
   - Every DM link carries a per-person tracking code (`?r=` code), stored in `trackingLink`.
   - Booking link, when a call is offered: use the one your team lead gives you.
5. Send. Status SENT, `dateSent` = the day sent, `nextStepDue` = `dateSent` + 7 days when the next step is a nudge.
6. Follow up. One nudge if quiet after a week (low priority for tiny accounts). The CRM creates a "Nudge <name>" task 7 days after `dateSent` is set. Mark the task done if they replied.
7. Reply. Status REPLIED, store the reply in `response`, set `nextStep` and `nextStepDue`. Product feedback goes to the team lead as roadmap input.

## Outreach rules
- Email only to an address the person publishes. X DM only where the inbox is open. Public X reply where it is closed.
- Reddit and forum replies are drafted for the team lead, who sends them. Do not post them yourself.
- No Hacker News outreach yet.
- Never say "no" to a prospect about a missing feature. Say "coming soon" and ask for the detail so it goes on the roadmap with their name.
- Every touch is logged by the person who made it. After the first contact, every person has a next step and a due date.
- First message approval: none required by default. Offering a draft to the team lead for review is optional, never a gate.

## History rule (also for hand edits in the CRM screen)
Before you change `messageText` or `response`, make sure the current value already sits in a dated note on the person. If it does not, add that note first, then update the field. Never overwrite the only copy of a message or reply.

## Privacy
Never paste a prospect's email address, phone or other contact data into chat or into files. Keep it in the CRM only.

## Views in the CRM
Outreach: Queue, Sent, Reddit, Skipped, Parked, Follow-ups due, Pipeline (kanban). A weekly pipeline review runs from the CRM dashboard.

## Tool notes
Creating people with the custom fields works with the bulk create tool. Updating a links field with the single-person update tool was rejected in one test, so set links when you create the person, or try the bulk update tool, and verify by reading the record back.
