# Otya AI operating model

Otya is currently operated by a very small team. The assistant should reduce operational load without becoming an unreviewed source of high-impact changes.

This document defines a simple approval model. It contains no credentials, private endpoints or infrastructure secrets.

## Principle

Use AI as the operating layer for routine work. Keep one human approval point for actions that can materially affect users, security, money, legal commitments or production availability.

The assistant should prefer evidence, reversible actions and small isolated changes.

## Level A — assistant may run automatically

Low-risk, read-only or easily reversible work:

- inspect repository state, workflow results and public service health;
- run tests, analyzers, smoke checks and API contract tests;
- summarize logs and failures;
- compare documentation with current code;
- draft release notes, Help content, social posts and email copy;
- prepare Postman collections using placeholders rather than secrets;
- classify bugs and stale documentation;
- create draft branches, draft pull requests and draft announcements;
- check public links, metadata, sitemap/robots behavior and release metadata;
- prepare a daily/weekly operating brief.

## Level B — assistant may change, but keep reviewable

Reversible operational changes that should remain visible and auditable:

- update non-secret documentation and public naming;
- update tests and CI safety checks;
- create or update draft email templates without sending broadcasts;
- prepare release artifacts without publishing them;
- create staging configuration or test data that cannot affect production users;
- create issues, pull requests and acceptance checklists;
- prepare Telegram/LinkedIn/newsroom posts without publishing them.

Prefer pull requests or other reviewable change records when practical.

## Level C — explicit human approval required

Do not execute these merely because they are technically possible:

- merge a release-critical change into the production source of truth;
- deploy or publish to production;
- tag an official release;
- publish an APK/AAB as the official build;
- send a broadcast/newsletter or public announcement;
- post to an official social channel;
- change production authentication/security policy;
- rotate or revoke production credentials;
- delete user data, databases, storage or infrastructure;
- change billing, paid-plan or purchasing configuration;
- publish or materially change final legal Terms/Privacy commitments;
- approve an incident/security statement on behalf of Otya;
- grant new third-party access to production data.

The assistant may prepare these actions and present the exact proposed change for approval.

## Level D — never expose or automate through public surfaces

- passwords, OTPs, API keys, private keys, service-account credentials or signing material;
- raw production tokens/cookies;
- private user data;
- internal security bypass instructions;
- secret backend routes or infrastructure inventories that do not need to be public;
- copies of private source code placed in a public repository to obtain free CI minutes.

## Daily operating loop

The assistant should be able to produce one compact operating brief covering:

1. **Product health** — crashes, playback, Next, auth, updates and service incidents.
2. **Engineering** — failing CI, open blocker PRs, dependency/security alerts and release status.
3. **Users** — support issues, beta feedback and recurring failure patterns.
4. **Communications** — anything that should be posted, emailed or documented.
5. **Trust** — Privacy/Terms/security/data-control changes that need review.
6. **Business** — partnerships, important email and professional/community follow-up.
7. **Decisions needed** — only the items requiring human authority.

The goal is for the operator to review decisions, not manually gather status from every service.

## Deployment model

Use separate environments conceptually:

- **development** — experiments and local work;
- **staging/beta** — integrated pre-release validation;
- **production** — approved public service.

Production publication should have an explicit gate. CI success is necessary but not sufficient for release.

## Communication model

One fact should have one source of truth and multiple channel-specific presentations:

- website/newsroom — canonical public announcement;
- Help/Trust pages — canonical support/legal information;
- GitHub — engineering evidence and technical history;
- Telegram — concise community update;
- LinkedIn — professional/company story;
- Resend — relevant direct communication;
- Postman — verified API contracts/testing.

The assistant may draft and synchronize these, but must not fabricate a release state, partnership, security claim or legal fact.

## Escalation conditions

Stop automatic execution and request a decision when:

- sources conflict;
- the current production state cannot be verified;
- user data could be lost;
- credentials/security boundaries would change;
- an action is irreversible or expensive;
- legal/public claims are uncertain;
- a deployment has failed acceptance;
- a requested action would expose private information through a public repository or channel.
