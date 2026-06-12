<!-- GitHub Profile README — adeoluwaadesina -->

<div align="center">

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│   building infrastructure for long-running AI conversations │
│                                                             │
│   MCP servers · local-first · open source                  │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

# Adeoluwa Adesina

**AI Engineer · MCP Builder · Lagos, Nigeria**

[![wingman-mcp](https://img.shields.io/pypi/v/wingman-mcp?color=0a84ff&label=wingman-mcp&style=flat-square)](https://pypi.org/project/wingman-mcp/)
[![PyPI downloads](https://img.shields.io/pypi/dm/wingman-mcp?color=0a84ff&label=installs%2Fmo&style=flat-square)](https://pypi.org/project/wingman-mcp/)
[![License: MIT](https://img.shields.io/badge/license-MIT-34c759?style=flat-square)](https://github.com/adeoluwaadesina/wingman-mcp/blob/main/LICENSE)

</div>

---

I build **MCP servers** — open-source infrastructure that extends what Claude can do inside long, complex conversations.

My current focus: making AI-assisted work feel less like chatting and more like having a capable collaborator who tracks state, holds context, and takes action alongside you.

---

## Shipped

### [Wingman MCP](https://github.com/adeoluwaadesina/wingman-mcp) — `pip install wingman-mcp`

> *Sits beside you. Doesn't fly the plane.*

Gives Claude conversations a **persistent, interactive plan panel** rendered inline in the chat via MCP Apps (SEP-1865). Plans live in local SQLite. You tick checkboxes from the panel; Claude ticks tasks after completing work. State syncs live. Works in Claude Desktop and MCPJam.

```
┌──────────────────────────────────────────────────┐
│  Claude Desktop / Cursor / MCPJam                │
│                                                  │
│  ┌──────────────┐   ┌──────────────────────────┐ │
│  │  Claude LLM  │──▶│  Wingman MCP Server      │ │
│  └──────────────┘   │  12 tools · SQLite store │ │
│         ▲           └──────────────────────────┘ │
│  sendMessage()                   │               │
│         │              JSON-RPC postMessage       │
│  ┌──────────────┐                │               │
│  │  Plan Panel  │◀───────────────┘               │
│  │  (iframe)    │                                │
│  └──────────────┘                                │
└──────────────────────────────────────────────────┘
```

**Two discoveries along the way** that aren't documented anywhere else in the MCP ecosystem:

- **`resourceUri` dual-interpretation bug** — a registration-level `resourceUri` in tool metadata is interpreted by Claude Desktop as a "hide from model" signal, silently dropping the tool from `tools/list`. Fix: return `CallToolResult` directly with `_meta` at the top level.
- **FastMCP `structuredContent` meta-burial bug** — returning a plain dict with `_meta` nested inside causes FastMCP to serialize it into `structuredContent`, burying the resource pointer from the host. Fix: return `CallToolResult` directly.

---

### [Genesis MCP](https://github.com/adeoluwaadesina/genesis-mcp)

MCP server scaffolding and tooling. Shipped before Wingman; part of the same infrastructure thesis.

---

## Stack

```
Python · FastMCP · SQLite · MCP Apps (SEP-1865)
HTML / CSS / JS (vanilla) · Sortable.js
platformdirs · Pydantic · pytest
```

---

## Stats

<div align="center">

<img height="180em" src="https://github-readme-stats.vercel.app/api?username=adeoluwaadesina&show_icons=true&theme=github_dark&include_all_commits=true&count_private=true&hide_border=true&title_color=0a84ff&icon_color=0a84ff&text_color=ffffff&bg_color=0d1117"/>
<img height="180em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=adeoluwaadesina&layout=compact&theme=github_dark&hide_border=true&title_color=0a84ff&text_color=ffffff&bg_color=0d1117&langs_count=6"/>

</div>

<div align="center">

<img src="https://streak-stats.demolab.com?user=adeoluwaadesina&theme=github-dark-blue&hide_border=true&stroke=0a84ff&ring=0a84ff&fire=34c759&currStreakLabel=0a84ff&background=0d1117"/>

</div>

<div align="center">

[![trophy](https://github-profile-trophy.vercel.app/?username=adeoluwaadesina&theme=darkhub&no-frame=true&column=6&margin-w=8&title_color=0a84ff)](https://github.com/ryo-ma/github-profile-trophy)

</div>

---

## What I'm working on

- **Wingman v0.3** — server-pushed updates via MCP notifications (replacing 2.5s polling)
- **Wingman Cloud** — HTTP/SSE transport, OAuth 2.1, Postgres, Fly.io · unlocks mobile Claude support

---

<div align="center">

`No telemetry. No phone-home. Local-first by default.`

</div>
