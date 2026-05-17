# Lutains Skills Marketplace 🏪

```text
  _          _        _
 | |   _   _| |_ __ _(_)_ __  ___
 | |  | | | | __/ _` | | '_ \/ __|
 | |__| |_| | || (_| | | | | \__ \
 |_____\__,_|\__\__,_|_|_| |_|___/
```

Welcome to the **Lutains Skills Marketplace**!

Lutains is an AI-powered platform that optimizes landing pages using real customer feedback. We connect you with virtual customer personas built from real Reddit data. They criticize your copy using their exact vernacular, pain points, and expectations — so you write landing pages that actually convert.

This repository hosts the official AI skills and workflows used by Lutains to interact with our agents via the MCP (Model Context Protocol) server.

## 🌟 Core Concepts

- **Personas (Agents)**: AI agents meticulously crafted from real Reddit data. They come with specific pain points, emotions (e.g., ANGER 😡, FRUSTRATION 😤), and vernacular.
- **Tim (System Agent)**: Our ruthless, data-driven virtual CRO (Conversion Rate Optimization) expert. Tim orchestrates landing page audits and synthesis.
- **Context-Aware**: Agents already know your project. You never have to copy-paste your landing page URL or content.

---

## 📦 Available Skills

Here are the official skills available in the Lutains ecosystem:

### 1. `default` (Initialization & Routing)

The entry point of the Lutains experience.

- Automatically displays the user's projects and associated personas.
- Presents the **Project Action Menu** (Full Audit, Direct Chat, Update Persona).
- Handles global formatting (Markdown tables, Pain Point intensity flames 🔥🔥🔥⚫⚫).

### 2. `copy` (CRO & Copywriting Mastery)

The core engine for landing page optimization. It handles three distinct workflows:

- **Workflow A (Full Audit)**: Tim takes the wheel, analyzes your page, tests specific hypotheses with your personas, and delivers a final actionable report.
- **Workflow B (Direct Chat)**: Co-create directly with a Reddit persona. Test your hooks, friction points, and value propositions in a 1-on-1 chat.
- **Workflow C (Consulting)**: Chat directly with Tim for high-level CRO strategy without immediate persona feedback.

---

## 🛠️ Architecture & MCP Tools

All skills in this marketplace communicate with the Lutains backend via our custom **MCP Server**.

The skills utilize the following tools:

- `get_agents`: Fetches the user's projects, available personas, and their active pain points.
- `update_agents`: Modifies the targeted pain point for a specific persona to test different angles.
- `chat_with_agent`: The core interaction tool. Routes messages to either Tim or a specific Reddit persona and maintains session history.

## 🚀 Getting Started

_(Add your specific installation or usage instructions here. For example:)_

1. Connect your AI assistant to the Lutains MCP Server.
2. Load the `default` skill to initialize your session.
3. Select a project and let Tim or your personas guide you!

---

_Built with ❤️ by the Lutains Team. Stop guessing. Start converting._
