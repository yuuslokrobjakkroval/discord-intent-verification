# 05 — Review Process & Thresholds

> Discord’s current review guidance uses unique reachable users, not the historical 100-server threshold. App Verification and Privileged Intent Review are separate processes.

---

## Determine whether review is required

Discord’s current pages describe this operating model:

- **Below 10,000 unique users:** the relevant Developer Portal toggles may remain self-serve.
- **At or above 10,000:** Discord notifies the app or team owner and shows a Developer Portal notice.
- **After notification:** the owner has 90 days to submit the privileged-intent request.
- **Previously reviewed access:** annual reapplication is required after Discord gives notice.
- **Timely submission:** current access is retained while a timely request is under review, according to Discord’s guidance.
- **During review:** the app can continue joining servers and growing under the current process.

Discord says the count means unique users with access to the app across all installed servers. It does not display the live app user count in the Developer Portal; use Discord’s notification and portal alert as the action signal.

## App Verification is separate

Do not treat these as one approval:

| Track | What it answers |
|---|---|
| App Verification | Whether the application meets Discord’s verification and larger-application requirements |
| Privileged Intent Review | Whether the app has demonstrated the need for specific privileged data categories |

Keep application identity, support contact, privacy policy, terms, and production feature descriptions consistent across both submissions, but record each status independently.

## The current workflow

### 1. Audit the actual code and product

For each intent, record:

- event or API field used;
- feature and user journey;
- who benefits;
- frequency and volume;
- alternative considered;
- why that alternative fails;
- storage and retention;
- security and access controls;
- deletion process; and
- evidence URL, screenshot, or video.

### 2. Remove unnecessary access

Discord’s review guide calls taking stock of actual data needs the most important preparation step. Turning off one unused intent is better than submitting a broad “all intents” request that cannot be demonstrated.

### 3. Write specific answers

Use feature names, triggers, event/field names, alternative analysis, data flow, retention, security, and evidence. A library setting is not a product explanation.

### 4. Configure both sides

Enable the exact categories in the portal and request the same exact categories in the client Identify configuration. Reviewed apps should use only access Discord has granted.

### 5. Test production-like behavior

Verify the expected payloads, test with each intent off, check every shard, and confirm no hidden code path depends on unapproved data.

### 6. Stay ready for annual review

Keep evidence and the use-case matrix current. Reapply within the 90-day window after notice, and remove access that the product no longer needs.

## Historical guidance to ignore

Older sources commonly say:

- under 100 servers can self-enable;
- 100 servers requires verification;
- intent review is part of app verification; or
- growth is blocked during review.

Current official 2026 guidance instead describes 10,000 unique reachable users, annual reapplication, separated review tracks, and continued growth during review.

## Key takeaway

Treat notification, the 90-day deadline, the annual cycle, and each intent decision as explicit product operations—not as a one-time checkbox.