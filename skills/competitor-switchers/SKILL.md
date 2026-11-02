---
name: competitor-switchers
description: Find people in the user's Needle leads who are leaving or unhappy with a competitor, and suggest an outreach angle for each. Use when the user asks about competitor switchers or churn from a rival tool.
---

# Competitor switchers

Uses the Needle MCP tools. Cost: about 2-6 API calls.

1. Call `get_leads` with `{"intent_type": "switching", "tier": "all", "since": "7d", "limit": 50}`.
2. Group the leads by the names in `competitor_mentions` (leads with none go under "unnamed tool").
3. For each group, read the `evidence` text and summarise why people are leaving (price, missing feature, support, reliability). Quote short phrases.
4. Suggest one honest outreach angle per group, based on what the user's product does better. Use `list_brands` if you need the product's description and keywords.
5. List each lead with its `url` so the user can reply. Offer `draft_reply` for any of them.
