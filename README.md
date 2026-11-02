# Needle MCP server

Connect Claude, ChatGPT, Cursor and other MCP clients to your [Needle](https://useneedle.net) leads: see who to reply to, read a lead in full, draft a reply in your brand voice, mark leads as handled, and run new searches across Reddit, Hacker News, forums and more.

[![Add Needle to Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/install-mcp?name=needle&config=eyJ1cmwiOiJodHRwczovL2FwaS51c2VuZWVkbGUubmV0L21jcCJ9)

- **URL:** `https://api.useneedle.net/mcp` (Streamable HTTP)
- **Auth:** sign in with your Needle account (OAuth), or an API key from Needle **Settings → API & MCP**. Growth and Scale plans.
- **Docs:** [useneedle.net/docs/mcp](https://useneedle.net/docs/mcp) (tools, limits, errors) and the [REST API](https://useneedle.net/docs/api)

## Set up

**claude.ai and Claude Desktop:** Settings → Connectors → **Add custom connector**, paste `https://api.useneedle.net/mcp`, then **Connect** and allow access on the Needle page that opens.

**ChatGPT:** add a custom connector (developer mode) with the URL `https://api.useneedle.net/mcp` and OAuth authentication, then sign in to Needle.

**Claude Code**

```bash
claude mcp add --transport http needle https://api.useneedle.net/mcp
```

Then run `/mcp`, pick **needle** and authenticate in the browser.

**Cursor:** use the button above, or add this to `mcp.json` and click **Connect**:

```json
{
  "mcpServers": {
    "needle": { "url": "https://api.useneedle.net/mcp" }
  }
}
```

**With an API key** (Windsurf, scripts, or any client that cannot sign in):

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

Apps you sign in with are listed in Needle under **Settings → API & MCP → Connected apps**, where you can disconnect them.

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
