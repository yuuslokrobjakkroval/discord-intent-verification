# 04 — Message Content Intent

> `MESSAGE_CONTENT` controls access to content-bearing fields in message objects. It is broader than the plain text of `messageCreate`, so describe the exact fields and scope your feature needs.

---

## What it unlocks

Discord’s current documentation calls out fields including:

- `content`;
- `embeds`;
- `attachments`;
- `components`; and
- polls, subject to the live schema and current exceptions.

The intent affects message data surfaces, including API message objects. A message object existing does not mean every content-bearing field will be populated.

## Stronger use cases

Examples that may require the intent when no interaction-first design works:

- real-time moderation that scans arbitrary messages for phishing links, scams, malware, or policy violations;
- a safety feature that must inspect messages not directed at the app before a user explicitly invokes it; or
- a genuinely content-dependent workflow that needs arbitrary user-authored messages and cannot be represented by an interaction.

Legacy prefix commands are a weak long-term justification when slash commands or modals can capture the same input.

## Weak explanations

These do not establish necessity:

- “My bot needs message content.”
- “We need it for commands.”
- reading every message for analytics, advertising, profiling, or unrelated collection;
- requesting it because a framework sample enabled it; or
- using it for a message context command when the selected message is already in the interaction payload.

## Alternatives to test first

| Workflow | Interaction-first option |
|---|---|
| Structured command input | Slash command with typed options and autocomplete |
| Act on one selected message | Message context command |
| Act on one selected member | User context command or user option |
| Collect free-form text after an intentional action | Modal text input |
| Choose a bounded action | Button or select menu |

Some messages directed at, authored by, or replying to the app can be available under documented exceptions. Check the current [alternative guide](https://docs.discord.com/developers/gateway/you-might-not-need-a-privileged-intent) before depending on an exception; do not generalize it to arbitrary guild history.

## The AI/ML policy restriction

Discord’s Developer Policy says message content obtained through its APIs must not be used to train machine-learning or AI models, including LLMs, without Discord’s express permission. If raw content leaves your infrastructure for an AI service, review this restriction before applying.

Do not use a moderation request to justify unrelated training, advertising, profiling, scraping, or analytics.

## What a strong answer should contain

1. Name the content-dependent feature.
2. State whether you need arbitrary guild messages, selected messages, DMs, mentions, or your own messages.
3. List the exact fields: for example, `content` and `embeds`, but not attachments or polls.
4. Explain why slash commands, context menus, components, or modals cannot provide the trigger.
5. Describe the data flow: receive → process → result → discard/store.
6. State whether raw content leaves your infrastructure, how it is protected, retention, and deletion.
7. State that it is not used for unrelated analytics, advertising, profiling, scraping, or prohibited model training.
8. Include live screenshots or video that demonstrate the feature and its necessity.

### Reusable answer pattern

> We request **Message Content** for **[feature]**. When **[arbitrary message/event]** occurs, the app reads **[exact fields]** to **[user-visible result]**. We tested **[slash command/context menu/modal/component]**, but it cannot **[specific missing capability]** because the feature must **[observe arbitrary content without an explicit invocation]**. We process only **[scope]**, retain **[minimal derived result or none]** for **[period]**, delete it by **[mechanism]**, restrict access to **[roles/services]**, and do not use the content for unrelated purposes or AI/ML training without express permission.

## Controlled testing

Test at least:

- a DM;
- a guild message that mentions the bot;
- the bot’s own message; and
- a non-mention user message in a guild.

These cases help distinguish documented exceptions from actual arbitrary-message access. An empty field may be an intentional privacy boundary rather than a bad token or missing channel permission.

## Key takeaway

Message Content survives an alternative audit only when the product must observe content without an explicit user interaction. Narrow the fields, channels, lifecycle, and evidence as much as the feature allows.