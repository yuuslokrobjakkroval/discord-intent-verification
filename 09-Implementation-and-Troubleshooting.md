# 09 — Implementation & Troubleshooting

> Portal authorization, client configuration, and runtime behavior are separate checks. Diagnose them separately.

---

## Configure the portal and client

1. Enable only the required intent in **Developer Portal → Bot → Privileged Gateway Intents**.
2. Request the same exact flags in the client’s Identify configuration.
3. Keep every shard/process on the same approved configuration.
4. Reconnect after changing portal settings.
5. Test the actual event and fields, not just a successful `READY`.

A code flag cannot bypass Discord authorization. A portal toggle does not automatically change code.

## Library configuration principles

Library documentation can lag Discord policy. Use the installed version’s API names, but use Discord’s current review guide for thresholds and deadlines.

- **discord.js:** use the version-specific `GatewayIntentBits`/client options and request the minimal set.
- **discord.py:** pass an `Intents` object and enable only the flags the product uses.
- **nextcord/Pycord:** configure the corresponding members, presences, or `message_content` flags explicitly.
- Avoid `Intents.all()` or framework “default intents” unless every selected flag is independently justified.

## Gateway close codes

### 4013 — Invalid intent

Check:

- numeric bitfield;
- library version and constant names;
- unsupported or deprecated bits;
- Identify payload encoding; and
- copied examples that use a different library version.

### 4014 — Disallowed intent

Check:

- Developer Portal toggle;
- review or annual access state;
- whether the app is entitled to use that intent;
- the exact flags the running process requests; and
- every shard/client configuration.

Reconnect after portal changes and test one change at a time.

## No close, but no data

If the Gateway stays connected but fields or events are missing:

- confirm the exact intent is requested at startup;
- confirm the event is delivered by that intent;
- inspect member cache settings separately from authorization;
- test the documented Message Content exceptions;
- check channel visibility and normal Discord permissions; and
- inspect the effective outbound Identify configuration rather than only a local schema file.

## Test matrix

| Test | What it distinguishes |
|---|---|
| DM message | documented DM/content exception behavior |
| Bot mention in a guild | mention exception versus arbitrary guild content |
| Bot’s own guild message | own-message behavior versus general access |
| Non-mention user message in a guild | actual Message Content request/authorization |
| `GUILD_MEMBER_ADD`/`REMOVE` | member-event dependency |
| Known-user lookup | targeted REST path that may remove the member dependency |
| `PRESENCE_UPDATE` | actual presence dependency |
| Request Guild Members with query/user IDs | targeted limits versus full-roster requirement |
| Unapproved privileged flag in Identify | expected 4014 handling |

Test content-bearing and content-free cases through both Gateway and REST paths. Missing fields can be an intentional privacy boundary.

## Safe diagnostics

Log:

- configuration names;
- enabled feature modules;
- shard/session identifiers; and
- close codes and library versions.

Never log bot tokens, interaction tokens, private keys, raw message content, or unnecessary member/presence payloads.

## Key takeaway

When something fails, identify which layer failed: product design, Discord authorization, runtime request, or normal permissions. Fixing only one layer often leaves the same symptom in place.