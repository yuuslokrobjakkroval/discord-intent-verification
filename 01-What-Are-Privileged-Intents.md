# 01 — What Are Privileged Intents?

> Privileged intents are data-access categories on Discord’s Gateway. They are not normal bot permissions, and enabling a portal toggle alone does not make a feature necessary or make the running client request the data.

---

## The three privileged intents

| Intent | Main data surface | Typical events or operations |
|---|---|---|
| `GUILD_MEMBERS` | Guild member joins, updates, removals, and broader member retrieval | `GUILD_MEMBER_ADD`, `GUILD_MEMBER_UPDATE`, `GUILD_MEMBER_REMOVE`, Request Guild Members |
| `GUILD_PRESENCES` | Individual online state, status, activity, and presence changes | `PRESENCE_UPDATE` |
| `MESSAGE_CONTENT` | Message content fields such as content, embeds, attachments, components, and polls | Applies to relevant message objects and Gateway data; it is not simply another event subscription |

The exact fields and exceptions can change. Use the live [Gateway Intents documentation](https://docs.discord.com/developers/events/gateway#gateway-intents) and [Message Resource](https://docs.discord.com/developers/resources/message) reference for protocol details.

## Four separate access layers

A reliable review and debugging plan keeps these facts separate:

1. **Product necessity** — a real user-facing feature needs the data.
2. **Discord-side authorization** — the Developer Portal toggle and, where required, Discord’s review grant allow the category.
3. **Gateway request** — the client library includes the exact intent in its Identify payload.
4. **Normal Discord permissions** — permissions such as `VIEW_CHANNEL` or `SEND_MESSAGES` limit actions and visibility but do not grant privileged intent access.

An app can have Administrator permission and still receive a disallowed-intent error. An app can have a portal toggle enabled and still receive no data if its client does not request the bit.

## Portal and code must agree

The normal path is:

1. Open **Developer Portal → your application → Bot → Privileged Gateway Intents**.
2. Enable only the intents the product audit supports.
3. If Discord requires review, request only those same intents.
4. Configure the library/client to request the same exact set at startup.
5. Reconnect and test production-like events and fields.

Do not turn on every default provided by a library tutorial. Library defaults are implementation conveniences, not evidence that your product needs those data categories.

## Current process in brief

Discord’s current guidance describes a review trigger based on **10,000 unique users who have access to the app across all installed servers**, rather than the old 100-server rule. The owner is notified and receives a 90-day submission window. Existing reviewed access is subject to annual reapplication after Discord gives notice.

App Verification and Privileged Intent Review are now separate tracks. Treat them as separate states even if the same app is dealing with both.

## Key takeaway

The strongest request is not “the framework needs this intent.” It is:

> “This named feature uses this specific event or field to produce this user-visible result; we tested this alternative and it cannot provide the required capability; here is our minimal data lifecycle and evidence.”

Continue with the page for the specific intent you actually need:

- [Guild Members](./02-Guild-Members-Intent.md)
- [Guild Presences](./03-Guild-Presences-Intent.md)
- [Message Content](./04-Message-Content-Intent.md)