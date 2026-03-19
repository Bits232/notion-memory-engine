# VS Code Copilot Setup

This guide connects Notion MCP to GitHub Copilot inside VS Code using OAuth — no API tokens needed.

---

## Prerequisites

- VS Code installed
- GitHub Copilot extension installed — free tier works
- A Notion account with your workspace set up (see [notion-setup.md](./notion-setup.md))

---

## Step 1 — Create the MCP Config File

Create a file called `.vscode/mcp.json` inside your workspace folder with this content:

```json
{
  "servers": {
    "notion": {
      "type": "http",
      "url": "https://mcp.notion.com/mcp"
    }
  }
}
```

This tells VS Code to use Notion's official hosted MCP server.

---

## Step 2 — Start the Notion Server

1. Open the Command Palette — `Ctrl+Shift+P` on Windows/Linux or `Cmd+Shift+P` on Mac
2. Search for and run: **MCP: List Servers**
3. Find the Notion server in the list and click **Start**
4. VS Code will prompt you to complete an **OAuth flow** — log in to Notion and authorize the connection
5. Done — VS Code Copilot now has access to your Notion workspace

---

## Step 3 — Configure Across All Workspaces (Optional)

If you want the Notion MCP connection to work in every project, not just one:

1. Open the Command Palette
2. Run: **MCP: Open User Configuration**
3. Add the same server config there:

```json
{
  "servers": {
    "notion": {
      "type": "http",
      "url": "https://mcp.notion.com/mcp"
    }
  }
}
```

---

## Step 4 — Switch Copilot to Agent Mode

Notion MCP tools only work when Copilot is in **Agent mode**.

1. Open the GitHub Copilot chat panel
2. Look for the mode dropdown at the top of the chat
3. Switch from **Ask** to **Agent**

---

## Step 5 — Test the Connection

In Copilot Agent chat, type:

```
What pages do I have in my Notion workspace?
```

Copilot should reach into your Notion workspace and list your pages. If it does, everything is working.

---

## Troubleshooting

| Issue | Fix |
|---|---|
| MCP: List Servers not appearing | Make sure GitHub Copilot extension is up to date |
| OAuth flow not triggering | Restart VS Code and try MCP: List Servers again |
| Copilot does not use Notion | Make sure you are in **Agent** mode, not Ask or Edit |
| Server shows as disconnected | Re-run the OAuth flow via MCP: List Servers |
