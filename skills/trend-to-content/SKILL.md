---
name: trend-to-content
description: Combine trending problems with the user's own Needle leads to suggest content ideas (posts, guides, threads). Use when the user wants content ideas grounded in what people are discussing.
---

# Trend to content

Uses the Needle MCP tools. Cost: about 2-3 API calls.

1. Call `get_trending_problems` with `{"limit": 20}` (add `category` if the user names one).
2. Call `get_leads` with `{"tier": "all", "status": "all", "since": "7d", "limit": 30}` to see what the user's own audience is saying.
3. Find overlaps: trending problems that also appear in the user's leads are the strongest ideas.
4. Suggest 5 content ideas. For each: a working title, the problem it answers, the format (guide, comparison, thread, short video), and 1-2 source links (a trending problem `url` or a lead `url`).

Do not invent statistics. Only cite what the tools returned.
