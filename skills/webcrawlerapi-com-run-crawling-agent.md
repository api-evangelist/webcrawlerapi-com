---
generated: '2026-09-19'
method: generated
name: Run the WebCrawlerAPI crawling agent
description: Start a prompt-driven crawling-agent (Wagent) run with a hard spend cap and an optional JSON Schema, poll it to completion, and read the extracted data.
api: openapi/webcrawlerapi-com-openapi.yml
operations: [runAgent, getAgentJob, listAgentJobs]
operation_id_note: The provider's Swagger document ships no operationIds; these names come from overlays/webcrawlerapi-com-openapi-overlay.yaml and map to POST /v1/agent, GET /v1/agent/job/{id}, GET /v1/agent/jobs, which are verbatim in openapi/_original/webcrawlerapi-com-swagger.json.
source: >-
  Grounded in openapi/_original/webcrawlerapi-com-swagger.json (Agent tag), openapi/_original/webcrawlerapi-com-agent-openapi.json
  and https://webcrawlerapi.com/docs/api/agent/agent-run + /docs/crawling-agent. Auth per authentication/webcrawlerapi-com-authentication.yml,
  errors per errors/webcrawlerapi-com-problem-types.yml, money rules per conventions/webcrawlerapi-com-conventions.yml and plans/.
---

# Run the WebCrawlerAPI crawling agent

The crawling agent browses from seed URLs, follows the links it judges relevant, and returns JSON shaped by your prompt (and, optionally, your schema). It is billed per LLM token **plus** per page visited, so the spend cap is not optional.

## Auth
- `Authorization: Bearer <API key>` from https://dash.webcrawlerapi.com/access. Base URL `https://api.webcrawlerapi.com`.

## Steps

1. **Start the run** — `runAgent` (`POST /v1/agent`) with a JSON body:
   - `prompt` (required) — what to find or extract, in plain language.
   - `max_spend_usd` (required, > 0) — the hard ceiling for this run. The API rejects a missing or zero value with `400`.
   - `urls` — seed URLs; add `"seed_urls_only": true` to stop the agent following links.
   - `output_schema` — a strict JSON Schema (root `object`, every property in `required`, `additionalProperties: false`, null unions for optional fields) when you need a fixed shape.
   - `model` — one of the models listed on the reference page (e.g. `openai/gpt-5.4-mini`, `anthropic/claude-sonnet-4.6`).
   - `max_age` — reuse a cached run for the same model + prompt + URLs; cache hits are free.
   The response is an `AgentRunView` with `status: in_progress` and an `id`. **Persist the id immediately** — there is no idempotency key, and a retried POST starts a second billable run.
2. **Poll** — `getAgentJob` (`GET /v1/agent/job/{id}`) until `status` is `done`, `error` or `canceled`. Agent runs have no `webhook_url`; polling is the only completion signal. Back off between polls; the run object carries no recommended delay.
3. **Read the result** — on `done`, `data` holds the extracted JSON (matching `output_schema` when one was given), `success` is `true` only when `data` is non-empty, and `balance_used_usd` tells you what the run actually cost against `max_spend_usd`. On `error`, read `error_reason`.
4. **Audit** — `listAgentJobs` (`GET /v1/agent/jobs?limit=&offset=`) returns `{items, total}` for the organization; use it to find a run whose id you lost before starting another.

## Rules an agent must follow

- **Cap first, then prompt.** `max_spend_usd` is the only brake: there is no cancel operation for an agent run in the spec (the status enum includes `canceled`, but nothing exposes it), so a run cannot be stopped once started. Size the cap to the task (docs guide: ~$0.004–0.02 in tokens per page plus the plan's per-page rate).
- **No retries without a lookup.** No idempotency mechanism exists (`conventions/`). If the POST times out, check `listAgentJobs` before posting again.
- **Balance before launch.** A `402` means the organization balance cannot cover the run; check `GET /organization/balance` (documented, not in the Swagger) or top up in the dashboard.
- **Errors are not RFC 9457.** Expect `{error_code, error_message}` JSON; `401` returns `{error, message}`. See `errors/`.
- **Robots and politeness.** The agent shares the provider's 10-parallel-threads-per-target ceiling with every other customer; throughput on a busy site is not yours to set.
