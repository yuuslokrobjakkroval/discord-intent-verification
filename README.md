<div align="center">

# Discord Privileged Intent Verification Guide

**A practical, evidence-led guide to deciding whether your app needs privileged Gateway intents and preparing a clear Discord review request.**

[![Discord Developer Docs](https://img.shields.io/badge/Source-Discord%20Developer%20Docs-5865F2?style=flat-square&logo=discord&logoColor=white)](https://docs.discord.com/developers/gateway/getting-started-with-privileged-intent-review)
[![Research](https://img.shields.io/badge/Research%20sources-37-5865F2?style=flat-square)](./11-Source-Register.md)
[![Status](https://img.shields.io/badge/Status-Living%20guide-2ea44f?style=flat-square)](./05-Review-Process-and-Thresholds.md)

</div>

---

## What this guide covers

Discord currently treats **Guild Members**, **Guild Presences**, and **Message Content** as privileged Gateway intents. This guide explains:

- what data each intent exposes;
- when the current user-based review process applies;
- how to design around an intent with interactions or targeted API calls;
- how to explain necessity, data handling, retention, and security;
- how to configure the Developer Portal and Gateway client consistently;
- how to test missing data and diagnose Gateway errors; and
- how to prepare for denial, resubmission, and annual reapplication.

The guide is based on 37 official, library, and community sources documented in the [source register](./11-Source-Register.md). Official Discord documentation controls when a community or library source conflicts with it.

## Current rules at a glance

| Topic | Current guidance |
|---|---|
| Privileged intents | Guild Members, Guild Presences, and Message Content |
| Review trigger | Discord describes 10,000 unique users with access to the app across installed servers |
| Under the threshold | Required toggles remain available in the Developer Portal, but unnecessary data access is still a policy risk |
| Notification window | Discord gives the owner 90 days from notification to submit |
| Existing reviewed access | Annual reapplication after Discord gives notice; timely submissions retain current access while under review |
| App verification | Separate from privileged-intent review |
| Growth during review | Current guidance says the app can continue joining servers and growing while review is pending |
| Best approval strategy | Prove necessity, request the narrowest set, explain the data lifecycle, and show the feature working |

> **Important:** Older guides often say “100 servers.” That is historical guidance. Use Discord’s live review documentation for thresholds, deadlines, and status.

## Documentation

| # | Page | What it covers |
|---|---|---|
| 1 | [What Are Privileged Intents?](./01-What-Are-Privileged-Intents.md) | The three intents and the four separate access layers |
| 2 | [Guild Members Intent](./02-Guild-Members-Intent.md) | Member events, roster access, alternatives, and strong justifications |
| 3 | [Guild Presences Intent](./03-Guild-Presences-Intent.md) | Real-time presence data, necessity, privacy, and aggregate alternatives |
| 4 | [Message Content Intent](./04-Message-Content-Intent.md) | Message fields, arbitrary-message use cases, alternatives, and the AI/ML restriction |
| 5 | [Review Process & Thresholds](./05-Review-Process-and-Thresholds.md) | The current process, deadlines, notifications, and annual reapplication |
| 6 | [Alternatives & Minimal Design](./06-Alternatives-and-Minimal-Design.md) | Slash commands, context menus, components, modals, REST, and HTTP interactions |
| 7 | [Submission Evidence & Form](./07-Submission-Evidence-and-Form.md) | Strong answers, evidence packets, and the supplied Developer Portal screenshots |
| 8 | [Privacy & Developer Policy](./08-Privacy-and-Developer-Policy.md) | Data minimization, storage, disclosure, security, deletion, and policy consistency |
| 9 | [Implementation & Troubleshooting](./09-Implementation-and-Troubleshooting.md) | Portal/client configuration, events, tests, and Gateway 4013/4014 diagnosis |
| 10 | [Rejection, Resubmission & Annual Readiness](./10-Rejection-Resubmission-and-Annual-Readiness.md) | How to respond to denial reasons without bypassing Discord’s controls |
| 11 | [Source Register](./11-Source-Register.md) | All 37 sources, evidence labels, and historical-source cautions |
| 12 | [Pre-Submission Checklist](./12-Pre-Submission-Checklist.md) | A complete product, policy, evidence, and runtime checklist |

## Start here

1. Read [What Are Privileged Intents?](./01-What-Are-Privileged-Intents.md).
2. Audit the actual data your app uses with the matrices in the intent-specific pages.
3. Read [Alternatives & Minimal Design](./06-Alternatives-and-Minimal-Design.md) before requesting Message Content or Guild Members.
4. Prepare the [submission evidence packet](./07-Submission-Evidence-and-Form.md).
5. Run the [pre-submission checklist](./12-Pre-Submission-Checklist.md).

## Evidence labels

- **[OFFICIAL]** — directly from Discord documentation or Discord Developer Support.
- **[LIBRARY]** — maintainer documentation about implementing Discord behavior.
- **[COMMUNITY]** — an issue, discussion, gist, or developer report; useful for symptoms and patterns, not a policy guarantee.
- **[INFERENCE]** — a practical conclusion derived from multiple sources. It is not a Discord-published rule.

## Supplied Developer Portal examples

The screenshots are stored with descriptive names in [`assets/`](./assets/):

- [Request Intents overview](./assets/Request-Intents-Overview.jpg)
- [Guild Members form](./assets/Guild-Members-Intent-Form.jpg)
- [Guild Presences form](./assets/Guild-Presences-Intent-Form.jpg)
- [Message Content form](./assets/Message-Content-Intent-Form.jpg)

They are visual references only. Do not copy private data into an evidence packet or submit screenshots containing tokens, private keys, or unrelated user data.

---

> Discord’s policies and Developer Portal change over time. Re-check the linked official pages immediately before submitting or reapplying. This guide is independent and is not affiliated with Discord.