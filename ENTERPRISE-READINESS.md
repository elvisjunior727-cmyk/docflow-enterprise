# Enterprise readiness matrix

DocFlow 3.0 is designed as an enterprise-oriented application foundation. This file separates what the application implements from what must be provided by the operator or a customer environment.

| Area | Application support | Production action |
|---|---|---|
| Tenant isolation | Implemented | Test with tenant-isolation review |
| RBAC | Implemented | Map roles to customer policy |
| Audit | Implemented | Define retention/export policy |
| Approval gates | Implemented | Define business approval rules |
| API keys | Implemented with scopes/revocation | Rotate and monitor keys |
| MFA | Optional TOTP | Enforce for privileged users |
| OIDC SSO | Implemented flow | Configure customer IdP and test claims |
| SCIM | Provisioning endpoints | Configure customer IdP and lifecycle rules |
| Secret encryption | AES-256-GCM application encryption | Protect ENCRYPTION_KEY in managed secret storage |
| Document storage | S3-compatible adapter | Use durable storage with encryption and lifecycle policies |
| Queue/retries | PostgreSQL-backed jobs | Monitor queue depth/failures |
| Webhooks | Signed delivery records + retries | Verify receiver signatures and monitor failures |
| Backups | External | Configure managed DB backups and test restores |
| Monitoring | Health/readiness endpoints | Add centralized logs, alerts and metrics |
| Disaster recovery | External | Define RPO/RTO and run recovery tests |
| Penetration testing | External | Independent assessment before sensitive workloads |
| Formal certifications | External | Complete the relevant organizational assessment |
