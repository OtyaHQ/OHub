# Otya ecosystem engineering standard

**Status:** Working engineering standard  
**Audience:** Otya product teams, maintainers, contractors and approved partners

This document defines the shared engineering expectations for Otya products. It describes intended architecture and release discipline; it does not certify that any feature, provider integration or production deployment is active.

## Product portfolio and ownership

| Product | Responsibility | Data boundary |
| --- | --- | --- |
| **Otya ecosystem** | Shared product experience and platform conventions | Does not become a universal store for every product's private records |
| **Otya End** | Shared identity, service contracts, integrations, notifications and platform operations | Owns only shared platform data and operational records |
| **OPoint** | Retail, inventory, staff, cash control and future agency operations | Business records and financial ledgers belong to OPoint |
| **Omy Play** | Independent media and entertainment product | Core playback and private media stay device-local; optional connected features are explicitly scoped |
| **O** | Private owner-facing intelligence and approved company operations | Owner context and privileged tools remain private |
| **OHub** | Public developer and partner information | Public documentation only; no secrets, private endpoints or customer records |

A shared Otya account does not grant automatic access to every product. Each product must enforce its own server-side authorization, tenant/business scope and permissions.

## Approved technology direction

- **Source and review:** GitHub organization repositories, pull requests and protected release branches.
- **Runtime, storage and security:** Cloudflare Workers, D1, R2, KV, Queues, Durable Objects, Workflows, Access and observability where each capability is justified.
- **Transactional email:** Resend through server-side adapters.
- **Android notifications and Google platform functions:** Firebase may be used only for the clearly scoped Android/Google capability that requires it. Firebase must not become a second business backend or shared identity authority.
- **Other infrastructure providers:** Do not add Supabase, Appwrite, Vercel or an additional backend/database provider without a documented need and owner approval.

Prefer a small set of reusable services over duplicate Workers, databases or vendors. Do not add infrastructure solely to match a product name.

## Identity and authentication

- Otya End is the shared identity authority.
- Supported sign-in methods are approved email/password or other explicitly approved first-party methods.
- One-time codes may be delivered by email and, where configured, an Otya-operated Telegram bot.
- **Telegram Login, Telegram OAuth/OIDC, Telegram account login widgets and Telegram Mini App authentication are not approved sign-in methods.**
- Telegram is a message/OTP transport only where a user has explicitly enrolled and the destination has been verified. A Telegram chat ID or bot interaction must not be treated as proof of account ownership by itself.
- OTPs must be short-lived, purpose-bound, rate-limited, single-use, protected at rest and invalidated after success or expiry.
- Product roles, staff membership and owner privileges are verified server-side. Never trust client-supplied role flags.

## Data and security boundaries

- No product may write directly into another product's database.
- Cross-product access must use an authenticated, narrowly scoped service contract.
- Financial operations must be idempotent, atomic where possible, auditable and reconcilable.
- Unknown provider outcomes remain unknown until verified from trusted provider evidence.
- Do not store provider secrets, signing keys, service-account files, access tokens or recovery material in source control, APKs, browser code or public CI output.
- Keep logs useful but privacy-preserving. Never log OTPs, passwords, authorization headers, private media names, full payment credentials or message bodies unnecessarily.
- Apply least privilege to GitHub, Cloudflare, CI and service bindings.

## Environments and releases

- Keep local, staging and production environments separate.
- Staging must use its own databases, buckets, queues, service bindings and provider credentials. It must never perform real money movement or send customer-facing production notices.
- Production deployment requires successful automated validation, an explicit release decision and a recoverable migration plan.
- Database migrations must be reviewed, sequential, tested against a disposable copy and backed by a verified recovery point before production application.
- Deploying code does not restore or migrate data. Rolling back code does not roll back D1, R2 or external provider state.
- Never activate a live payment rail until the provider contract, credentials, callbacks, reconciliation and regulatory/operational requirements are confirmed.

## Repository and review discipline

- Use a small, predictable branch set: `main` plus short-lived `feat/*`, `fix/*`, `security/*` and `rebuild/*` branches.
- Make focused pull requests with a clear problem statement, risk, tests and rollback note.
- Require automated checks for linting, type checking, tests, dependency/security scanning and deployment configuration.
- Pin high-impact GitHub Actions to reviewed immutable versions or commit SHAs.
- Keep public OHub documentation separate from private source, operational runbooks and infrastructure inventories.
- Treat repository visibility as a security control: application/backend source and internal operational material should be private; OHub is the intended public developer surface.

## Reliability and acceptance

A green CI run is evidence for the checks it executed, not proof of production readiness. For each product, record separately:

1. Source and static validation.
2. Automated tests.
3. Staging integration evidence.
4. Production deployment evidence.
5. Real-device or real-provider acceptance where relevant.
6. Monitoring, rollback and recovery evidence.

Every user-facing feature must have useful loading, empty, success, pending, failure and recovery states. Preserve local/offline capabilities where they are part of the product promise.

## Change control

Before changing live DNS, repository visibility, production secrets, OAuth clients, signing identities, payment-provider settings, D1 schemas or existing public URLs, identify dependencies and record the intended rollback. Keep old identifiers as compatibility aliases until dependent clients and integrations have been migrated and verified.

