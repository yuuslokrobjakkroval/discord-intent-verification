# 10 — Rejection, Resubmission & Annual Readiness

> A denial is a signal to audit the product and data flow, not an invitation to disguise the same collection through another route.

---

## Common denial patterns and fixes

| Review concern | Better response |
|---|---|
| No demonstrated necessity | Remove the intent or document why every viable alternative fails |
| Interaction could replace it | Migrate to slash commands, context menus, components, or modals |
| Submission unclear or incomplete | Add the user journey, exact events/fields, lifecycle, security, and evidence |
| Policy inconsistency | Stop the offending use and redesign before resubmitting |
| Data practice concern | Minimize, delete, segregate access, disclose, and explain controls |
| Evidence does not show the claim | Record the live feature, including the trigger and result |

## If access is denied

1. Read Discord’s notice carefully; it controls whether access remains during remediation.
2. Do not assume the issue is a technical toggle.
3. Map every denial phrase to a concrete product or documentation change.
4. Request only the intents that survive the new audit.
5. Include before/after behavior if the feature changed.
6. Attach live screenshots or video, not only architecture diagrams.
7. Submit within any deadline Discord gives if current access is at risk.
8. Keep the app functional without the intent where possible.

Depending on the notice, some cases may allow correction and resubmission while access remains; other policy-inconsistent cases may remove access while allowing a new request later.

## Never bypass a denial

Do not:

- disguise the same data collection as a different feature;
- scrape or retrieve data outside the approved path;
- use user-account automation;
- request an unapproved Gateway flag;
- claim a context-menu exception provides arbitrary message history; or
- retain data longer than the stated purpose requires.

## Annual readiness

Keep a living review packet:

- current product description;
- intent matrix;
- code/configuration audit;
- privacy and retention statement;
- user/server controls;
- current screenshots/video;
- provider and security details;
- list of unused intents removed; and
- change log for features that alter data access.

When Discord notifies you of annual reapplication, use the 90-day window and ensure the request matches the current production build—not an old demo.

## Acceptance is use-case-specific

The reviewed sources do not provide a reliable public acceptance-rate table or a universal “magic wording.” An approval for one app does not establish that another app with the same intent will be approved. Public anecdotes can reveal questions and symptoms, but current Discord documentation controls.

## Key takeaway

The best resubmission answers the stated denial reason directly, narrows the product where appropriate, and makes the feature/data relationship visible.