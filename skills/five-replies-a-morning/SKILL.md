---
name: five-replies-a-morning
description: Draft replies for the user's top 5 Needle leads so they can post them in one sitting. Use when the user wants reply drafts for their best leads.
---

# Five replies a morning

Uses the Needle MCP tools. Cost: about 7-12 API calls and 5 of the user's daily reply drafts. Call `get_usage` first if unsure there are 5 drafts left.

1. Call `get_leads` with `{"tier": "hot_lead", "limit": 10}`. If fewer than 5 come back, call it again with `{"limit": 10}` (hot and worth-engaging).
2. Pick the 5 strongest (highest `lead_score`, clear `evidence`).
3. For each, call `draft_reply` with `{"lead_id": "…"}`. Use `"strategy": "pure_value"` when the post asks a question your product does not directly answer.
4. Show each lead's title and `url`, then the `best` draft and the `alternate`. If `fit_warning` is set, say why the lead may be a poor fit.
5. Remind the user that Needle never posts: they paste and post the reply themselves. After they confirm which ones they posted, call `update_lead_status` with those ids and `"status": "replied"`.
