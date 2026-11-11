# OtyaHub

**OtyaHub** is the public developer and partner entry point for **Otya OS**. It publishes public documentation, safe examples, product guidance, and integration information—not private operations or administrative controls. This public hub describes product roles and does not assert the legal registration or trading-name status of any parent entity.

## Public surfaces

- Product: https://otya.site
- Help and documentation: https://docs.otya.site
- Service status: https://status.otya.site
- Account and product space: https://space.otya.site
- Privacy: https://otya.site/privacy
- Terms: https://otya.site/terms
- Download: https://otya.site/download/otya-player
- News: [Otya News](news/)

## Domain portability

Otya product identity is independent of public domain names. The current public addresses are configurable entry points; product IDs, account IDs, service bindings, data schemas and authorization scopes must not use a hostname as their identity. See [Domain portability and service addressing](DOMAIN_PORTABILITY.md) before adding a URL to code or documentation.

## Latest update

- [Otya 1.0 confirms its local-first Music scope — 2 September 2026](news/2026-09-02-local-first-music-scope.md)

## Operating documents

- [Beta scope and acceptance](BETA.md)
- [AI operating model](AI_OPERATING_MODEL.md)
- [User-side Next](USER_SIDE_NEXT.md)
- [AI provider strategy](AI_PROVIDER_STRATEGY.md)
- [Public automation policy](PUBLIC_AUTOMATION.md)
- [Developer and communication channels](DEVELOPER_CHANNELS.md)
- [Public Postman collection](postman/Otya-public.postman_collection.json)
- [Otya platform service blueprint (proposal; pricing not finalized)](platform/SERVICE_BLUEPRINT_AND_PRICING_V1.md)
- [Public ecosystem service map](ECOSYSTEM_SERVICE_MAP.md)
- [Security and vulnerability reporting](SECURITY.md)

## What belongs here

This repository may contain:

- public product and developer-facing documentation;
- public release and service-health checks;
- safe API examples that contain no credentials or private user data;
- links to official Otya support, security and community surfaces;
- public GitHub Actions that operate only on information safe to expose.

## What does not belong here

Do not commit or print:

- production credentials, API keys, signing material, tokens or service-account files;
- private source code copied here only to obtain public-runner minutes;
- internal infrastructure inventories, private endpoints or administrative procedures;
- user data, crash payloads, private logs or account-recovery material.

If Otya's application or server repositories become private later, this repository can remain public as the stable product/developer hub. Public workflows must continue to operate only on public inputs unless a separately reviewed security design explicitly permits otherwise.

## Product naming and ecosystem boundaries

- **Otya OS** — unified platform and shared ecosystem experience.
- **Otya End** — canonical name of the shared backend and integration layer. The existing `Otya-Server` GitHub repository slug is a compatibility identifier, not the product name.
- **OtyaPoint** — the owner's shop/business operations application; its private retail, staff, inventory, and financial data must not be published in this public hub.
- **Otya Media** — the local-first media player (existing repository slug: `OtyaPlayer`). Core playback remains available without the backend.
- **OtyaHub** — this public developer and partner information surface.
- **Next** — private owner intelligence application; do not expose owner-only operations or internal infrastructure through public content.

Keep existing repository slugs, API paths, Worker names, app IDs, and public links unchanged until a separately reviewed compatibility migration is approved. Legacy all-caps `OTYA` identifiers may remain in compatibility-sensitive code or historical records, but public product copy should use the canonical names above.

## Release status

Otya v1 is still under acceptance. A successful CI build is not the same as a released or physically device-tested build.

## Security

Please use the [Otya Security Policy](SECURITY.md) to report vulnerabilities privately. Do not publish secrets, tokens, exploit details or user data in a public issue.
