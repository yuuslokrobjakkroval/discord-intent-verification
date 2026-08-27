# 12 — Pre-Submission Checklist

> Complete this checklist against the production build. An unchecked item is a reason to pause and audit—not a reason to make the request broader.

---

## Product and necessity

- [ ] I can name the exact user-facing feature for every requested intent.
- [ ] I mapped every event, operation, and field to that feature.
- [ ] I tried slash commands, context commands, buttons, selects, modals, user-installed commands, and targeted REST where relevant.
- [ ] I can explain the specific capability each alternative lacks.
- [ ] I removed every intent that is only convenient, tutorial-driven, or intended for future features.
- [ ] My application page, commands, privacy policy, code, and evidence describe the same product.

## Guild Members

- [ ] I explained whether I need join, update, remove, full-roster, or Request Guild Members behavior.
- [ ] I explained why a user option, mention, search, or targeted lookup cannot cover the workflow.
- [ ] I accounted for member-list limits, query frequency, and rate limits.
- [ ] I minimize or discard member data and have a deletion process.

## Guild Presences

- [ ] I named the exact `PRESENCE_UPDATE` transition I observe.
- [ ] I explained the user-facing action it triggers.
- [ ] I explained why `approximate_presence_count` is insufficient.
- [ ] I do not silently build a behavioral history.
- [ ] I documented visibility, retention, deletion, and access restrictions.

## Message Content

- [ ] I named the exact required fields: content, embeds, attachments, components, polls, or another documented field.
- [ ] I stated whether I need arbitrary guild messages, selected messages, mentions, DMs, or my own messages.
- [ ] I explained why a slash command, context menu, component, or modal cannot provide the required trigger.
- [ ] I documented receive → process → result → delete/store.
- [ ] I stated whether raw content leaves my infrastructure.
- [ ] I addressed the prohibition on using Discord API message content for ML/AI training without express permission.
- [ ] I tested DM, mention, own-message, and non-mention guild-message cases.

## Portal, client, and runtime

- [ ] I enabled only the required intents in Developer Portal → Bot → Privileged Gateway Intents.
- [ ] My client requests the same exact intent set in Identify.
- [ ] Every shard/process uses a consistent approved configuration.
- [ ] I handle missing/empty message content and absent events safely.
- [ ] I can distinguish 4013 Invalid intent from 4014 Disallowed intent.
- [ ] I tested the feature with each privileged intent disabled.
- [ ] I do not log bot tokens, interaction tokens, private keys, raw content, or unnecessary payloads.

## Privacy and policy

- [ ] My privacy policy explains Discord data use accurately.
- [ ] I collect only what the stated feature needs.
- [ ] I do not scrape Discord Data or bypass privacy, safety, or security features.
- [ ] I respect block/removal decisions.
- [ ] I do not disclose Discord Data without specific informed consent.
- [ ] I retain data only as long as necessary.
- [ ] I documented encryption, access controls, service providers, and deletion.
- [ ] Users have a clear issue/violation report path.

## Evidence packet

- [ ] I wrote a one-paragraph product description in plain language.
- [ ] I completed an intent-to-feature matrix.
- [ ] I included alternatives and specific reasons they fail.
- [ ] I included current screenshots or a short recording of the live feature.
- [ ] The evidence shows the trigger and user-visible result.
- [ ] The screenshots/video contain no tokens, private keys, or unrelated private data.
- [ ] The privacy-policy link is accessible to a reviewer.
- [ ] The evidence matches the current production build.

## Process and timing

- [ ] I know whether Discord has notified me that review is required.
- [ ] If notified, I am within the 90-day submission window.
- [ ] I am tracking app verification and privileged-intent review separately.
- [ ] I have a plan for annual reapplication after Discord’s notice.
- [ ] I know what the app does if the request is denied.
- [ ] I will not bypass a denial with disguised collection, scraping, or an unapproved Gateway request.

## Final review

- [ ] I requested the narrowest set of privileged intents.
- [ ] Every answer is complete, accurate, current, and free of contradictions.
- [ ] The app can operate safely without the intent where possible.
- [ ] I re-checked the live Discord docs for policy, threshold, deadline, and schema changes.

> Ready means the request is specific, minimal, policy-consistent, and demonstrable—not merely that the portal toggles are on.