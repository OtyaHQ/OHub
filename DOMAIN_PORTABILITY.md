# Domain portability and service addressing

## Purpose

Otya must be able to change, add, or retire public domains without changing its product identity, database identity, authorization model, internal service topology, or installed application identity.

A domain is an address for a service. It is not the service, product, tenant, user, company, database, or security principal.

## Stable identities

Use stable logical identifiers in code, data, logs, events and authorization rules:

| Scope | Stable identity |
|---|---|
| Ecosystem | `otya` |
| Unified platform | `otya-os` |
| Shared backend | `otya-end` |
| Business operations | `otyapoint` |
| Media product | `otya-media` |
| Developer community | `otyahub` |
| Owner intelligence | `next` |
| Authentication service | `otya-auth` |

Use internal IDs or explicit product/tenant IDs for ownership and access checks. Never use a domain, email address, URL path, display name, or provider subject as a database primary key.

## Addressing model

1. **Public entry points:** custom domains and subdomains map to a logical surface such as app, docs, status, space, assets or downloads.
2. **Routing:** the Cloudflare edge maps a hostname to a surface. Host-to-surface mappings are configuration, not hardcoded product identity.
3. **Internal calls:** Workers communicate through Cloudflare Service Bindings and typed service contracts. Do not call another Otya Worker through its public URL when a service binding exists.
4. **Storage:** use D1 database IDs, R2 bucket bindings, KV namespace bindings and object keys. Do not store a public hostname as the locator for internal data.
5. **Authentication:** the auth service issues tokens for stable audiences/scopes such as `otya-end` and `otyapoint`, not for a particular web hostname. Browser cookies are host-only. Cross-product sign-in uses a short-lived, one-time authorization-code handoff; never rely on a parent-domain cookie.
6. **CORS:** same-origin browser APIs need no CORS header. Cross-origin access must be explicit and checked against a product-specific allowlist; never use a universal wildcard for credentialed endpoints.
7. **Email:** sender identity and delivery provider are independent settings. Change mail sender/domain and provider verification without changing application identity or database records.
8. **Mobile and desktop clients:** a compiled bootstrap address is only the first contact point. The target client configuration service returns a signed, versioned endpoint manifest with multiple approved origins, expiry, minimum app version and rollback data. Clients cache the last-known-good manifest and use bounded health-checked failover. Do not silently accept arbitrary URLs from unsigned remote configuration.

## Current public address map

These are current deployment addresses, not permanent identities:

| Surface | Current address |
|---|---|
| Public product site | `https://otya.site` |
| Documentation and help | `https://docs.otya.site` |
| Service status | `https://status.otya.site` |
| Account and product space | `https://space.otya.site` |
| Email sending domain | `otya.site` |

Other branded domains may be attached later and mapped to the same logical surface. A surface may have several approved hostnames. The canonical URL used for search/social metadata is a configurable preference; it is not an API dependency.

## Configuration contract

Use the following names consistently across deployment configuration:

- `OTYA_PRIMARY_HOSTS`
- `OTYA_DOCS_HOSTS`
- `OTYA_STATUS_HOSTS`
- `OTYA_SPACE_HOSTS`
- `OTYA_ASSETS_HOSTS`
- `OTYA_PUBLIC_URL`
- `OTYA_SUPPORT_EMAIL`
- `OTYA_NO_REPLY_EMAIL`
- `OTYA_API_ORIGINS`
- `OTYA_ENDPOINT_MANIFEST_VERSION`

Host lists accept multiple comma-separated approved hostnames. Do not put secrets in these values. Keep signing keys, provider tokens, API keys and credentials in Cloudflare Secrets Store.

## Change-domain procedure

A domain change is an infrastructure/configuration release, not an application rewrite:

1. Add the new zone and verify registrar delegation, DNSSEC state, SSL and DNS records.
2. Attach the hostname to the intended Cloudflare Worker/R2 service and verify origin routing.
3. Add the hostname to the appropriate approved host list and canonical public URL setting.
4. Update OAuth/identity callback allowlists, Turnstile hostnames, webhook callback URLs, Firebase/App Check domains and any third-party origin registrations.
5. Verify email sender-domain DNS and deliverability separately.
6. Verify host-only sign-in, one-time code flows, asset/download delivery, deep links, API routing, robots/sitemap/canonical metadata and monitoring from each approved hostname.
7. Keep old domains as explicitly temporary aliases only when needed for safe transition. Measure traffic and callback use before retiring them.
8. Remove old DNS, Worker custom domains, provider allowlists and secrets/configuration only after evidence shows no remaining production dependency.

## Non-goals and safeguards

- Do not make every domain an independent backend or duplicate database.
- Do not use a public domain as the key for an account, business, file, transaction, or service.
- Do not use wildcard DNS/CORS as a shortcut.
- Do not delete a legacy domain before critical email, OAuth, payment-provider callbacks, downloads and customer links have been migrated.
- A hostname change does not authorize changing product names, package IDs, signing keys, database IDs, D1/R2 resources or payment-provider credentials.

## Implementation status

The domain-aware Worker routing, host-only web session cookies, configurable public metadata/mail identities and refreshed client defaults are being prepared on the `domain-portability-foundation` branches. Signed remote endpoint manifests, multiple-origin mobile failover, full authentication callback migration, and final legacy-domain retirement remain separate implementation and verification work. No production deployment is implied by these branch changes.
