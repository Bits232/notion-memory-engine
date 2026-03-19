# Notion Setup

No API tokens or integrations needed. Notion MCP uses OAuth — you just connect your account and grant access. Here is everything you need to set up in Notion before connecting any AI tool.

---

## Step 1 — Create Your Pages

In your Notion workspace, create a parent page to hold everything. You can call it anything — for example, **MCP Project Hub**.

Inside that page, create two things:

**1. A Database** — This is your Context Database where all memory entries get saved.

Give it these properties:

| Property Name | Type |
|---|---|
| Title | Title (already exists by default) |
| Category | Text |
| Content | Text |
| Updated At | Date |

Notion automatically adds Created At — no need to add it manually.

**2. A Page** — Title it exactly: **System Prompt**

Leave it blank for now. You will paste the contents of [system-prompt.md](./system-prompt.md) into this page. This is the protocol page that gives Claude its memory behavior.

---

## Step 2 — That's It

You do not need to create any integrations or generate any API tokens. When you connect Claude or VS Code to Notion MCP, it uses OAuth — you just log in to Notion and authorize the connection directly. The AI tools will have access to your workspace automatically.

---

## Tip

Make sure the System Prompt page and your Context Database are not buried inside private pages that are hard to find. Keep them at the top level of your workspace or under one clear parent page so your AI tools can always locate them.
