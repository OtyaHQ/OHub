# Otya developer and public channels

Otya should use each external platform for one clear purpose.

## GitHub

Use GitHub for source control, issues, pull requests, CI/CD evidence, public release metadata, security reporting and technical history.

- `PeterSmartLink/Omy Play`: application source while public; may become private later.
- `PeterSmartLink/Otya-Server`: server/backend source while public; may become private later.
- `PeterSmartLink/Otya`: stable public Otya hub, public automation, safe API examples and links to official product/help/trust surfaces.

The public Otya hub must never contain private source or production secrets just to obtain public-runner minutes.

## Postman

Use Postman as the API testing and developer-experience layer.

Public workspace/collection:
- public version/release endpoints;
- public API examples that require no secret credentials;
- public documentation and first-request examples when Otya exposes a supported developer API.

Private/internal workspace:
- authentication flows;
- account creation/recovery/deletion tests;
- Next requests;
- provider integrations;
- admin/internal endpoints;
- staging environments and test credentials.

Never publish real access tokens, refresh tokens, service secrets, user data or production admin requests in a public Postman workspace.

## LinkedIn

Use LinkedIn primarily for Otya's professional/company presence and meaningful product/ecosystem announcements.

Good uses:
- release milestones after they are actually released;
- engineering/reliability lessons that do not expose security details;
- company/product announcements;
- partnerships and hiring when real;
- links to permanent Otya website/newsroom posts.

Do not turn LinkedIn into Otya's source of truth. Product status, legal documents, downloads and support must remain on Otya-controlled surfaces.

A LinkedIn Developer application should only be created for a concrete integration need such as approved sign-in, member sharing, or an approved organization/community-management integration. Do not request broad LinkedIn permissions simply because they are available.

## Telegram

Use Telegram for community updates, quick announcements and discussion. Permanent factual information should link back to the official Otya website/help/trust pages.

## Website

The website is Otya's canonical public source of truth for product information, downloads, Help, Privacy, Terms, account-deletion information and service/trust information.

## Rule

Publish once as the factual source; adapt the message for each channel. Do not maintain five conflicting versions of the same fact.
