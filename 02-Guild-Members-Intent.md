# 02 — Guild Members Intent

> Request `GUILD_MEMBERS` when a feature genuinely depends on observing or reconciling members broadly or in real time—not merely because a client library has a member cache.

---

## What it unlocks

According to Discord’s documentation, the intent can provide:

- real-time member join events;
- member profile, role, and nickname-related updates exposed by the Gateway;
- member leave/removal events;
- Request Guild Members operations and member-list retrieval/chunking; and
- broader member-list access subject to Discord’s limits and endpoint behavior.

The event reference distinguishes a known-member lookup, a prefix search, and a complete roster request. Explain which operation your product uses.

## Stronger use cases

These are practical examples that may justify the intent when the implementation and data handling match:

- An onboarding service must react to **every** member join in real time.
- A moderation or safety service must react to member removal or role updates.
- An access-control system must reconcile **all** current members with an external authorization system.
- A disclosed feature requires a complete roster and cannot operate from user-selected IDs or targeted lookups.

These are examples, not an approval guarantee.

## Weak explanations

The following do not explain necessity by themselves:

- “We want a member cache because it is convenient.”
- “The tutorial enables members by default.”
- “We have a `/userinfo` command.”
- “We need to know everyone in the server.”
- “We need it for future features.”

If a command receives a selected user, mention, or user option, the interaction often already supplies the target.

## Alternatives to test first

| Need | Prefer this first |
|---|---|
| Look up a known member ID | Get Guild Member |
| Search by username or nickname prefix | Search Guild Members |
| Target a user selected by an administrator | Slash-command user option or user context command |
| Target a mentioned user | Interaction data or a targeted lookup |
| Read the invoking member | The interaction payload |

An alternative is not a reason to claim that the intent is impossible; explain the exact capability it lacks. For example, a targeted lookup cannot substitute for receiving every join event.

## What a strong answer should contain

Use this structure in the application:

1. **Feature and trigger:** name the feature and what starts it.
2. **Exact dependency:** name `GUILD_MEMBER_ADD`, `GUILD_MEMBER_UPDATE`, `GUILD_MEMBER_REMOVE`, or Request Guild Members.
3. **Completeness:** state whether you need every event, a full roster, or both.
4. **Alternative analysis:** explain why user options, mentions, search, or targeted REST cannot cover this workflow.
5. **Scope and frequency:** state which servers/modules are enabled and how often full retrieval occurs.
6. **Lifecycle:** say whether member data is streamed, cached, persisted, or discarded, with retention and deletion behavior.
7. **Security:** state who can access it and how access is restricted.

### Reusable answer pattern

> We request **Guild Members** for **[feature]**. When **[member event or scheduled reconciliation]** occurs, the app uses **[member fields]** to **[user-visible outcome]**. A selected-user option and Get Guild Member cannot work because **[specific reason all members/events are required]**. We process only **[scope]**, retain **[minimal derived data or none]** for **[period]**, delete it by **[mechanism]**, and restrict access to **[roles/services]**.

## Operational limits to mention

Discord’s Gateway event documentation records limits around Request Guild Members:

- one `guild_id` per request;
- prefix queries return at most 100 members;
- `user_ids` requests remain limited to 100 members; and
- a full member-list request requires `GUILD_MEMBERS`.

If your design repeatedly enumerates every member, explain why that frequency is necessary and how you stay within request and rate limits.

## Key takeaway

A real-time all-member invariant is stronger than a cache convenience. Prove the invariant, use targeted access everywhere else, and request no additional privileged intent.