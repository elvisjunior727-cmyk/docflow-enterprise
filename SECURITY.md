# DocFlow security notes

DocFlow 3.0 includes baseline enterprise application controls: tenant-scoped queries, role checks, bcrypt password hashing, JWT token-version invalidation, scoped API keys, request IDs, security headers, rate limiting, encrypted application secrets, optional TOTP MFA, OIDC SSO, SCIM-style provisioning, audit events, retention cleanup and database-backed job retries.

## Required production hardening

- Use S3-compatible durable object storage rather than local disk.
- Enable encryption at rest at the storage/provider layer and protect database credentials.
- Configure managed PostgreSQL backups and test restore procedures.
- Centralize application logs and create operational alerts for failed jobs and webhook failures.
- Configure SSO/SCIM for customer identity systems when required.
- Run an independent threat model, penetration test and dependency review before handling highly sensitive production data.
- Define incident response, access review, disaster recovery and data retention procedures.
- Do not claim SOC 2, ISO 27001, GDPR certification, HIPAA compliance or other formal status merely because the code contains security controls; certifications and contractual compliance depend on the entire operating environment and assessment scope.
- Never store payment card details directly. Use hosted Stripe/Paystack payment flows.


## 3.0 application safeguards

DocFlow 3.0 adds content-signature checks for uploads, separate authentication/upload rate limits, scoped API keys, validation status, correction version history, approval-aware workflow execution, one-time SSO exchange codes, signed billing webhooks with idempotency records, and protected operations/metrics surfaces.

These controls are application features, not a substitute for infrastructure security, malware scanning, penetration testing, backup/restore validation, identity-provider hardening, or formal compliance assessment.
