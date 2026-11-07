---
description: Log a sent message or a reply on a prospect and set the next step
argument-hint: <person name> sent|replied [text]
---

Use the smartmemory-gtm skill and the SmartMemory CRM tools. Input: $ARGUMENTS

1. Find the person in the CRM. Ask whether this is a SENT or a REPLIED touch if unclear, and get the text if not provided.
2. History first: if the current `messageText` (for SENT) or `response` (for REPLIED) is non-empty and no dated note on the person already holds it, add a dated note with that old value before overwriting.
3. SENT: set `outreachStatus` SENT, `dateSent` today, `nextStepDue` = `dateSent` + 7 days (when the next step is a nudge), `nextStep` (for example "one nudge"), and `messageText` if it changed. Add a dated note with the message and channel.
4. REPLIED: set `outreachStatus` REPLIED, `response` to the reply, and a `nextStep` with `nextStepDue`. Add a dated note with the reply. Mention that any open "Nudge" task can be marked done. If the reply holds product feedback or a feature ask, say so, and suggest passing it to the team lead as roadmap input ("coming soon", never "no").
5. Read the record back and confirm in a line. Do not print contact data.
