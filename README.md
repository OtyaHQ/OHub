# OHub

**OHub** is the public developer and partner entry point for the Otya ecosystem. It publishes public documentation, safe examples, product guidance and integration information—not private operations or administrative controls.

## Public surface

- Official ecosystem domain: https://otya.site
- News and public product updates: [Otya News](news/)
- Security: [OHub security policy](SECURITY.md)
- Developer and partner guidance: this repository

Use only routes verified on the official domain. Do not publish guessed documentation, download, status or account URLs.

## Latest update

- [Otya 1.0 confirms its local-first Music scope — 2 September 2026](news/2026-09-02-local-first-music-scope.md)

## Operating documents

- [Beta scope and acceptance](BETA.md)
- [AI operating model](AI_OPERATING_MODEL.md)
- [O user-side experience](USER_SIDE_NEXT.md)
- [AI provider strategy](AI_PROVIDER_STRATEGY.md)
- [Public automation policy](PUBLIC_AUTOMATION.md)
- [Developer and communication channels](DEVELOPER_CHANNELS.md)
- [Public Postman collection](postman/Otya-public.postman_collection.json)
- [Otya ecosystem service blueprint](platform/SERVICE_BLUEPRINT_AND_PRICING_V1.md)
- [Public ecosystem service map](ECOSYSTEM_SERVICE_MAP.md)
- [Otya ecosystem engineering standard](ENGINEERING_STANDARD.md)
- [Security and vulnerability reporting](SECURITY.md)

## Canonical product names

- **Otya** — the umbrella brand for the connected ecosystem.
- **OPoint** — the retail and business-operations application.
- **Omy Play** — the local-first media application.
- **O** — the private owner-AI application.
- **OEnd** — shared backend, identity integration and service infrastructure.
- **Otya ID** — shared account identity, email OTP and optional linked Telegram OTP delivery.
- **Otya Control** — private administration and operations.
- **OHub** — this public developer and partner documentation surface.

Product data and privileges remain isolated. OHub contains only intentionally public contracts, samples and guidance. It must never contain private operational inventories, credentials, signing material, personal data, customer financial data or owner-only AI tools.

## What belongs here

- Public product and developer-facing documentation.
- Public release and service-health checks with verified sources.
- Safe API examples containing no credentials or private user data.
- Links to official Otya support, security and community surfaces.
- Public GitHub Actions that operate only on information safe to expose.

## What does not belong here

Do not commit or print production credentials, API keys, signing material, tokens, service-account files, private source code, internal infrastructure inventories, private endpoints, administrative procedures, user data, crash payloads or account-recovery material.

If application/server repositories become private later, OHub can remain the stable public developer hub. Public workflows must continue to operate only on public inputs unless a separately reviewed security design explicitly permits otherwise.

## Release status

A successful CI build is not the same as a released or physically device-tested build. Public release claims must link to immutable build evidence and verified product status.

## Security

Please use the [OHub Security Policy](SECURITY.md) to report vulnerabilities privately. Do not publish secrets, tokens, exploit details or user data in a public issue.
