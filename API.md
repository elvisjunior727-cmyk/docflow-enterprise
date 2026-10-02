# DocFlow API surface

All authenticated application routes accept `Authorization: Bearer <JWT>`.

Machine clients can use scoped `df_live_...` API keys. Valid scopes are `documents:read`, `documents:write`, `approvals:read`, `workflows:read`, `workflows:write`, `exports:read`.

## Documents

`GET /api/documents` — list/search documents

`POST /api/documents/upload` — upload one or more PDF/image files

`GET /api/documents/:id` — inspect document metadata and extracted data

`GET /api/documents/:id/download` — stream the original file

`DELETE /api/documents/:id` — admin deletion

`GET /api/export/documents.csv` — workspace CSV export

## Automation

`GET /api/workflows`

`POST /api/workflows`

`PATCH /api/workflows/:id`

`DELETE /api/workflows/:id`

`GET /api/workflow-runs`

## Governance

`GET /api/approvals`

`POST /api/approvals/:id/decision`

`GET /api/audit`

`GET /api/security/settings`

`PATCH /api/security/settings`

## Identity

`GET /api/team`

`POST /api/team/invites`

`POST /api/team/invites/accept`

`PATCH /api/team/users/:id`

`POST /api/security/mfa/setup`

`POST /api/security/mfa/confirm`

`POST /api/security/mfa/disable`

`POST /api/oidc/start`

`POST /api/scim/token`

SCIM endpoints use the form `/scim/v2.0/:organization-slug/Users` with a SCIM bearer token.

## Integrations and schemas

`GET /api/integrations`

`POST /api/integrations`

`DELETE /api/integrations/:id`

`GET /api/schemas`

`POST /api/schemas`

## Operations

`GET /api/health`

`GET /api/readiness`

`GET /api/enterprise/readiness`


## Reliability and enterprise operations

`POST /api/documents/:id/reprocess` — queue a document for another extraction attempt.

`POST /api/documents/:id/correct` — save a human correction as a new document version.

`GET /api/documents/:id/versions` — review document correction history.

`GET /api/usage` — plan limits and current usage.

`GET /api/operations` — queue, webhook and workflow operational counters for admins.

`GET /api/export/documents.json` — structured workspace export (requires `exports:read`).

`POST /api/auth/sso/exchange` — exchange a short-lived one-time SSO code for an application session.

`POST /api/oidc/start-public` — begin SSO for a workspace slug.

`POST /api/billing/stripe/webhook` — signed Stripe subscription events.

`POST /api/billing/paystack/webhook` — signed Paystack payment events.

SCIM also exposes `ServiceProviderConfig` and `ResourceTypes` endpoints.
