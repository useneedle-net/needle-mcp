---
name: daily-lead-shortlist
description: Build today's shortlist of Needle leads worth replying to, with a one-line reason each, and dismiss the obvious misses. Use when the user asks who to reply to today or wants their Needle inbox triaged.
---

# Daily lead shortlist

Uses the Needle MCP tools. Cost: about 2-4 API calls (`get_leads`, optional `get_lead`, one `update_lead_status`).

1. Call `get_leads` with `{"since": "24h", "limit": 30}` (actionable leads still in the inbox).
2. Rank them: `hot_lead` before `worth_engaging`, then by `lead_score`. Read the `evidence` text and `intent_type`.
3. For any lead whose excerpt is too short to judge, call `get_lead` (at most 3).
4. Show the user the top 5-10 as a list: title, network, one line on why it is worth a reply, and the `url`.
5. List the clear misses (off-topic, spam, already solved) and ask before acting. If the user agrees, call `update_lead_status` once with all their ids and `"status": "dismissed"`.

Do not draft replies here; offer the five-replies-a-morning workflow instead.
