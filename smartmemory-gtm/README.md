# SmartMemory GTM kit

Four helpers for working prospects in the SmartMemory CRM: research a prospect, draft a message, log what you sent or what they replied, and see your pipeline. It also teaches Claude how the team does outreach, so you do not have to explain it each time.

Pick the setup that matches how you use Claude.

## A. Claude Code

1. Add the SmartMemory plugin catalog (one time): `claude plugin marketplace add smartmemory/claude-plugins`
2. Install: `claude plugin install smartmemory-gtm@smartmemory`
3. Connect the CRM (section C below).

You then have four commands: `/smartmemory-gtm:research-prospect`, `/smartmemory-gtm:draft-message`, `/smartmemory-gtm:log-touch`, `/smartmemory-gtm:my-pipeline`.

## B. Claude app or claude.ai (web)

1. Get the skill zip from your SmartMemory contact, or zip the folder `skills/smartmemory-gtm` yourself so that the zip contains the folder `smartmemory-gtm` with `SKILL.md` inside.
2. In Claude, open Settings, then Capabilities (or Skills), and upload the zip. Turn the skill on.
3. Add the CRM connector (section C below).
4. In a chat, just say what you want, for example "research this prospect: <link>", "draft a message for Jane", "log that I sent Jane the DM today", or "show my pipeline".

## C. Connect the CRM under your own login

This matters: records and notes are credited to the person who is signed in.

1. Ask your SmartMemory contact to invite you to the CRM. You will get your own login.
2. Claude Code: add the connector with `claude mcp add --transport http smartmemory-crm https://mcp.smartmemory.ai/crm/mcp`, then run `/mcp`, choose it, and sign in with your own CRM account when the browser opens.
   Claude app or web: open Settings, then Connectors, add a custom connector with the URL `https://mcp.smartmemory.ai/crm/mcp`, and sign in with your own CRM account.
3. Check it works: ask Claude "list my prospects". If it says it cannot see the CRM, the connector is not signed in yet.

Without an invited account the connector will not let you in, and you will see no data.

## Good to know

- Claude never sends anything. You send your own messages. Public forum replies are drafted for your team lead to post.
- Before changing a message or a reply in the CRM screen by hand, add the old one as a note first, then update the field.
- Keep contact details in the CRM only. Do not paste them into chats.
- The process is a draft and may change.
