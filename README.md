# G2

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

G2 is the world's largest B2B software marketplace, built on more than three million verified peer reviews and used by over 100 million software buyers a year. The G2 API provides programmatic access to G2's product catalog, category taxonomy, vendor records, reviews, badges, Grid reports, buyer intent signals and competitive intelligence. The v2 REST surface is a JSON:API contract of 62 operations served from data.g2.com, alongside a separate Data Solutions API for enriched flat-structure review data and a first-party remote MCP server at mcp.g2.com that exposes 21 tools to AI agents over OAuth 2.0. Authentication is by Developer Portal account token or OAuth 2.0 authorization code with PKCE, and most data surfaces are gated by subscription entitlement.

**Areas:** B2B · Software Discovery · Software Reviews · Buyer Intent · Market Intelligence · Product Catalog · Competitive Intelligence · Reviews · Data Solutions · MCP

## G2 on APIs.io

Everything profiled for G2 is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/g2/](https://apis.io/providers/g2/)** — or go straight to one of the APIs or properties below.

### APIs (29)

- [G2 MCP Server](https://apis.io/apis/g2/g2-mcp-server/) — G2's first-party remote Model Context Protocol server. It exposes 21 tools covering buyer intent signals, competitive intelligence, the product and category…
- [G2 Buyer Intent API](https://apis.io/apis/g2/g2-buyer-intent-api/) — The Buyer Intent API from G2 — 3 operation(s) for buyer intent.
- [G2 Categories API](https://apis.io/apis/g2/g2-categories-api/) — The Categories API from G2 — 2 operation(s) for categories.
- [G2 Chat Gpt Plugin API](https://apis.io/apis/g2/g2-chat-gpt-plugin-api/) — The Chat Gpt Plugin API from G2 — 2 operation(s) for chat gpt plugin.
- [G2 Competitors API](https://apis.io/apis/g2/g2-competitors-api/) — The Competitors API from G2 — 1 operation(s) for competitors.
- [G2 Credit Account API](https://apis.io/apis/g2/g2-credit-account-api/) — The Credit Account API from G2 — 2 operation(s) for credit account.
- [G2 Data Solutions Reviews API](https://apis.io/apis/g2/g2-data-solutions-reviews-api/) — The Data Solutions Reviews API from G2 — 1 operation(s) for data solutions reviews.
- [G2 Data Subscriptions API](https://apis.io/apis/g2/g2-data-subscriptions-api/) — The Data Subscriptions API from G2 — 2 operation(s) for data subscriptions.
- [G2 Discussions API](https://apis.io/apis/g2/g2-discussions-api/) — The Discussions API from G2 — 1 operation(s) for discussions.
- [G2 Downloads API](https://apis.io/apis/g2/g2-downloads-api/) — The Downloads API from G2 — 1 operation(s) for downloads.
- [G2 G2 Activate API](https://apis.io/apis/g2/g2-g2-activate-api/) — The G2 Activate API from G2 — 4 operation(s) for g2 activate.
- [G2 Integration Reviews API](https://apis.io/apis/g2/g2-integration-reviews-api/) — The Integration Reviews API from G2 — 1 operation(s) for integration reviews.
- [G2 Market Signals API](https://apis.io/apis/g2/g2-market-signals-api/) — The Market Signals API from G2 — 1 operation(s) for market signals.
- [G2 Medals API](https://apis.io/apis/g2/g2-medals-api/) — The Medals API from G2 — 1 operation(s) for medals.
- [G2 Performance Analytics API](https://apis.io/apis/g2/g2-performance-analytics-api/) — The Performance Analytics API from G2 — 5 operation(s) for performance analytics.
- [G2 Product Features API](https://apis.io/apis/g2/g2-product-features-api/) — The Product Features API from G2 — 4 operation(s) for product features.
- [G2 Product Mappings API](https://apis.io/apis/g2/g2-product-mappings-api/) — The Product Mappings API from G2 — 2 operation(s) for product mappings.
- [G2 Product Ratings API](https://apis.io/apis/g2/g2-product-ratings-api/) — The Product Ratings API from G2 — 1 operation(s) for product ratings.
- [G2 Product Videos API](https://apis.io/apis/g2/g2-product-videos-api/) — The Product Videos API from G2 — 1 operation(s) for product videos.
- [G2 Products API](https://apis.io/apis/g2/g2-products-api/) — The Products API from G2 — 3 operation(s) for products.
- [G2 Questions API](https://apis.io/apis/g2/g2-questions-api/) — The Questions API from G2 — 2 operation(s) for questions.
- [G2 Reports API](https://apis.io/apis/g2/g2-reports-api/) — The Reports API from G2 — 1 operation(s) for reports.
- [G2 Research Boards API](https://apis.io/apis/g2/g2-research-boards-api/) — The Research Boards API from G2 — 6 operation(s) for research boards.
- [G2 Reviews API](https://apis.io/apis/g2/g2-reviews-api/) — The Reviews API from G2 — 2 operation(s) for reviews.
- [G2 Screenshots API](https://apis.io/apis/g2/g2-screenshots-api/) — The Screenshots API from G2 — 3 operation(s) for screenshots.
- [G2 Snippets API](https://apis.io/apis/g2/g2-snippets-api/) — The Snippets API from G2 — 1 operation(s) for snippets.
- [G2 Users API](https://apis.io/apis/g2/g2-users-api/) — The Users API from G2 — 1 operation(s) for users.
- [G2 Vendors API](https://apis.io/apis/g2/g2-vendors-api/) — The Vendors API from G2 — 2 operation(s) for vendors.
- [G2 Video Reviews API](https://apis.io/apis/g2/g2-video-reviews-api/) — The Video Reviews API from G2 — 1 operation(s) for video reviews.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [G2 Webhooks](https://apis.io/asyncapis/g2/g2-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [G2 MCP Server](https://apis.io/servers/g2/g2-mcp-server/)

#### Overlays (30)

OpenAPI overlays, including conversational phrasing for each operation.

- [G2 Api V2 Overlay](https://apis.io/overlays/g2/g2-api-v2-overlay/)
- [G2 Buyer Intent Api Phrasing Overlay](https://apis.io/overlays/g2/g2-buyer-intent-api-phrasing-overlay/)
- [G2 Categories Api Phrasing Overlay](https://apis.io/overlays/g2/g2-categories-api-phrasing-overlay/)
- [G2 Chat Gpt Plugin Api Phrasing Overlay](https://apis.io/overlays/g2/g2-chat-gpt-plugin-api-phrasing-overlay/)
- [G2 Competitors Api Phrasing Overlay](https://apis.io/overlays/g2/g2-competitors-api-phrasing-overlay/)
- [G2 Credit Account Api Phrasing Overlay](https://apis.io/overlays/g2/g2-credit-account-api-phrasing-overlay/)
- [G2 Data Solutions Overlay](https://apis.io/overlays/g2/g2-data-solutions-overlay/)
- [G2 Data Solutions Reviews Api Phrasing Overlay](https://apis.io/overlays/g2/g2-data-solutions-reviews-api-phrasing-overlay/)
- [G2 Data Subscriptions Api Phrasing Overlay](https://apis.io/overlays/g2/g2-data-subscriptions-api-phrasing-overlay/)
- [G2 Discussions Api Phrasing Overlay](https://apis.io/overlays/g2/g2-discussions-api-phrasing-overlay/)
- [G2 Downloads Api Phrasing Overlay](https://apis.io/overlays/g2/g2-downloads-api-phrasing-overlay/)
- [G2 G2 Activate Api Phrasing Overlay](https://apis.io/overlays/g2/g2-g2-activate-api-phrasing-overlay/)
- [G2 Integration Reviews Api Phrasing Overlay](https://apis.io/overlays/g2/g2-integration-reviews-api-phrasing-overlay/)
- [G2 Market Signals Api Phrasing Overlay](https://apis.io/overlays/g2/g2-market-signals-api-phrasing-overlay/)
- [G2 Medals Api Phrasing Overlay](https://apis.io/overlays/g2/g2-medals-api-phrasing-overlay/)
- [G2 Performance Analytics Api Phrasing Overlay](https://apis.io/overlays/g2/g2-performance-analytics-api-phrasing-overlay/)
- [G2 Product Features Api Phrasing Overlay](https://apis.io/overlays/g2/g2-product-features-api-phrasing-overlay/)
- [G2 Product Mappings Api Phrasing Overlay](https://apis.io/overlays/g2/g2-product-mappings-api-phrasing-overlay/)
- [G2 Product Ratings Api Phrasing Overlay](https://apis.io/overlays/g2/g2-product-ratings-api-phrasing-overlay/)
- [G2 Product Videos Api Phrasing Overlay](https://apis.io/overlays/g2/g2-product-videos-api-phrasing-overlay/)
- [G2 Products Api Phrasing Overlay](https://apis.io/overlays/g2/g2-products-api-phrasing-overlay/)
- [G2 Questions Api Phrasing Overlay](https://apis.io/overlays/g2/g2-questions-api-phrasing-overlay/)
- [G2 Reports Api Phrasing Overlay](https://apis.io/overlays/g2/g2-reports-api-phrasing-overlay/)
- [G2 Research Boards Api Phrasing Overlay](https://apis.io/overlays/g2/g2-research-boards-api-phrasing-overlay/)
- [G2 Reviews Api Phrasing Overlay](https://apis.io/overlays/g2/g2-reviews-api-phrasing-overlay/)
- …and 5 more published on APIs.io

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [G2 Authentication](https://apis.io/security/g2/g2-authentication/)
- [G2 Domain Security](https://apis.io/security/g2/g2-domain-security/)
- [G2 Trust Center](https://apis.io/security/g2/g2-trust-center/)
- [G2 Vulnerability Disclosure](https://apis.io/security/g2/g2-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [G2 Scopes](https://apis.io/scopes/g2/g2-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [G2 Plans Pricing](https://apis.io/plans/g2/g2-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [G2 Rate Limits](https://apis.io/rate-limits/g2/g2-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [G2 Finops](https://apis.io/finops/g2/g2-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.g2.com/)
- [Documentation](https://documentation.g2.com/docs/g2-api)
- [Getting started](https://documentation.g2.com/docs/g2-api-information)
- [API reference](https://data.g2.com/api/v2/docs/index.html)
- [Pricing](https://sell.g2.com/plans)
- [Sign up](https://www.g2.com/users/sign_up)
- [Support](https://support.g2.com/s/)
- [Blog](https://learn.g2.com/)
- [Terms of service](https://legal.g2.com/terms-of-use)
- [Privacy policy](https://legal.g2.com/privacy-policy)
- [GitHub](https://github.com/g2crowd)

## API Evangelist rating

**Kin Score 69.0** — exemplar · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 80.0 |
| Contract quality | 60.0 |
| Contract governance | 18.2 |
| Operational transparency | 57.9 |
| Developer ergonomics | 56.5 |
| Access clarity | 92.1 |

**Agent readiness 58.3** — agent-native

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | verified |
| Auth Clarity | served (partial credit) |
| Idempotency | documented (partial credit) |
| Error Semantics | verified |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | partial |
| Operation Distinctiveness | distinct |

**Regulatory alignment 45.1** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/g2/](https://apis.io/providers/g2/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for G2: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/g2/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
