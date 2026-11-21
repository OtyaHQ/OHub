# Otya Ecosystem — Official Brand Asset Standard

**Authority:** Owner-supplied `Otya_Complete_Ecosystem_Logos_v2.zip`  
**Status:** Permanent visual source of truth; rollout must be verified per surface  
**Umbrella identity:** Otya  
**Parent-company identity:** Otya Holdings Limited

## Permanent logo set

Only the artwork supplied in the owner's ZIP is authoritative. Preserve each original file exactly; do not redraw, regenerate, recolour, crop, retype, distort, or substitute it.

| Identity | Official file family | Use |
|---|---|---|
| Otya | `01_Main_Logo_Otya/` | Parent/umbrella identity, main ecosystem website, corporate communications, cross-product navigation |
| O (four dots) | `02_AI_Logo_O_4Dots/` | AI app, assistant/chat surfaces, AI badges and AI project's OAuth branding |
| Omy | `03_Media_Player_Logo_Omy/` | Media player app, playback UI, splash/installer and media project's OAuth branding |
| Opoint | `04_Retail_MoMo_Logo_Opoint/` | Unified retail and mobile-money product, POS/checkout, agent and merchant portal, receipts and retail project's OAuth branding |

The ZIP's `WHERE_TO_USE_GUIDE.txt` is part of this standard and controls placement. Do not invent a separate logo for products or services that are not represented in the ZIP. OEnd and OID are service/technical identities, not additional logo families in this package.

## Use the supplied format for the job

- `*_Transparent.png` / `*.webp`: website and interface artwork.
- `*_App_Icon_1024x1024.png`: app launcher/store/OAuth app icon.
- `*_White_BG.png` / `*.jpg`: documents and platforms that require an opaque light background.
- `*_All_White_Transparent.png`: dark-background applications and watermarks.
- `*_All_Black_Transparent.png`: monochrome/stamp use.
- `*_Print_300DPI.pdf`: print production.
- `*.svg`: scalable web/design artwork.
- `Otya_Favicon.ico`: parent-brand favicon.

Keep original filenames and folder names in the source asset archive. Do not use the full wordmark as an app icon when the package provides a dedicated app-icon file.

## Google Cloud OAuth branding

The owner's guide specifies one Otya Google Cloud Organization with three separate projects:
- `otya-ai` uses the O (four dots) identity.
- `omy-media` uses the Omy identity.
- `opoint-retail-momo` uses the Opoint identity.

Apply the matching app icon/logo to each project's OAuth consent screen. Do not use the Otya parent logo as a substitute for a product logo.

## Asset hosting and rollout

The existing Cloudflare public asset host is `assets.otya.site`; the prior `brand/otya/v4/` artwork belongs to an older brand set and must not be treated as this ZIP's logo source. The new package's canonical source tree is to be staged separately under `brand/otya/official/v2/`, retaining its four source folders and filenames.

**Do not switch production references until the exact original files have been uploaded and verified byte-for-byte.** Verify file size and SHA-256 against the supplied ZIP, then verify public HTTP delivery. Preserve the old v4 objects as rollback material until every consuming surface has been migrated and checked.

## Rollout checklist

- [ ] Copy all original logo variants, favicon and print files into the canonical asset store.
- [ ] Verify SHA-256 and size for every uploaded file.
- [ ] Update Otya umbrella website header/footer/favicon and social metadata.
- [ ] Apply O mark to AI web/app/login/OAuth surfaces.
- [ ] Apply Omy mark to media web/app/launcher/splash/OAuth surfaces.
- [ ] Apply Opoint mark to retail/mobile-money web/app/POS/agent/receipt/OAuth surfaces.
- [ ] Update email templates, developer docs, plugin branding and app-store assets.
- [ ] Verify production build, browser pages, mobile launchers, OAuth screens and email rendering.
- [ ] Retire old artwork references only after all checks pass.

Never claim the rollout is complete based on asset upload alone. Record each surface as verified only after viewing the deployed result.


## Live rollout status — 2026-11-21

- The original owner-supplied ZIP was checksum-verified locally; its complete 41-file brand package is now preserved in the private Otya operations plugin, version **0.1.5**, under `assets/official-brand/v2/`.
- The operating instructions now distinguish the four official identities and their exact destinations.
- This repository, OEnd, Opoint, Omy Play and O have updated source-of-truth brand documentation.
- The Cloudflare bucket still contains the previous `brand/otya/v4/` objects. The new `brand/otya/official/v2/` object set has **not** been uploaded or publicly hash-verified.
- Existing website, email and application references have not been switched to the new URL family. This is intentional: references must not point to missing assets.
- Google OAuth project branding, live website rendering, launcher icons and app splash screens remain unverified.

Do not report the visual rollout as complete until the full official package has been uploaded to R2, each object's SHA-256 and public response have been verified, and each deployed product surface has been inspected.
