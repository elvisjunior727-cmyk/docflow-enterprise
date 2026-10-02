# DocFlow Enterprise 3.0

DocFlow is a standalone enterprise document intelligence and automation platform. It turns PDFs, scans and business documents into structured data, governed decisions and downstream business actions.

## What is included

### Document intelligence
- PDF and image intake, including bulk upload
- SHA-256 checksum tracking
- PDF text extraction
- Optional OCR for scanned documents/images
- AI extraction through an OpenAI-compatible API
- Deterministic fallback when AI/OCR is unavailable
- Auto document classification
- Configurable extraction schemas
- Confidence and risk signals
- Document inspector and original-file download
- CSV export

### Automation and operations
- Database-backed job queue with retries
- Event-driven workflows
- Approval gates
- High-risk approval policy
- Signed webhook deliveries with retry records
- Workflow run history
- SMTP notifications
- Integrations registry for ERP/CRM/accounting/custom connections

### Enterprise identity and security
- Workspace/tenant isolation
- Owner/admin/member/viewer permissions
- Scoped machine API keys
- Revocable API keys
- Password reset workflow
- Optional TOTP MFA
- OIDC SSO flow
- SCIM-style user provisioning endpoints
- Encrypted application secrets (AES-256-GCM)
- Security headers
- Rate limiting
- Audit log
- Retention policy and automated document cleanup
- Readiness endpoint

### Commercial
- Trial workspaces
- Stripe subscription checkout
- Paystack payment initialization
- Plan-aware document/storage limits

### Production architecture
- PostgreSQL
- Durable S3-compatible object storage (AWS S3 / Cloudflare R2 / Backblaze B2 style endpoints)
- Render deployment template
- Docker runtime
- Health and readiness endpoints

## Important production boundary

The software includes enterprise-oriented controls, but software alone does not create a compliance certification. Before putting highly regulated or mission-critical data into production, the operator should configure durable storage, backups, monitoring, SSO/SCIM, key management, incident response, disaster recovery, penetration testing and the controls required by the customer's jurisdiction and contract.

## Deploy

1. Create a **new GitHub repository** for DocFlow. Keep NEXUS in its existing repository.
2. Upload the project files.
3. Create Render PostgreSQL and a Render web service, or use `render.yaml`.
4. Set `JWT_SECRET` and `ENCRYPTION_KEY` to long random secrets.
5. Configure S3/R2/B2 before handling real customer documents. Local storage is only for demos.
6. Configure OCR and AI when required.
7. Configure SMTP, Stripe/Paystack and OIDC/SCIM when ready for those features.
8. Check `/api/readiness` after deploy.

## Environment variables

See `.env.example` for the complete list.


## Enterprise positioning

DocFlow 3.0 is a deployable enterprise-oriented foundation for document intelligence and workflow automation. It supports multi-tenant workspaces, role-based access, MFA, OIDC SSO, SCIM provisioning, encrypted integration secrets, durable object storage adapters, validation, approvals, audit history, API keys, signed webhooks, retries, usage controls and subscription billing.

Do not represent DocFlow as SOC 2, ISO 27001, HIPAA, GDPR certified, or penetration-tested solely because these application features exist. Those are organization- and deployment-specific obligations that require evidence, policies, infrastructure controls and independent assessment where applicable.

### First commercial workflow

The recommended first deployment is invoice/accounts-payable automation:

`invoice → OCR/PDF extraction → validation → human approval → accounting/ERP webhook → audit`

The product can then be extended to receipts, purchase orders, contracts, onboarding forms, claims and other document-heavy operations.
