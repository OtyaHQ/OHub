# Otya OS — Public Ecosystem Service Map

This page describes the intended roles of Otya products for developers, partners and customers. It excludes private infrastructure details, credentials, customer records and administrative endpoints.

## One connected ecosystem

The Otya ecosystem is a connected family of products. **OtyaPoint** is the public product name for the shop and business-operations experience. Each service has a clear responsibility; shared identity or navigation does not mean every product shares all data. Legal ownership and registration details are intentionally not stated on this product map.

| Product/service | Public purpose | Integration principle |
|---|---|---|
| **Otya OS** | Unified experience across the Otya family | Consistent identity, design and service discovery |
| **Otya End** | Shared backend and integration layer | Common documented contracts with product-specific authorization |
| **OtyaPoint** | Business operations for the owner's shop, including retail and agency workflows | Financial operations require partner verification, reconciliation and appropriate controls |
| **Omy Play** | Media and entertainment product for audio/video, private media and device-to-device sharing | Core playback remains useful offline; account/cloud features are optional |
| **Leo / Otya Next** | Private owner-facing AI coordinator | Owner-only tools stay private and require server-side authorization |
| **OtyaHub** | Public developer and partner information | Publish safe docs, integration guidance and public release information |
| **Resend** | Transactional email delivery and event visibility | Email integration is server-side; secrets and private delivery payloads stay protected |
| **Payment partners** | Approved provider rails for agency services | Provider adapters are replaceable; status is confirmed by trusted provider evidence, not UI optimism |

## Mobile-money agency readiness

Mobile-money agency operations are a core OtyaPoint business capability. The intended workflow includes cash-in/cash-out, airtime/data and bill-payment requests, cash and provider-float tracking, commissions, receipts, transaction history and reconciliation.

Provider integrations must remain behind a consistent adapter contract so providers can be added or replaced without rewriting the business application. Interswitch Marketplace Routing and Quickteller Business are separate products with distinct API contracts; neither should be treated as an alias for the other. Airtel Money and MTN Mobile Money are separate provider integrations as well.

A service must not display a transaction as successful until the provider's trusted response/status has been verified. Timeouts can leave a transaction pending or unknown and require reconciliation before retrying. Public documentation does not imply any payment integration is currently live or approved.

## Hybrid AI and automation

Leo may coordinate cross-product health checks, repository changes, incident analysis, documentation, release preparation and approved workflows. Product data remains under the relevant product's authorization boundary. High-impact actions such as production releases, permission changes, destructive operations and money movement require explicit authorization and post-action verification.

## Integration guidance for developers

- Prefer documented versioned APIs and explicit service ownership.
- Use least-privilege service identities and short-lived credentials.
- Validate identities and product roles on the server.
- Use idempotency keys for retryable writes.
- Define timeouts, retries, duplicate handling and observable error states.
- Keep user data and financial records out of public examples and public CI logs.
- Treat a successful build as engineering evidence, not proof of production readiness.
- Preserve existing public links, app IDs and API paths until a reviewed migration is approved.

## Status and accuracy

This is a statement of product roles and intended integration principles, not a live service-health dashboard. Refer to the official status surface for current availability, and do not infer that an integration is live merely because it is listed here.
