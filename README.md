# Needle MCP server

Connect Claude, Cursor and other MCP clients to your [Needle](https://useneedle.net) leads: see who to reply to, read a lead in full, draft a reply in your brand voice, mark leads as handled, and run new searches across Reddit, Hacker News, forums and more.

- **URL:** `https://api.useneedle.net/mcp` (Streamable HTTP)
- **Auth:** an API key from Needle **Settings → API & MCP** (Growth and Scale plans)
- **Docs:** [useneedle.net/docs/mcp](https://useneedle.net/docs/mcp) (tools, limits, errors) and the [REST API](https://useneedle.net/docs/api)

## Set up

**Claude Code**

```bash
claude mcp add --transport http needle https://api.useneedle.net/mcp --header "Authorization: Bearer ndl_live_…"
```

**Cursor, Windsurf and other clients** (`mcp.json`):

```json
{
  "mcpServers": {
    "needle": {
      "url": "https://api.useneedle.net/mcp",
      "headers": { "Authorization": "Bearer ndl_live_…" }
    }
  }
}
```

## Skills

Ready-made workflows in Agent Skills format (`skills/<name>/SKILL.md`). Each states roughly how many API calls it uses.

| Skill | What it does |
| --- | --- |
| [daily-lead-shortlist](skills/daily-lead-shortlist/SKILL.md) | Today's best leads with a one-line "why reply", skips dismissed |
| [five-replies-a-morning](skills/five-replies-a-morning/SKILL.md) | Drafts replies for your top 5 leads |
| [competitor-switchers](skills/competitor-switchers/SKILL.md) | People leaving a competitor, with outreach angles |
| [weekly-pain-report](skills/weekly-pain-report/SKILL.md) | The week's pains and questions, clustered with quotes |
| [trend-to-content](skills/trend-to-content/SKILL.md) | Content ideas from trending problems and your leads |

Needle never posts for you: drafts are text for you to review and post.

## License

MIT © VS NextGen Solutions. Questions: support@useneedle.net
