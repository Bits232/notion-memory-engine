# Claude Setup

This guide connects Notion MCP to Claude on claude.ai using OAuth — no tokens or API keys needed.

---

## Prerequisites

- Notion workspace set up with your database and System Prompt page (see [notion-setup.md](./notion-setup.md))
- A Claude account at [claude.ai](https://claude.ai) — free tier works

---

## Step 1 — Connect Notion MCP to Claude

1. Go to [claude.ai](https://claude.ai) and log in
2. Click your **profile icon** (bottom left)
3. Go to **Settings**
4. Click **Integrations**
5. Find **Notion** and click **Connect**
6. You will be redirected to Notion — log in and click **Allow Access**
7. Select the workspace where your database lives
8. Done — Claude now has full access to your Notion workspace

---

## Step 2 — Initialize the Memory Engine

Start a new Claude conversation and paste this exact message:

```
Please read my Notion page titled "System Prompt" and follow the protocol.
```

Claude will search your Notion workspace, find the System Prompt page, read the full protocol, and respond with the initialization handshake:

```
🧠 Memory Engine Online
Ready for @memory commands.
```

This confirms everything is connected and working. You are ready.

---

## Step 3 — Test It

Try your first memory command:

```
@memory -search test
```

If Claude searches your Notion database and returns results (or confirms no matches found), the connection is working perfectly.

---

## Notes

- Paste the initialization message **once at the start of each new conversation**
- Claude stays in **passive mode** — it will not touch Notion unless you use an `@memory` command
- You are always in full control of what gets saved
