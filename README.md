# WebCrawlerAPI

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

WebCrawlerAPI is a web crawling and scraping API from 103 Labs (Netherlands) that turns websites into clean, LLM-ready markdown, cleaned text, HTML or link lists for AI agents, support bots and RAG pipelines. It offers asynchronous multi-page crawl jobs (POST /v1/crawl with polling or webhooks), single-page scraping (POST /v2/scrape, sync or async, with prompt-based structured outputs validated against a JSON Schema), scheduled change-detection Feeds delivered as Atom 1.0, JSON Feed 1.1 or webhooks, a prompt-driven autonomous crawling agent with a required per-run spend cap, and organization usage/balance endpoints. Requests authenticate with a Bearer API key; usage is metered per successfully crawled page on a $0/month pay-as-you-go tier or $29/$99/$499 monthly plans, with 7-day caching (cache hits free). Published surfaces: a Swagger 2.0 document behind a live Swagger UI, an Agent API OpenAPI 3.0.3, an A2A agent card and RFC 9727 API catalog at /.well-known/, llms.txt, SDKs for JavaScript, Python, PHP, .NET and Java, an npm MCP server (local stdio), the webcr CLI, a Claude Code Agent Skill, a public Postman collection and a dated changelog.

**Areas:** Web Scraping · Web Crawling · Data Extraction · Markdown · AI Agents · LLM · RAG · Web Feeds · Change Detection · Structured Data · MCP · A2A

## WebCrawlerAPI on APIs.io

Everything profiled for WebCrawlerAPI is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/webcrawlerapi-com/](https://apis.io/providers/webcrawlerapi-com/)** — or go straight to one of the APIs or properties below.

### APIs (8)

- [WebCrawlerAPI MCP Server](https://apis.io/apis/webcrawlerapi-com/webcrawlerapi-mcp-server/) — Official Model Context Protocol server distributed as the npm package webcrawler-mcp (npx -y webcrawler-mcp) and run locally over stdio - or self-hosted…
- [WebCrawlerAPI Agent Card](https://apis.io/apis/webcrawlerapi-com/webcrawlerapi-a2a-agent-card/) — A2A-style agent card served from https://webcrawlerapi.com/.well-known/agent-card.json describing "WebCrawlerAPI Agent" (version 1.0.0) with three skills -…
- [WebCrawlerAPI Agent API](https://apis.io/apis/webcrawlerapi-com/webcrawlerapi-com-agent-api/) — The Agent API from WebCrawlerAPI — 3 operation(s) for agent.
- [WebCrawlerAPI Feeds API](https://apis.io/apis/webcrawlerapi-com/webcrawlerapi-com-feeds-api/) — The Feeds API from WebCrawlerAPI — 9 operation(s) for feeds.
- [WebCrawlerAPI Jobs API](https://apis.io/apis/webcrawlerapi-com/webcrawlerapi-com-jobs-api/) — The Jobs API from WebCrawlerAPI — 6 operation(s) for jobs.
- [WebCrawlerAPI Organization API](https://apis.io/apis/webcrawlerapi-com/webcrawlerapi-com-organization-api/) — The Organization API from WebCrawlerAPI — 1 operation(s) for organization.
- [WebCrawlerAPI Status API](https://apis.io/apis/webcrawlerapi-com/webcrawlerapi-com-status-api/) — The Status API from WebCrawlerAPI — 2 operation(s) for status.
- [WebCrawlerAPI V2 Scraping API](https://apis.io/apis/webcrawlerapi-com/webcrawlerapi-com-v2-scraping-api/) — The V2 Scraping API from WebCrawlerAPI — 2 operation(s) for v2 scraping.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Webcrawlerapi Com Webhooks](https://apis.io/asyncapis/webcrawlerapi-com/webcrawlerapi-com-webhooks/)

#### MCP servers (2)

Model Context Protocol servers that expose the API to agents.

- [webcrawler-mcp](https://apis.io/servers/webcrawlerapi-com/webcrawler-mcp/)
- [webcrawler-mcp on npm (local stdio package)](https://apis.io/servers/webcrawlerapi-com/webcrawler-mcp-on-npm-local-stdio-package/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Webcrawlerapi Com Openapi Overlay](https://apis.io/overlays/webcrawlerapi-com/webcrawlerapi-com-openapi-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Webcrawlerapi Com Authentication](https://apis.io/security/webcrawlerapi-com/webcrawlerapi-com-authentication/)
- [Webcrawlerapi Com Domain Security](https://apis.io/security/webcrawlerapi-com/webcrawlerapi-com-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Webcrawlerapi Com Plans Pricing](https://apis.io/plans/webcrawlerapi-com/webcrawlerapi-com-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Webcrawlerapi Com Rate Limits](https://apis.io/rate-limits/webcrawlerapi-com/webcrawlerapi-com-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://webcrawlerapi.com/)
- [Documentation](https://webcrawlerapi.com/docs/getting-started)
- [Getting started](https://webcrawlerapi.com/docs/getting-started)
- [API reference](https://api.webcrawlerapi.com/swagger/index.html)
- [Pricing](https://webcrawlerapi.com/docs/pricing)
- [Sign up](https://dash.webcrawlerapi.com/sign-up)
- [Changelog](https://webcrawlerapi.com/changelog)
- [Blog](https://webcrawlerapi.com/blog)
- [Terms of service](https://webcrawlerapi.com/tos)
- [Privacy policy](https://webcrawlerapi.com/privacy)
- [GitHub](https://github.com/WebCrawlerAPI)
- [Status](https://status.webcrawlerapi.com)

## API Evangelist rating

**Kin Score 64.6** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 88.3 |
| Contract quality | 57.2 |
| Contract governance | 18.2 |
| Operational transparency | 44.7 |
| Developer ergonomics | 83.3 |
| Access clarity | 76.3 |

**Agent readiness 43.0** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | documented (partial credit) |
| MCP Server | documented (partial credit) |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | yes |
| Well Known Catalog | yes |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | paginated |
| Operation Distinctiveness | distinct |

**Regulatory alignment 30.0** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/webcrawlerapi-com/](https://apis.io/providers/webcrawlerapi-com/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for WebCrawlerAPI: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/webcrawlerapi-com/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
