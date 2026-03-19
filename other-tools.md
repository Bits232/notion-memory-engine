# Connecting Other MCP-Compatible Tools

The Notion Memory Engine is not limited to Claude and VS Code Copilot. Any tool that supports MCP can plug into the same Notion workspace. Here is how to connect the most popular ones.

The core pattern for all tools is the same — Notion now offers a hosted MCP server at `https://mcp.notion.com/mcp` that uses OAuth, so no API tokens are required for most modern tools.

---

## Cursor

1. Open Cursor
2. Go to **Settings** → **Cursor Settings** → **MCP**
3. Click **Add new MCP server**
4. Add this config:

```json
{
  "name": "notion",
  "type": "http",
  "url": "https://mcp.notion.com/mcp"
}
```

5. Complete the OAuth flow when prompted
6. In Cursor's AI chat, switch to **Agent** mode and test with: `What is in my Notion workspace?`

---

## Claude Desktop App

1. Find your Claude config file:
   - Mac: `~/Library/Application Support/Claude/claude_desktop_config.json`
   - Windows: `%APPDATA%\Claude\claude_desktop_config.json`

2. Add the following:

```json
{
  "mcpServers": {
    "notion": {
      "type": "http",
      "url": "https://mcp.notion.com/mcp"
    }
  }
}
```

3. Restart the desktop app and complete the OAuth flow
4. Initialize the memory engine with the same prompt as the web version

---

## Windsurf

1. Open Windsurf
2. Go to **Settings** → **MCP Servers**
3. Add a new HTTP server pointing to `https://mcp.notion.com/mcp`
4. Complete OAuth when prompted
5. Use the Cascade agent panel to interact with Notion

---

## Any Other MCP-Compatible Tool

If the tool supports HTTP-based MCP servers, the config is always:

- **Type:** `http`
- **URL:** `https://mcp.notion.com/mcp`

If the tool requires a local stdio-based server instead of HTTP, you can fall back to running the official Notion MCP server locally with npx:

```json
{
  "command": "npx",
  "args": ["-y", "@notionhq/notion-mcp-server"],
  "env": {
    "OPENAPI_MCP_HEADERS": "{\"Authorization\": \"Bearer YOUR_TOKEN\", \"Notion-Version\": \"2022-06-28\"}"
  }
}
```

For the local/stdio approach you will need a Notion Internal Integration Token from [notion.so/my-integrations](https://www.notion.so/my-integrations).

---

## The Core Principle

No matter which tool you add, they all read from and write to the same Notion database. Every tool you connect makes the memory engine more powerful — the more tools share the same brain, the less context you lose switching between them.
