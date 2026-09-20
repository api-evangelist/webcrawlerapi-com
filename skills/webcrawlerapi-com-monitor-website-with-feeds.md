---
generated: '2026-09-19'
method: generated
name: Monitor a website for changes with Feeds
description: Create a scheduled change-detection feed for a site, consume the changes as Atom 1.0 / JSON Feed 1.1 or a webhook, and pause, resume, force-run or delete the feed.
api: openapi/webcrawlerapi-com-openapi.yml
operations: [createFeed, getFeed, listFeeds, getFeedRss, getFeedJson, pauseFeed, resumeFeed, runFeed, resendFeedWebhook, deleteFeed]
operation_id_note: Overlay-assigned names (overlays/webcrawlerapi-com-openapi-overlay.yaml) for POST /v2/feed, GET /v2/feed/{id}, GET /v2/feeds, GET /v2/feed/{id}/rss, GET /v2/feed/{id}/json, PUT /v2/feed/{id}/pause|resume|run, POST /v2/feed/{id}/webhook/resend, DELETE /v2/feed/{id} - all verbatim in openapi/_original/webcrawlerapi-com-swagger.json.
source: >-
  Grounded in openapi/_original/webcrawlerapi-com-swagger.json (Feeds tag) and https://webcrawlerapi.com/docs/feeds + /docs/api/feed/*.
  Limits per rate-limits/webcrawlerapi-com-rate-limits.yml, reversibility per conventions/webcrawlerapi-com-conventions.yml,
  webhook semantics per asyncapi/webcrawlerapi-com-webhooks.yml.
---

# Monitor a website for changes with Feeds

A feed re-crawls a URL on a schedule and reports only what changed — new, changed, unavailable (and, opted in, error) pages — as a standard syndication feed or a webhook. Each run is billed like a crawl job (per page).

## Auth
- `Authorization: Bearer <API key>`. Base URL `https://api.webcrawlerapi.com`. Note the reference pages and the Swagger document use `/v2/feed`; the overview page still shows `/v1/feeds` — use `/v2`.

## Steps

1. **Create** — `createFeed` (`POST /v2/feed`) with `url` (required) and, as needed, `name`, `output_format` (`markdown` default | `cleaned` | `html`), `items_limit` (default 10), `max_depth` (0–10), `whitelist_regexp` / `blacklist_regexp`, `respect_robots_txt`, `main_content_only`, `include_errors`, `webhook_url`. The response is a `FeedResponse` with `id`, `status: active` and `next_run_at`.
2. **Consume changes** — pick one:
   - `getFeedRss` (`GET /v2/feed/{id}/rss?page=&page_size=`) — Atom 1.0 with RFC 5005 paging; each entry carries a `category` term of `new` | `changed` | `unavailable` | `error`.
   - `getFeedJson` (`GET /v2/feed/{id}/json`) — JSON Feed 1.1; provider fields live under `_webcrawlerapi` (`change_type`, `page_status_code`, `content_url`, `page_size`).
   - a `webhook_url` — a POST per run with the change set; re-deliver with `resendFeedWebhook` if your endpoint missed it. Payloads are **unsigned**; verify by re-reading the feed with your own key.
   Page content is fetched separately from each item's `content_url`.
3. **Inspect** — `getFeed` (`GET /v2/feed/{id}`) returns `recent_runs[]` (`pages_crawled / changed / new / unavailable / errors`, `cost_usd`); `listFeeds` (`GET /v2/feeds`) lists the organization's feeds.
4. **Operate** — `pauseFeed` / `resumeFeed` (`PUT /v2/feed/{id}/pause|resume`) are a reversible pair; `runFeed` (`PUT /v2/feed/{id}/run`) forces an extra run; `deleteFeed` (`DELETE /v2/feed/{id}`) is terminal.

## Rules an agent must follow

- **Ceilings.** Max **100 feeds per organization**; force-run at most **once per hour** per feed (a second attempt returns `400` with a wait message, not `429`) and only while the feed is `active` with balance ≥ 10,000 micro-dollars; `page_size` max 1000. See `rate-limits/`.
- **Reversibility.** Pause is fully reversible; a canceled/deleted feed cannot be paused or resumed. No time window is stated — there is nothing to refund because runs are billed as they happen. See `conventions/`.
- **Auto-pause.** The provider pauses a feed after 3 consecutive errored runs; poll `getFeed` for `status` before assuming it is still running.
- **No idempotency key.** A retried `createFeed` makes a second feed that will also bill on every run; check `listFeeds` before re-creating.
- **Errors** are `{error_code, error_message}` JSON (`400` invalid regex/URL or invalid state transition, `402` insufficient balance, `403` organization suspended, `404` feed not yours). See `errors/`.
