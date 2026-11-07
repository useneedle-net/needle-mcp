# Changelog

The Needle MCP server (`https://api.useneedle.net/mcp`) and REST API (`https://api.useneedle.net/v1`) share one version. Tools, endpoints, inputs and output fields are never renamed or removed; a breaking change would get a new major version and at least a month in which the old behaviour keeps working.

## 1.2.0 (2026-11-07)

- Tool errors now carry the same fields as REST errors: after the `code: message` line comes a JSON line with `details` (for example the running search's `search_id`), `doc_url` and `request_id`.
- Every response has an `X-Request-ID` header, and REST error bodies include `doc_url` and `request_id`.
- `api_plan_required` says why access is missing (`details.reason`: plan, trial ended or plan inactive) and where to upgrade (`details.upgrade_url`).
- Clearer `invalid_token` messages for a truncated key or an unsupported `Authorization` scheme.
- `search.networks` and `get_leads.platform` accept network names as well as ids, and an unknown network is a `400` listing the valid ids.
- Tool annotations: `update_lead_status` is marked destructive (it overwrites triage state), and `draft_reply` is marked open-world (it reads the live thread and calls a language model).
- Server instructions and tool descriptions say that post content is third-party data, and ask clients to confirm before write tools. Tool summaries quote post titles.
- The OpenAPI document now lists the `202`, `409`, `413` and `502` responses, response headers, error codes and request examples, and uses REST wording.

## 1.1.0 (2026-11-02)

- Sign in with OAuth 2.1 (PKCE, rotating refresh tokens, client ID metadata documents and dynamic client registration). An API key is no longer required.

## 1.0.0 (2026-11-02)

- First release: 9 tools over Streamable HTTP with API keys, and the matching REST API.
