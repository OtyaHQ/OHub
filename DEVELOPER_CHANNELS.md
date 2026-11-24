# Otya company and developer presence

**Umbrella brand:** Otya  
**GitHub developer organisation:** OtyaHQ  
**Intended parent-company identity:** Otya Holdings Limited  
**Tagline:** One ecosystem. Endless possibilities.  
**Brand line:** Innovate | Connect | Grow.

Otya is the public umbrella identity for the connected ecosystem. OtyaHQ is its official GitHub development and engineering home. Otya Holdings Limited is the intended parent-company identity; do not describe it as incorporated, registered, or legally verified until that status has been confirmed.

## GitHub organisation profile

Keep the organisation login `OtyaHQ` stable. Use the Otya umbrella identity—not a product logo—for the organisation's display name and profile artwork.

Recommended public profile values:

- **Display name:** Otya
- **Description:** Official development organisation for Otya — one connected ecosystem spanning business, media and AI.
- **Website:** https://otya.site
- **Public email:** Leave unset until an approved company-domain contact address is confirmed for public use.
- **Location:** Publish only the company-approved location; do not expose a personal or shop address.
- **Profile image:** Use the exact Otya master logo from the owner's official brand package. Do not substitute the O, Omy or Opoint product marks.

The public `.github` repository now hosts the approved organisation introduction at `profile/README.md`. Keep that repository focused on public profile and community-health assets; pin existing public repositories rather than creating duplicates.

## Repository map

Use the existing repositories as the source of truth. Do not create duplicates merely to change slug casing or product presentation.

| Repository | Responsibility |
|---|---|
| [OHub (OWeb repository)](https://github.com/OtyaHQ/OWeb) | Public developer and partner documentation; safe public examples and ecosystem guidance |
| [OEnd](https://github.com/OtyaHQ/OEnd) | Shared backend and integration source; currently public during active development |
| [\.github](https://github.com/OtyaHQ/.github) | Public organisation profile and community-health assets |

The repository slugs are technical identifiers. Public product naming remains **Otya**, **Opoint**, **Omy Play**, **O**, **OEnd**, **OID**, **OHub** and **Otya OS**. Do not rename a repository or deployed service solely for visual consistency.

Private product and owner-source repositories are restricted to authorized collaborators and are not public developer integration targets. Do not publish private source links in this public channel guide. Opoint is the internal Otya workforce and business-operations application; it is not a public customer SaaS.

## Platform responsibilities

- **GitHub:** source control, code review, issues, pull requests, CI/CD evidence, release history and security reporting.
- **Cloudflare:** Otya's preferred application runtime, data, storage, networking and edge security platform.
- **Resend:** approved transactional email delivery. Keep provider credentials in managed secrets, never in source files.
- **Website:** https://otya.site is the canonical public source for product information, support, policies and verified release information.

Publish a fact once at its canonical source, then link to it from other channels. Do not maintain conflicting copies of product status, policy or support information.

## Official social channels

The official Otya handle is **@otyahq** on TikTok, YouTube, Instagram and X. Use these owner-supplied channel links consistently in public bios, website footers, release announcements and cross-channel posts. Confirm control of each profile and its canonical URL before publishing or connecting automation.

- TikTok: https://www.tiktok.com/@otyahq
- YouTube: https://www.youtube.com/@otyahq
- Instagram: https://www.instagram.com/otyahq/
- X: https://x.com/otyahq

Social accounts are communication and publishing channels only. They are not OID login providers, account-recovery methods or sources of trusted identity claims. Automated publishing, where supported and approved, must use provider-authorised credentials in managed secrets, least-privilege scopes, per-channel revocation, audit logs and an approval queue. Do not commit tokens or expose them to browser clients.

## Other public channels

- **LinkedIn:** company presence, verified milestones, product announcements, partnerships and genuine hiring.
- **Telegram:** community updates and discussion. Link permanent information back to Otya-controlled sources.
- **Postman:** public collections only for supported APIs and examples that require no private credentials. Keep authentication, administration, provider operations and internal environments private.

Create external developer or social integrations only for a real, approved use case. Do not request broad permissions simply because a platform offers them.

## Security and company controls

- Require two-factor authentication for every human account with organisation access.
- Keep organisation ownership limited to trusted company administrators; grant repository access by least privilege.
- Protect `main` branches against force-pushes and deletion. Keep deployment authorization and production environment approvals explicit.
- Use GitHub Actions permissions with least privilege and store deployment credentials only as managed repository or environment secrets.
- Review repository visibility before publishing source, workflows, artifacts or packages.
- Never commit API keys, tokens, signing material, service-account files, private endpoints, customer records, financial data or recovery codes.
- Do not expose internal infrastructure inventories or owner-only AI controls in OHub.
- Treat a successful CI run as validation evidence, not proof that a production deployment or device release is complete.

## Brand and public-trust rules

The owner's `Otya_Complete_Ecosystem_Logos_v2.zip` and its `WHERE_TO_USE_GUIDE.txt` remain the permanent visual source of truth.

- Use the Otya master artwork for the organisation and parent-brand presence.
- Use the four-dot O mark only for the AI product.
- Use Omy artwork only for Omy Play.
- Use Opoint artwork only for Opoint retail and mobile-money surfaces.
- Do not redraw, recolour, crop, distort or replace supplied artwork.
- Do not display a legal-registration, domain-verification or GitHub-verified claim until it has actually been completed and checked.

## Official links

- Otya: https://otya.site
- OtyaHQ on GitHub: https://github.com/OtyaHQ
- OHub developer hub (OWeb repository): https://github.com/OtyaHQ/OWeb
- Otya organisation profile: https://github.com/OtyaHQ/.github
- OEnd public development repository: https://github.com/OtyaHQ/OEnd

