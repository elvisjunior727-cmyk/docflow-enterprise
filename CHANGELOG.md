# Changelog

## 3.0.1
- Fixed authenticated downloads/exports in the web UI.
- Fixed confidence rendering and workflow trigger consistency.
- Enforced workflow approval behavior for review-risk documents.
- Added invite/password-reset/SSO link handling in the web UI.
- Added webhook URL validation and safer Paystack workspace attribution.
- Restricted bulk exports to administrators.
- Added a deployment verification checklist.

## 2.0.0
- Added durable S3-compatible object storage adapter
- Added PostgreSQL-backed processing queue and webhook delivery retries
- Added checksums and document usage enforcement
- Added configurable extraction schemas
- Added team invitations and member lifecycle controls
- Added optional TOTP MFA
- Added password reset flow
- Added OIDC SSO flow with nonce/state handling
- Added SCIM-style provisioning endpoints and token rotation
- Added encrypted integration/application secrets
- Added integration registry
- Added retention policies and automated cleanup
- Added readiness and enterprise-control status endpoints
- Added scoped API keys
- Expanded enterprise dashboard and admin UI


## 3.0.0 — Enterprise finalization

- Hardened upload validation with file-signature checks.
- Added dedicated authentication and upload rate limits.
- Added extraction validation and human-correction version history.
- Approval-gated workflows now wait for approval before dispatching downstream webhooks.
- Added workflow resume jobs after approval decisions.
- Added one-time SSO exchange codes instead of placing JWTs in callback URLs.
- Added public OIDC workspace sign-in start and additional SCIM discovery endpoints.
- Added Stripe and Paystack webhook handling with signed event verification and idempotency records.
- Added usage, operations, JSON export and document reprocessing endpoints.
- Added safer team/owner account protections and API scope allowlisting.
- Updated deployment/environment documentation for enterprise operations.
