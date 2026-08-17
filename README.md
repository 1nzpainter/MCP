# My Painting Club — Painting Lesson Knowledge Base (MCP Server)

[![smithery badge](https://smithery.ai/badge/mypaintingclub/painting_lessons)](https://smithery.ai/servers/mypaintingclub/painting_lessons)

A remote MCP (Model Context Protocol) server that lets AI agents search transcribed painting lessons from [mypaintingclub.com](https://mypaintingclub.com).

## What it does

The `search_painting_lessons` tool answers natural-language painting technique questions using real transcribed lesson content. Every result includes:

- **Answer text** — the relevant passage from the lesson
- **Lesson title** and **sales page URL** on mypaintingclub.com
- **Vimeo deep link** — a timestamped URL that seeks to the exact moment in the video

Topics covered: colour mixing, edges, composition, value, brushwork, oils, acrylics.

## Connect via MCP

**Server URL:** `https://mypaintingclub.com/kb/mcp`  
**Protocol:** Streamable HTTP (MCP 2025-03-26)  
**Auth:** None required

### Claude Desktop (`claude_desktop_config.json`)

```json
{
  "mcpServers": {
    "mpc-painting-lessons": {
      "type": "streamable-http",
      "url": "https://mypaintingclub.com/kb/mcp"
    }
  }
}
```

### Cursor / other MCP clients

Add `https://mypaintingclub.com/kb/mcp` as a Streamable HTTP server.

## Auto-discovery endpoints

| Path | Format |
|---|---|
| `/.well-known/mcp.json` | MCP auto-discovery |
| `/.well-known/ai-plugin.json` | OpenAI plugin manifest |
| `/kb/openapi.json` | OpenAPI spec |
| `/kb/docs` | API docs |
| `/kb/health` | Health check |

## Rate limits

30 requests/minute per IP · 500 queries/day global (resets midnight UTC)

## Tool reference

### `search_painting_lessons`

| Parameter | Type | Required | Default | Description |
|---|---|---|---|---|
| `question` | string | ✓ | — | Natural-language painting technique question |
| `top_k` | integer | | 5 | Max results (1–20) |

**Example:**
```json
{ "question": "how do I paint soft edges in oils", "top_k": 3 }
```

## Links

- [mypaintingclub.com](https://mypaintingclub.com) — the full painting school
- [Smithery listing](https://smithery.ai/servers/mypaintingclub/painting_lessons)
- [/kb/docs](https://mypaintingclub.com/kb/docs) — API documentation
- [support@mypaintingclub.com](mailto:support@mypaintingclub.com)
