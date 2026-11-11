# Product-side AI assistants

Product AI is optional and must remain separate from the private owner assistant in the **O** application.

## Product-specific workspaces

### OPoint Copilot

When explicitly enabled, OPoint Copilot may explain product features, summarize the signed-in user's own company/branch-scoped read models, help understand inventory and reconciliation status, and prepare reports.

It must not initiate deposits, withdrawals, bill payments, airtime purchases, refunds, ledger postings, staff permission changes or any other financial write. A model response never changes the authoritative transaction state. Financial actions remain in OPoint's ordinary authenticated and approval-controlled workflows.

### Omy Play Guide

When explicitly enabled, Omy Play Guide may explain playback and app features, help locate user-selected media using on-device metadata, and control narrow playback/navigation tools after user intent.

It must not upload local media libraries, Private/Vault contents, file bytes, device paths, playback history or sensitive metadata to a remote model. Local playback and local media management must continue when AI, OEnd or the network is unavailable.

### O

O is the separate private owner-AI application. It may assist the owner with company engineering and operations through approved OEnd/product APIs. It does not inherit consumer product permissions and must not access a customer's private Omy Play data.

## Four-layer context model

Use four layers instead of putting the entire product and user history into every model prompt:

1. **Small system policy** — identity, behavior, privacy, safety and tool rules.
2. **Retrieved product knowledge** — fetch only relevant public Help/product/policy passages for the current request.
3. **Live product tools** — ask the owning app/backend for current, permissioned state rather than teaching the model stale state as text.
4. **Optional user context** — small, permissioned preferences/history only where the product supports it and the user expects it.

The model is never the source of truth for identity, permissions, balances, playback state or release state.

## Knowledge source of truth

Product assistants retrieve only from versioned, approved sources such as:

- OHub public product/developer documentation;
- current OPoint and Omy Play Help content;
- current Privacy and Terms where relevant;
- verified release and known-issue information;
- approved FAQs and support articles.

Archived engineering handoffs, secrets, internal infrastructure documents, owner-only notes and obsolete product generations must not be exposed as user knowledge.

## Free-tier and cost strategy

- Keep system policy small and retrieve only a few relevant knowledge chunks per request.
- Cap user input and output lengths; stream responses.
- Summarize useful conversation context rather than resending entire chats.
- Use the lowest-cost model that passes product-specific quality and safety evaluations.
- Reserve stronger models/providers for cases that genuinely need them.
- Cache safe, non-personal Help answers where useful.
- Apply per-user and guest rate limits and per-product budgets.
- Prevent recursive agent loops and unbounded tool calls.
- Monitor inference, retrieval, database, queue and R2 usage.
- Fail gracefully when provider capacity is unavailable; never silently weaken security.

## Graceful quota failure

When online AI capacity is exhausted or unavailable:

- do not leave the user on an indefinite `Thinking…` state;
- preserve only the conversation draft/history the product is allowed to retain;
- explain briefly that the assistant is temporarily unavailable;
- keep Help pages, local playback, inventory and normal product functions available;
- allow retry after capacity returns;
- do not silently switch to an unapproved provider.

## User memory and privacy

Memory is selective and optional, not a transcript dump.

Potential user-selected preferences include language, playback behavior or explicitly saved app settings. Do not store passwords, OTPs, credentials, recovery material, raw Private media or unrelated device data as AI memory.

Omy Play's local media and Private/Vault areas must remain on-device. OPoint Copilot context is tenant/branch-scoped and may never cross company boundaries. Owner memory for O must remain separate from both.

## Narrow tool permissions

Every product tool must be typed, scoped and permissioned.

Omy Play examples:

- `search_selected_local_media(query)` — read selected local metadata only when the user asks;
- `play_media(item_id)` — play a selected item;
- `pause_playback()` — pause playback;
- `open_omy_play_screen(route)` — navigate to an approved screen;
- `get_app_version()` — read the installed app version;
- `get_help(topic)` — retrieve canonical Help content.

OPoint examples:

- `get_inventory_summary(company_id, branch_id)` — read an authorized summary;
- `get_reconciliation_status(company_id, branch_id, session_id)` — read reconciliation state;
- `draft_sales_report(company_id, branch_id, period)` — prepare a report without posting financial entries.

Avoid a generic unrestricted `execute` tool. Actions that delete data, change account/security state, send/share files or affect another person require the product's normal confirmation and authorization rules.

## Model quality and product claims

Assistant quality depends on the inference model/provider actually configured. Do not market a free model as equivalent to a named frontier commercial model.

The product promise should focus on what Otya controls: useful context, fast streaming, accurate product knowledge, safe tools, privacy boundaries and consistent failure handling.

## Rollout

Enable assistants only after their product-specific threat model, data map, prompt/tool registry, evaluation set, rate limits, cost budget and rollback behavior are reviewed. Keep each assistant disabled by default until those gates pass.
