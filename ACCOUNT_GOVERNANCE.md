# Otya ecosystem account governance

**Status:** operating standard and migration record, 11 November 2026.

## One ecosystem, controlled accounts

Otya is the public umbrella brand. Otya OS is the unified platform; Otya End is the shared backend; OtyaPoint, Otya Media, OtyaHub and Next are distinct products/services with stable internal identities.

Otya Holdings Limited is the intended parent-company identity. Its incorporation and each provider/account transfer must be completed before describing it as the legal owner, merchant, or data controller for services still held in an individual's name. An account display label is not evidence of legal incorporation or ownership.

Domains, repository names, Worker names, email addresses, package IDs and database IDs are technical addresses or identifiers, not the legal entity, product identity, customer, tenant or authorization subject.

## GitHub

The five repositories are currently under the personal GitHub user `peterkatabira`. There is no Otya GitHub Organization yet.

Target steps:
1. Create an Otya GitHub Organization under the appropriate legal/business identity.
2. Transfer OtyaEnd, OtyaMedia, Leo, OtyaPoint and OtyaHub without changing repository slugs initially.
3. Add least-privilege teams for owners, platform maintainers, product maintainers, security reviewers and public documentation maintainers.
4. Protect `main` with pull requests, required CI, CODEOWNERS, restricted force-push/deletion and protected production environments.
5. Audit collaborators, GitHub Apps, Actions secrets, environments, deploy keys, webhooks, packages and repository visibility after transfer.
6. Keep OtyaHub public. Decide the other repositories' visibility based on actual source/data exposure and operational need.

Repository transfer requires GitHub account-owner/admin interaction. The currently connected GitHub tool can edit repositories but cannot create an Organization or transfer them. Do not delete the current owner or rename repository slugs until transfer and recovery have been verified.

## Cloudflare

Cloudflare already displays the account as **Otya Holdings Limited**. Use one governed Otya account for the shared zones and services, with named human users, least-privilege roles and separate scoped API tokens for CI/CD.

Use Worker Service Bindings for internal Otya calls. Public domains are client entry points only. Keep production, staging and local resources separate. Store runtime credentials in Cloudflare Secrets Store/Worker secrets, never in GitHub source, application packages or public configuration.

The account display name is not proof of incorporation or legal ownership. Reconcile legal name, billing, recovery contacts and provider contracts after the relevant company registration and provider approval.

## Resend and business email

Use one shared Otya Resend account for ecosystem transactional mail. Product services should use the shared notification/mail service rather than separate vendor accounts or browser-visible API keys.

- Sending domain: `otya.site`, verified.
- Inbound role mail: Cloudflare Email Routing.
- Operational Resend webhook: `https://otya.site/webhooks/`, enabled.
- Keep DKIM, SPF, DMARC, custom return-path, bounce/complaint handling and webhook-signature verification under the Otya platform owner.
- Store Resend credentials server-side only. Separate production and staging credentials where supported; rotate only after every consumer and rollback path is verified.

## Domain registrar and DNS

Namecheap remains the registrar; Cloudflare is authoritative DNS/edge for the active `otya.site` zone.

Every hostname maps to a configurable logical surface: primary, API, docs, status, Space, assets or downloads. Never use a hostname as a user, tenant, transaction, database, service or authorization ID. DNSSEC must be enabled only after the matching DS record is configured at the registrar.

Legacy `petersmartlink.com` public-browser hosts are temporary redirects to their Otya equivalents. Old API/auth/update/webhook paths remain temporarily available for older installed builds and callback compatibility. Remove the old zone and its Worker/R2 custom domains only after measured traffic, app upgrades, OAuth/callback delivery, update distribution and rollback tests prove that they are no longer needed.

## Secrets and production controls

- No API keys, bot tokens, signing keys, passwords, database credentials or owner tokens in source, issues, public documentation or mobile builds.
- Use scoped Cloudflare Secrets Store bindings for runtime credentials.
- GitHub Actions deployment credentials must be scoped and protected by required reviewers.
- Keep payment-provider writes disabled until legal merchant onboarding, callback authenticity, idempotency, reversal/refund, settlement and reconciliation controls are verified.
- Back up before destructive operations and prove a restore path.
- Record each resource's purpose, environment, owner, dependencies and recovery procedure.

## Current migration status

- `otya.site` is active in Cloudflare. Main site, API, docs, status and Space hostnames are attached to `otya-core`; `assets.otya.site` is attached to the Otya R2 assets bucket.
- Cloudflare-managed SSL is active. Minimum TLS is 1.2, Always Use HTTPS is enabled, and HSTS is set to a short one-day period pending full browser validation.
- DMARC is monitoring-only (`p=none`) while aggregate reports are reviewed.
- Resend reports `otya.site` verified for sending. Inbound forwarding is handled by Cloudflare Email Routing.
- Five coordinated domain-portability PRs remain drafts and have not been merged or deployed. Their CI is still being checked.
- Old browser hosts are configured to redirect on GET/HEAD. Old API/auth/latest/check-update/APK/webhook paths are kept as temporary compatibility endpoints.
- Some production Worker plain-text variables still require a reviewed full Wrangler deployment. Do not patch a partial Worker bindings array: it can remove existing secrets, services, D1, R2, KV or queues.
- GitHub Organization creation and repository transfer remain outstanding.
- A signed runtime endpoint manifest and health-checked multi-origin failover are specified as the next portability milestone; current mobile defaults can be overridden through centralized build/release configuration, but signed runtime endpoint discovery is not yet implemented.
