# User-side Next

Next is the user-facing assistant inside Otya. It must be separated from the owner/operator assistant that can work with Otya systems.

## Roles

### User-side Next

May help a user with:

- general questions and conversation within the capability of the configured model;
- Otya Help and troubleshooting;
- finding and explaining Otya features;
- controlling approved in-app actions such as playback, search, navigation or settings through explicit app tools;
- using the signed-in user's own permitted context when needed;
- explaining errors and guiding recovery.

It must not receive Otya owner/admin credentials or tools such as production GitHub, Cloudflare, Resend, Firebase administration, release publishing or other operator-only capabilities.

### Owner/operator assistant

May inspect and operate Otya systems under the separate approval model in `AI_OPERATING_MODEL.md`.

The two roles may share verified public Otya product knowledge, but they do not share authority.

## Next does not need model training on all Otya information

Do not try to place the entire product, documentation, user history and operational system into every model prompt.

Use four layers instead:

1. **Small system policy** — identity, behavior, safety, privacy and tool rules.
2. **Retrieved Otya knowledge** — fetch only relevant Help/product/policy passages for the current question.
3. **Live tools** — ask the app/backend for current state instead of teaching the model stale state as text.
4. **Optional user context** — small, permissioned user preferences/history where the product actually supports it.

This is easier to update and cheaper than retraining a model whenever Otya changes.

## Knowledge source of truth

User-side Next should retrieve from canonical, versioned sources such as:

- Otya Help;
- current product documentation;
- current Privacy and Terms where relevant;
- current release/known-issue information;
- approved FAQ and support content.

Archived engineering handoffs, secrets, internal infrastructure documents and obsolete product generations must not be exposed as user knowledge.

## Free-tier strategy

While Otya is on limited/free AI infrastructure:

- keep the system prompt small;
- retrieve only a few relevant knowledge chunks per request;
- cap user input and output lengths reasonably;
- stream responses instead of holding the UI on a long spinner;
- summarize old conversation context rather than resending entire chats forever;
- use a fast lower-cost model for normal requests and reserve stronger models/providers for cases that genuinely need them when available;
- cache safe, non-personal product/help answers where useful;
- apply per-user and guest rate limits during beta;
- prevent recursive/agent loops that consume quota without user value;
- monitor inference and database usage;
- fail gracefully when quota/provider capacity is unavailable.

Otya's local media experience must continue working if Next is unavailable.

## Graceful quota failure

When online AI capacity is exhausted or unavailable:

- do not leave the user on an indefinite `Thinking…` state;
- preserve the conversation draft/history that is safe to keep;
- explain briefly that Next is temporarily unavailable;
- keep Help pages, local playback, Library, Private, Transfer and other non-AI functionality available;
- allow retry after capacity returns;
- do not silently downgrade security or send requests to an unapproved provider.

## User memory

Memory should be selective and optional, not a transcript dump.

Good candidates, when the user has enabled them, include:

- preferred language;
- preferred playback behavior;
- explicitly saved preferences;
- short conversation summaries needed for continuity.

Do not use raw Private media, passwords, OTPs, credentials, sensitive account-recovery material or unrelated device data as AI memory.

Users should be able to understand and control any persistent AI history/memory that Otya stores.

## Tool permissions

Every user-side tool must be narrow and permissioned.

Examples:

- `search_local_media(query)` — read the user's indexed local media metadata only as needed;
- `play_media(item_id)` — play a selected item;
- `pause_playback()` — pause playback;
- `open_otya_screen(route)` — navigate to an approved screen;
- `get_app_version()` — read app version/build;
- `get_help(topic)` — retrieve canonical Help content.

Avoid a generic unrestricted `execute` tool.

Actions that delete data, change account/security state, send/share files or affect another person require normal Otya confirmations and permissions even when requested through Next.

## Model quality

The Next experience can be designed to feel conversational like leading assistants, but model intelligence depends on the inference model/provider actually configured. A free Cloudflare model should not be marketed as equivalent to a specific frontier commercial model.

The product promise should focus on what Otya controls: useful context, fast streaming, accurate Otya knowledge, safe tools, clear failure handling and consistent user experience.

## Distribution before Google Play

Otya can run a controlled beta without Google Play using a verified signed APK distributed through approved Otya channels. Google Play-specific production protections and store workflows should be tracked separately rather than faked.

Do not weaken production security claims merely to make a sideload beta appear Play-distributed.
