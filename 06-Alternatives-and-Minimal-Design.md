# 06 — Alternatives & Minimal Design

> Discord’s strongest design signal is interaction-first: let users explicitly choose the command, target, value, or text whenever that can replace broad Gateway data.

---

## Alternative map

| If the feature currently… | Evaluate this first |
|---|---|
| Parses `!command` text | Slash command with typed options |
| Acts on one message | Message context command |
| Acts on one user/member | User context command or user option |
| Needs free-form input after a user starts a workflow | Modal |
| Needs a bounded choice | Button or select menu |
| Looks up one known member | Get Guild Member |
| Searches by name prefix | Search Guild Members |
| Needs only a rough online total | `approximate_presence_count` |
| Is entirely command/component-driven | HTTP interactions endpoint |

The right alternative depends on the product. An interaction does not replace moderation that must inspect arbitrary messages before a user invokes the app, and a targeted member lookup does not replace receiving every join or leave event.

## Application commands

Discord’s official command model includes:

- slash commands;
- message context commands;
- user context commands; and
- Entry Point commands for Activities where appropriate.

Slash options can provide typed user, role, channel, mentionable, attachment, number, integer, boolean, and string input. Autocomplete helps users choose values without scanning arbitrary messages.

Command permissions and contexts can make a moderation workflow narrower than a broad message listener.

## Components and modals

Buttons and select menus send a component interaction with a `custom_id` and selected values. A modal gathers free-form input after an explicit user action. A typical minimal flow is:

1. receive the interaction;
2. validate user, guild, channel, permissions, and `custom_id`;
3. read only selected values or modal fields;
4. perform the action; and
5. store only a required audit result, discarding the original payload otherwise.

Components do not grant arbitrary message access and do not solve passive moderation.

## User-installed, command-only apps

Discord’s application and command documentation describes user-installed apps that are visible to the authorizing user and restricted to commands. If a product works in that context, it may not need a bot user, a persistent Gateway connection, or any privileged intent.

Do not call this equivalent to a server-wide bot. It constrains visibility and feature scope.

## HTTP interactions

An app can receive interactions through an outgoing HTTP webhook instead of the Gateway. These methods are mutually exclusive. An HTTP interaction endpoint can remove the need for a persistent Gateway client for command/component-driven products.

If you use this architecture:

- validate Discord signatures with the application public key;
- acknowledge promptly;
- treat interaction tokens as sensitive short-lived runtime data;
- validate payload structure and installation context; and
- avoid copying full payloads into permanent logs.

## Alternative analysis in the review form

Do not write “we use commands” and stop. State:

1. which primitive you evaluated;
2. what data it supplies;
3. what exact capability is missing; and
4. why the requested intent is the narrowest remaining path.

### Example: selected message

> We use a message context command because a moderator selects one message and asks the app to classify it. The selected message is supplied in the interaction; we do not subscribe to arbitrary guild messages.

### Example: arbitrary moderation

> We cannot use a message command because the safety feature must evaluate arbitrary user messages before a user invokes the app. The app is limited to the server’s configured moderation channels and discards raw content after classification.

## Key takeaway

An alternative-first audit can eliminate a privileged intent entirely. When it cannot, it gives the reviewer a concrete reason why the remaining request is necessary.