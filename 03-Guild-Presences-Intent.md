# 03 — Guild Presences Intent

> `GUILD_PRESENCES` exposes individual presence updates. It is the least replaceable intent for live individual presence, but “we want a dashboard” is still not a complete necessity argument.

---

## What it unlocks

The intent provides access to `PRESENCE_UPDATE` data such as:

- online/offline state;
- user status changes;
- activity or Rich Presence information; and
- platform/status details included by Discord in the presence payload.

Describe the exact transition you observe and the action it triggers.

## Stronger use cases

A request is easier to understand when the product’s primary function depends on an individual presence transition, for example:

- a user-facing workflow reacts to a member becoming online or offline;
- a server tool triggers a defined action when a presence changes; or
- an operational feature uses live activity as its actual signal and no equivalent event or endpoint exists.

The use case must still be bounded, visible, and consistent with your privacy notice.

## Weak or risky explanations

These statements need more evidence and often point to a design problem:

- “We want to show online members.”
- “We need it for statistics.”
- “We need all intents for future features.”
- “We want to track activity.”

Discord’s alternative guide says approximate presence counts are available on a Guild object. A cosmetic dashboard or behavioral history should not be presented as a necessary live-presence feature without explaining the product action, visibility, retention, and controls.

## Alternatives and boundaries

- Use `approximate_presence_count` when an aggregate estimate is enough.
- Setting the bot’s own status or activity does **not** require Guild Presences.
- Redesign around an explicit command, button, or other user action when presence is only a proxy for intent.
- Discord documents that equivalent individual real-time presence data is not available through another endpoint. This can strengthen a genuine presence-dependent case, but it does not make vague monitoring acceptable.

## What a strong answer should contain

1. Name the exact presence transition.
2. Explain the user-facing behavior that depends on it.
3. Explain why an approximate count cannot provide that behavior.
4. State whether activity data is stored or discarded.
5. Describe visibility, deletion, retention, and access restrictions.
6. Explain how the design avoids silently building a behavioral history.

### Reusable answer pattern

> We request **Guild Presences** for **[feature]**. On **[specific presence transition]**, the app **[user-visible action]**. An approximate guild-level count cannot work because **[specific missing individual signal]**. We process only **[scope]**, do not retain more activity history than necessary, delete **[data]** after **[period/event]**, and expose the result only to **[authorized audience]**.

## Privacy controls

If a feature genuinely needs history:

- collect only the fields that drive the feature;
- set a short retention period;
- make the server/user control clear;
- do not use presence as hidden surveillance;
- restrict staff or service access; and
- document deletion and report handling.

## Key takeaway

Show the exact action caused by `PRESENCE_UPDATE`. A count, status badge, or “future analytics” claim is not the same as a bounded, necessary real-time workflow.