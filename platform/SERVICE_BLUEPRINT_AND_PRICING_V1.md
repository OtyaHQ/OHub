# Otya Platform — Service Blueprint and Monetisation v1

Status: proposal for review; not a promise of live integrations, legal advice, or government approval.
Owner: Otya platform team
Review date: 2026-10-30

## 1. Product promise

Otya should help people and organisations turn a goal into a working outcome, even when they do not know which tool, provider, or technical steps are required. The customer starts with what they want to achieve—not with Cloudflare, GitHub, DNS, APIs, or code.

Examples:
- “I want to register my business in Uganda.”
- “I need a domain and professional email.”
- “I want a website, online shop, or booking page.”
- “Help me deploy my existing GitHub project.”
- “I am a developer and need an API, MCP server, integration, or deployment workflow.”
- “I am not technical; explain what to do and help me do it safely.”

Otya is the guided service layer across providers. It should not pretend to own government services or replace Cloudflare, GitHub, domain registrars, banks, or other providers.

## 2. One front door, several routes

Every new task should begin with a plain-language goal and an optional skill-level choice:
- **Guide me** — simple explanations, checklists, translations and official links.
- **Help me do it** — guided steps, form preparation, progress tracking and a review before each external action.
- **Do it with me** — a human-assisted service for setup, migration, troubleshooting or business administration.
- **Developer mode** — APIs, CLI commands, repositories, logs, MCP, deployment and technical details.

Do not force a user to choose the right vendor first. Otya recommends the provider and explains why, the price, the trade-offs, what the user must own, and how to leave or move later.

## 3. First service catalogue

### A. Start and formalise a business in Uganda
1. Ask what the person is starting and whether they are registering a business name, partnership, company, or are unsure.
2. Explain the likely pathway and prepare a checklist of information/documents.
3. Link directly to official URSB / OBRS and URA resources for filing and tax registration; explain trading-licence requirements may depend on the location and business.
4. Help prepare a draft checklist and review documents before the user uploads them to an official portal.
5. Track user-entered milestones, reminders and document status; offer a human-assisted package if requested.

Guardrails:
- Clearly distinguish Otya's service fee from official government charges and third-party charges.
- Show the official fee source and date checked; fees and rules can change.
- Never claim registration, TIN, licence, or approval is complete until the relevant authority confirms it.
- Do not collect national ID, passport, tax, or company documents unless necessary for a specific user-requested service. Explain purpose, retention and access first.
- Do not ask for or store the user's government-portal password, OTP, or recovery code.
- The user reviews and submits official applications and payments unless a verified, authorised integration legally supports the action.

Official starting points:
- URSB services: https://ursb.go.ug/services/
- URSB eRegistry: https://eregistry.ursb.go.ug/services
- URA business formalisation: https://ura.go.ug/en/business-formalisation/
- Government eBiz portal: https://www.ebiz.go.ug/

### B. Domain, website and business email
- Help select a name and explain domain extensions, renewal costs, DNS, privacy and transferability.
- Check availability through an approved registrar integration where available; otherwise direct the user to the registrar's verified search page.
- Prefer registering the domain in the customer's own account and billing details. Otya may be delegated limited DNS access only with clear permission.
- Offer free planning and DNS guidance; charge for assisted setup, website build, migration, email configuration, monitoring or support.
- Before changing DNS, display the proposed records, expected impact, rollback plan and customer approval.

### C. Cloudflare, GitHub, hosting and deployment
- Start with a goal wizard: publish a website, protect a domain, host an API, automate a build, store files, or troubleshoot a deployment.
- Connect accounts using provider-supported OAuth or scoped tokens where supported; explain each permission and request the minimum.
- Never ask a user to paste a root key, broad personal access token, private key, or production secret into chat.
- Use read-only diagnosis first. Before writes, show the exact change and ask for approval.
- Create a branch and pull request for code changes; do not merge or deploy to production without explicit approval.
- Support both guided no-code steps and advanced CLI/API instructions.

### D. Developer and organisation workspace
- Public docs and public repositories remain accessible without an Otya account.
- Optional Otya account for saved projects, usage, support and billing.
- Organisation workspaces with invitations, roles, per-project permissions, audit history and member removal.
- API keys are scoped, revocable and shown once; use separate development and production credentials.
- MCP tools are published by capability and permission: public read-only first, then personal and organisation tools, and carefully gated write actions.
- MCP is an integration interface, not a shortcut around authentication, authorisation, approval or audit.

### E. Everyday help and learning
- Searchable plain-language guides, step-by-step walkthroughs, short videos, templates, readiness checklists, diagnostics and local-language explanations where feasible.
- A support assistant can explain and prepare work; it must say when a human, regulator or provider must complete the final step.
- Allow customers to export their documents, configurations and project data. Do not create lock-in by withholding their work.

## 4. Pricing model: free first, then usage and plans

Use a hybrid model; do not charge a subscription merely to read help articles.

### Free
- Public documentation, basic guides, checklists and templates.
- Basic service/provider comparison and official links.
- Limited project inventory and read-only diagnostics.
- Otya Media's local playback and essential offline functions.
- Clear estimates before any billable operation.

### Pay as you go
- One-off assisted setup, domain/DNS changes, deployment help, migration, troubleshooting or document preparation.
- Metered API/MCP calls, storage, compute, notifications or AI usage only when the cost can be measured and shown clearly.
- Provider charges (domain, hosting, email, government fees, etc.) are separate line items and are passed through transparently where applicable.
- Hard usage caps, alerts, spend history and a way to disable paid usage.

### Monthly or yearly plans
- **Individual:** saved workspaces, personal project history, optional sync and priority support.
- **Builder:** multiple projects, deployment assistance, integrations, monitoring and team collaboration.
- **Business:** organisation roles, shared workflows, business setup tracker, inventory/service integrations and support SLA.
- **Partner/agency:** manage multiple customer workspaces with explicit customer delegation, separate billing and audit trails.
- Annual billing may offer a modest discount; clearly show renewal date, cancellation and refund terms.

Do not finalise prices until costs, provider terms, support workload and target-market willingness to pay are measured. Show UGX as a first-class currency for Uganda, with other currencies where useful. No surprise auto-upgrades or hidden usage fees.

## 5. How Otya earns money

1. Transparent service fees for assisted business setup and digital onboarding.
2. Website, domain, email and deployment setup packages.
3. Monthly plans for teams, monitoring, support and repeat workflows.
4. Pay-as-you-go usage for costly services, with limits and clear unit prices.
5. Partner referrals only when disclosed; recommendations must not be secretly ranked by commission.
6. Optional paid Otya Media extras only after core playback is reliable and useful; never make local playback depend on a paid account.

Do not promise that any provider pays referral commission unless a real partner agreement exists.

## 6. Architecture and integration boundaries

- Otya owns the customer journey, service catalogue, workflow state, permissions, receipts, support and audit trail.
- Providers remain authoritative for their accounts, domain registrations, deployments, official filings and charges.
- Use documented provider APIs/OAuth where available; do not automate portals in ways that violate provider terms or bypass user confirmation.
- Cloudflare is the approved runtime and data platform; GitHub is the canonical source-control, review, and CI system; Resend is the shared transactional email provider. Do not introduce Supabase, Appwrite, or Vercel into OtyaPoint or the approved ecosystem foundation unless the owner explicitly approves a documented exception. Avoid duplicate infrastructure just because a provider has a feature.
- Keep product data domains separate: Otya identity does not automatically grant access to OmniPoint financial records, Otya Player private files, or another organisation's data.
- Use per-organisation authorisation, least privilege, MFA for privileged users, immutable security audit records, rate limits, idempotency and revocation.
- AI tools must use an allowlist, structured inputs, server-side permission checks and explicit confirmation for consequential changes. No arbitrary SQL/shell, unrestricted admin, secret retrieval, financial transfers or unattended production deploys.
- Every workflow needs status, owner, next step, estimated cost, required user action, failure recovery and cancellation/export path.

## 7. Suggested delivery order

### Phase 1 — trust and discovery
- Publish the service catalogue and simple “What are you trying to do?” intake.
- Create reviewed guides for Uganda business formalisation, domains, Cloudflare, GitHub and website launch.
- Add provider-cost estimates, official-source dates, privacy notice and support escalation.
- Measure which guides lead to successful completion.

### Phase 2 — guided workspace
- Save checklists and project progress.
- Add read-only connections and diagnostics for one provider at a time.
- Add consent screens, scoped permissions, audit events and connection revocation.
- Keep production changes manual and approval-gated.

### Phase 3 — paid assisted workflows
- Offer one-off packages and limited monthly plans.
- Add transparent usage metering, receipts, budgets, caps and refunds/cancellation policy.
- Pilot with a small number of Ugandan businesses and developers before advertising broadly.

### Phase 4 — controlled automation and MCP
- Publish public read-only MCP tools first.
- Add authenticated personal and organisation tools only after tenant isolation and negative authorisation tests pass.
- Add write tools one workflow at a time with preview, explicit approval, idempotency and rollback.
- Review provider terms, data protection, tax and consumer obligations before handling payments or sensitive documents.

## 8. Minimum acceptance checklist

- [ ] A beginner can start with an outcome, not a vendor name.
- [ ] A developer can switch to technical details without losing the guided route.
- [ ] All fees are split into Otya fee, provider fee and official fee.
- [ ] Official registration and provider actions are never falsely shown as complete.
- [ ] No provider password, OTP, root key or private key is requested in chat.
- [ ] Every connected account shows permissions, last use, and disconnect/revoke controls.
- [ ] Organisation A cannot read or change Organisation B's data.
- [ ] Paid actions require a visible estimate and explicit consent.
- [ ] Usage caps, receipts, export, cancellation and support paths exist.
- [ ] Production changes, deployments and financial actions are approval-gated and audited.
- [ ] Core Otya Player local playback works without login or network.
- [ ] Public OtyaHub resources remain public.

## 9. Success measures

Track completed user outcomes, not just signups:
- time from goal to successful completion;
- guide-to-completion conversion and drop-off reasons;
- successful domain/website launch rate;
- repeat usage and paid conversion by service;
- support resolution time and customer satisfaction;
- unexpected-cost incidents, security incidents and failed/rolled-back changes;
- retention, cancellation reasons and user ability to export or leave.
