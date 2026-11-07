---
description: Add a researched prospect to the CRM as QUEUE or DRAFT_READY
argument-hint: <name or profile link> [notes]
---

Use the smartmemory-gtm skill and the SmartMemory CRM tools. Input: $ARGUMENTS

1. Search the CRM for this person and their company first. If they exist with another owner or lane, stop and say who owns them. If they exist under you, offer `draft-message` instead of creating a duplicate.
2. Collect from the user (ask only for what is missing): their words (verbatim quote of the pain), where found and when (`foundOn`), the source link, the channel (EMAIL, X_DM, REDDIT, OTHER) and `route`, and `subreddit` if Reddit. Apply the qualify rules: if they should be SKIPPED or PARKED, set that status with a `statusReason`.
3. Create the person with `lane` set to the user's lane (ask if unknown), `outreachStatus` QUEUE (or DRAFT_READY if the user already has `messageText`), `theirWords`, `foundOn`, `sourceLink`, `route`, `channel`. Set links at create time.
4. Add a dated note on the person saying who researched them and why.
5. Read the record back and confirm in a line. Do not print contact data.
