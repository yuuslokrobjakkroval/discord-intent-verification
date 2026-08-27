# 08 — Privacy & Developer Policy

> Intent access is scoped permission to use data for the app’s permitted functionality. It is not ownership of Discord data and is not permission to repurpose it.

---

## Core policy controls

Discord’s Developer Policy and Developer Terms require developers to keep the following in view:

- use API Data only as necessary for the app’s stated functionality;
- do not scrape Discord Data;
- do not bypass or circumvent Discord privacy, safety, or security features;
- respect a user’s decision to block or remove the app;
- do not disclose Discord Data without specific, informed consent;
- do not retain data longer than necessary;
- protect API data and use it only for permitted functionality;
- provide a way for users to report issues or violations and review those reports; and
- do not use message content obtained through Discord APIs to train ML/AI models, including LLMs, without Discord’s express permission.

Terms and policies can change. The live documents control over this summary.

## Data-flow statement

Write the real flow, not a broad promise:

> Receive **[event/field]** → process **[purpose]** → produce **[action/result]** → delete raw data **[when/how]** → retain only **[derived result]** for **[why/period]**.

State whether data:

- stays inside your infrastructure;
- is sent to a service provider;
- is encrypted in transit and at rest;
- is visible to moderators, staff, or end users;
- is cached or persisted; and
- is deleted automatically or through a user/server control.

## Minimize by intent

### Guild Members

Prefer a user option, mention, or targeted lookup for a selected member. If all-member events or reconciliation are necessary, state why and avoid retaining a complete roster longer than required.

### Guild Presences

Avoid silent behavioral histories. If a live transition drives a feature, collect only the fields that drive the action and explain who can see the outcome.

### Message Content

List the fields actually used. Do not call a broad message subscription “narrow” if the Gateway receives a broader surface. State whether raw content leaves your infrastructure and address the no-ML/AI-training rule explicitly when relevant.

## Installation and permission clarity

Keep these facts distinct:

1. installation authorization;
2. normal bot permission bits;
3. Gateway privileged-intent authorization; and
4. the runtime Identify request.

User-installed command apps, bot-installed server apps, and HTTP interaction endpoints have different data and visibility boundaries. Describe the one you actually ship.

## Security statements

A useful security section identifies:

- where tokens and keys are kept;
- who can access raw data;
- encryption and transport protections;
- provider/subprocessor boundaries;
- audit logging without sensitive payloads;
- deletion controls; and
- how users report privacy or abuse concerns.

Never put a bot token, interaction token, private key, or credential in a screenshot, recording, public repository, or review response.

## Key takeaway

Reviewers should see the same data practice in the code, privacy policy, evidence packet, and production behavior. Minimize first, disclose clearly, and delete what the feature does not need.