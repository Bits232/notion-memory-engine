# 🧠 Notion Memory Engine

> One Notion workspace. Multiple AI tools. Zero context loss.

---

## The Problem

You are deep in a conversation with Claude. Twenty minutes in. You have explained your entire project — the stack, the architecture, the decisions. The advice is flowing. The momentum is real.

And then you need to actually write the code.

You open VS Code. You open GitHub Copilot. And it hits you — Copilot has no idea what you and Claude just talked about. So you start copying and pasting. Grabbing context from one tab, dumping it into another. Summarizing your own conversation just to get a different AI up to speed.

**This is the invisible tax every developer pays when working with multiple AI tools.**

---

## The Solution

The **Notion Memory Engine** turns Notion into a single shared brain for all your AI tools using the **Notion MCP (Model Context Protocol)**.

- Claude reads from it and writes to it  
- VS Code Copilot reads from it and writes to it  
- Any MCP-compatible tool can be plugged in  
- Same database. Same context. Zero copy pasting.

---

## Architecture

```
┌─────────────┐      ┌─────────────────────┐      ┌──────────────────┐
│   Claude    │ ───► │                     │ ◄─── │  VS Code Copilot │
└─────────────┘      │   Notion Database   │      └──────────────────┘
                     │  (Memory Engine)    │
┌─────────────┐      │                     │      ┌──────────────────┐
│   Cursor    │ ───► │  - Title            │ ◄─── │   + Any MCP Tool │
└─────────────┘      │  - Category         │      └──────────────────┘
                     │  - Content          │
                     │  - Updated At       │
                     └─────────────────────┘
```

---

## How It Works

A **System Prompt page** inside Notion gives Claude a set of rules and commands. When you connect Claude to Notion via MCP and initialize it, Claude becomes your memory engine — saving, reading, updating, and searching your knowledge base on command.

VS Code Copilot (and any other MCP-compatible tool) connects to the same Notion database and can read and write entries independently.

**Result: every tool shares the same brain.**

---

## Commands

| Command | What it does |
|---|---|
| `@memory -read [Title]` | Load a specific memory entry into context |
| `@memory -create short` | Save current convo — 3 to 5 bullet points, key decisions only |
| `@memory -create medium` | Save current convo — summary + key code snippets + next steps |
| `@memory -create full` | Save current convo — complete technical documentation |
| `@memory -update` | Append new progress to the most recent entry |
| `@memory -search [keyword]` | Find entries by keyword with previews |

---

## Notion Database Schema

| Property | Type | Purpose |
|---|---|---|
| Title | Title | Unique name of the memory entry |
| Category | Text | Grouping: Python, React, Idea, Bug, DevOps, etc. |
| Content | Text | The actual work: code, decisions, next steps |
| Updated At | Date | Last time this entry was modified |
| Created At | Created Time | Set automatically by Notion |

---

## Setup Guides

1. [Notion Setup](./notion-setup.md) — Create your pages and database  
2. [Claude Setup](./claude-setup.md) — Connect Notion MCP to Claude  
3. [VS Code Copilot Setup](./vscode-setup.md) — Connect Notion MCP to GitHub Copilot  
4. [Other Tools](./other-tools.md) — Add Cursor, Windsurf, Claude Desktop, and more  
5. [System Prompt](./system-prompt.md) — The protocol that powers the engine  

---

## Demo

> Built for the [DEV.to x Notion MCP Challenge](https://dev.to/challenges/notion-2026-03-04)

Watch the full demo video: https://youtu.be/54SRnggzLFE?si=OkdN6538BhUfpIK4

Read the full DEV.to article: https://dev.to/isah_alamin_93d4e4d2ab01f/i-was-tired-of-explaining-my-project-to-every-new-ai-tab-i-opened-3ed7

---

## License

MIT — use it, fork it, extend it.
