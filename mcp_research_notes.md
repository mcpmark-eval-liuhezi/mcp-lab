# MCP Research Notes — Team Briefing (Monday Team Sync)

Research backing the mcp_briefing.pptx deck. Leadership question: is MCP worth adopting for our internal tooling?

---

## 1. Official definition — from the MCP project's own documentation

Source: https://modelcontextprotocol.io (What is the Model Context Protocol (MCP)? — docs revision 2026-07-28)
Direct link: https://modelcontextprotocol.io/docs/2026-07-28/getting-started/intro.md

> "MCP (Model Context Protocol) is an open-source standard for connecting AI applications to external systems. Using MCP, AI applications like Claude or ChatGPT can connect to data sources (e.g. local files, databases), tools (e.g. search engines, calculators) and workflows (e.g. specialized prompts)—enabling them to access key information and perform tasks."

> "Think of MCP like a USB-C port for AI applications. Just as USB-C provides a standardized way to connect electronic devices, MCP provides a standardized way to connect AI applications to external systems."

Other points from the same page:
- Broad ecosystem support: "MCP is an open protocol supported across a wide range of clients and servers. AI assistants like Claude and ChatGPT, development tools like Visual Studio Code, Cursor, MCPJam, and many others all support MCP — making it easy to build once and integrate everywhere."
- For developers: "MCP reduces development time and complexity when building, or integrating with, an AI application or agent."

## 2. Video metadata — "MCP In 26 Minutes (Model Context Protocol)"

- **Title:** MCP In 26 Minutes (Model Context Protocol)
- **Channel:** Tina Huang (https://www.youtube.com/@TinaHuang1 — channel ID UC2UXDak6o7rBm23k3Vv5dww, ~1.36M subscribers)
- **Published:** 2025-10-15 (2025-10-15T14:38:05Z)
- **Duration:** 26 minutes 23 seconds (PT26M23S / 26:23)
- **View count:** 265,662 (live check at time of research); ~7.1K likes
- **URL:** https://www.youtube.com/watch?v=kOhLoixrJXo
- Companion code repo (creator's): https://github.com/hellotinah/MCP (Google Sheets & Forms MCP server — the build example from the final section of the video)

## 3. Transcript highlights — what the video actually says

Chapter structure (from the video's own timestamps):
1. Intro (00:00)
2. Video overview (00:44)
3. MCP definition (01:06)
4. Fundamentals of MCP (04:38)
5. Tools, Resources, Prompt Templates (07:54)
6. Communication Life Cycle (12:18)
7. Building an MCP Server — no-code (15:47)
8. Building an MCP Server — with code (20:42)

### Key points, in the order the video presents them

- **Intro:** The presenter has built MCP servers and clients for her team and for B2B clients, and teaches an MCP section in her AI agents bootcamp. The video's promise: explain the fundamentals of MCP, show how to use MCP servers, and how to build your own MCP servers — both with code and no-code. Four short assessments/quizzes are sprinkled through the video to check understanding.
- **Overview:** The stated structure is (1) define MCP and why it's important and how it's used; (2) go under the hood into the fundamentals — "the concepts and frameworks that govern it... basically everything you need to know to be able to use and build your own servers"; (3) build one, both with code and no-code.
- **MCP definition:** MCP = Model Context Protocol, created by Anthropic. Anthropic's definition, quoted in the video: an **open protocol** that standardizes how your LLM applications connect to and work with your tools and data sources. USB analogy: MCP is like a USB plug — a universal standard that lets any device connect to any other device. Before USB, hooking a computer up to a microphone or webcam meant a mess of different ports, special cords, and adapters — and you'd still have to write the software to support each device.
- **Fundamentals:** the "under the hood" section covering concepts, frameworks, and architecture needed to use and build MCP servers.
- **Tools, Resources, Prompt Templates — the three primitives an MCP server exposes.** Concretely, in the video's companion repo (a Google Sheets & Forms MCP server):
  - Tools: list_spreadsheets, read_sheet, write_sheet, append_sheet, create_spreadsheet, create_form
  - Resources: sheet://{spreadsheet_id}/{range_name} URIs
  - Prompt templates: analyze_sheet_data, create_report_template, form_to_sheet
- **Communication life cycle:** how the components of an MCP setup communicate over the course of a session, over JSON-RPC with two transport options — stdio for local subprocess servers and HTTP/SSE for remote servers.
- **Building an MCP server, no-code:** walkthrough of building a server without writing code.
- **Building an MCP server, with code:** the companion repo is the finished example — a Google Sheets & Forms MCP server:
  - Python server (gsheets_server.py) run in a virtualenv with requirements.txt
  - Google Cloud Console setup: enable the Sheets / Forms / Drive APIs, create an OAuth client ID, save credentials.json; on first run a browser window opens for Google auth and token.pickle stores the token
  - Test with MCP Inspector: npx @modelcontextprotocol/inspector python gsheets_server.py
  - Register in Claude Desktop via claude_desktop_config.json — an mcpServers entry with command, args, and env
  - Then ask Claude things like "List my spreadsheets", "Read the data from spreadsheet ID 'abc123' in range 'Sheet1!A1:C10'", "Use the analyze_sheet_data prompt"

### Opening line of the video (transcript)

> "I learned MCP for you. In the past 68 months, you've probably heard a lot of people talk about MCP. MCP is so amazing. MCP is such a game changer."

### Course structure

The video is structured as a teach-then-verify course, with quiz checkpoints after each major section (definition, fundamentals, life cycle, and the two build walkthroughs).

### The Anthropic MCP course referenced in the video

https://www.deeplearning.ai/short-courses/mcp-build-rich-context-ai-apps-with-anthropic/

---

## Sources

- MCP official documentation (source of truth for the definition): https://modelcontextprotocol.io
- "MCP In 26 Minutes (Model Context Protocol)" — Tina Huang: https://www.youtube.com/watch?v=kOhLoixrJXo
- Creator's companion code repo: https://github.com/hellotinah/MCP
