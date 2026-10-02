# DocFlow Enterprise 3.0 deployment

## Render

Use the included `render.yaml`, or create a PostgreSQL database and Node web service manually.

Required environment variables in production:

- `DATABASE_URL`
- `JWT_SECRET`
- `ENCRYPTION_KEY`
- `APP_BASE_URL`
- `S3_BUCKET`
- `S3_REGION`
- `S3_ENDPOINT` when using an S3-compatible provider rather than AWS
- `S3_ACCESS_KEY_ID`
- `S3_SECRET_ACCESS_KEY`

Recommended service integrations:

- `AI_API_KEY` + `AI_BASE_URL` + `AI_MODEL`
- `OCR_API_URL` + `OCR_API_KEY`
- SMTP variables for invitations and password resets
- Stripe or Paystack variables for billing
- OIDC variables for SSO
- `SCIM_TOKEN_SECRET` for SCIM administration

## Object storage

Local filesystem storage is acceptable for local development only. In production, configure S3/R2/B2-style object storage. DocFlow stores the object key in PostgreSQL and streams the original file from the object store when downloaded.

## Operational checklist

1. Deploy.
2. Open `/api/health` and confirm database connectivity.
3. Open `/api/readiness` and resolve missing required production controls.
4. Create a test workspace and upload a sample invoice.
5. Confirm the background queue changes the document from `queued` to `processed`.
6. Confirm approval and webhook workflow behavior.
7. Confirm a document can be downloaded after the object-store configuration.
8. Configure monitoring for 5xx errors, failed jobs, storage failures and webhook failures.
9. Configure database backups and verify a restore procedure.
10. Run a security review before onboarding sensitive enterprise customers.


## Before enterprise production

Use durable encrypted object storage, managed PostgreSQL backups, a tested restore process, centralized logging/alerts, and independent security testing. Configure the customer identity provider before enabling SSO/SCIM. Treat the readiness endpoints as deployment gates, not as a certification claim.
