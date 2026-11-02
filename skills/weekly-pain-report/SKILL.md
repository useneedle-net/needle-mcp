---
name: weekly-pain-report
description: Turn the past week's Needle leads into a report of the main pains and questions people raised, with quotes and links. Use for weekly customer research or roadmap input.
---

# Weekly pain report

Uses the Needle MCP tools. Cost: about 2-6 API calls.

1. Call `get_leads` with `{"intent_type": "pain", "tier": "all", "status": "all", "since": "7d", "limit": 50}`, then again with `"intent_type": "question"`. Follow `next_cursor` at most twice per query.
2. Cluster the posts into 3-7 themes by what the person is struggling with.
3. For each theme: a one-sentence summary, how many posts, 2-3 short quotes from `evidence` or `excerpt`, and their `url`s.
4. End with the 3 themes that best match the user's product (use `list_brands` for its description) and one suggested action for each.

Quote people accurately and keep quotes short. Do not include author names in the report unless the user asks.
