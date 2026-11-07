---
description: Draft the first outreach message for a prospect and save it as DRAFT_READY
argument-hint: <person name>
---

Use the smartmemory-gtm skill and the SmartMemory CRM tools. Person: $ARGUMENTS

1. Find the person in the CRM and read `theirWords`, `foundOn`, `channel`, `route`, `subreddit`, `variant`, `trackingLink`. Check the owner and lane: if it is not the user's, stop.
2. Pick the variant (A for teams and senior people, B for indie and small accounts) unless one is set. Write the message to match the channel (short DM, email, or a public reply with no link, and Reddit follows the subreddit rules). Quote their words, name the gap their own fix leaves, one line on SmartMemory, "we're early". Use the tracking link if present. Never say "no" to a missing feature.
3. Show the draft to the user and let them edit.
4. Offer, as an optional choice the user can decline: "Send this to your team lead for review?" If they accept, share the draft and the person's name with them using whatever messaging the user prefers (email draft or paste). Never force this step. Reddit and forum drafts are always for the team lead to post.
5. When the user approves the text: per the history rule, make sure any existing `messageText` is already saved in a dated note, then set `messageText`, `variant`, and `outreachStatus` DRAFT_READY. Add a dated note with the draft.
6. Do not send anything.
