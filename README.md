# Vectra Nexus

**Your personal hive mind.**

Plan projects, dispatch tasks to AI agents, and orchestrate distributed nodes — all from a single command surface. Multi-provider LLM backbone with 500+ models.

🌐 **Live:** [roncka.com](https://roncka.com)

---

## What is Vectra Nexus?

Vectra Nexus is an AI-driven project management platform that combines natural language task planning with distributed agent execution. Think of it as a command center where you break down work, assign it to AI agents or human team members, and watch it execute across local and remote nodes.

Built with Next.js, Firebase, and a multi-provider LLM architecture that gives you access to 500+ models from 5+ providers — all with automatic fallback and per-user token management.

## Core Features

### 🗣️ AI Chat Surface
Natural language task planning with streaming responses, voice input (Whisper STT), and voice output (Orpheus TTS). Markdown rendering with GFM support, syntax-highlighted code blocks, and separated tool I/O cards for transparency.

### 🧠 Multi-Provider LLMs
Connect to **5 providers** with 500+ models through a unified interface:

| Provider | Models | Highlights |
|----------|--------|------------|
| **Groq** | Llama 3.3 70B, Llama 3.1 8B, Qwen3 32B, Groq Compound | Ultra-fast inference |
| **Google Gemini** | Gemini 3 Flash | Multimodal, large context |
| **Z.ai (Zhipu)** | GLM-5, GLM-4.7 Flash | Default provider |
| **Mistral** | Magistral Medium, Mistral Medium 3, Mistral Small 3.1, Codestral | Code-optimized models |
| **Kilo Code Gateway** | Claude Sonnet 4.5, Claude Haiku 4.5, GPT-5.2, Kilo Auto + 500 more | Aggregation gateway |

Models are dynamically listed via API with Firestore-cached metadata (24h TTL). Switch providers per-chat or set user-level defaults.

### 🌐 Distributed Nodes
Edge relay nodes (via [Vectra Relay](https://github.com/mroncka/vectra-relay)) execute tasks locally on your infrastructure. Features include:
- Real-time heartbeat monitoring
- Node topology visualization (Brain Graph)
- Task delegation with lifecycle tracking (queued → leased → running → completed)
- Three node types: workflow, cron, service

### 📁 Git-Backed Projects
Every project can sync to a private GitHub repo. Section-based project management with:
- Drag-to-reorder within sections
- Inline rename, delete, icon picker
- Project types (main/side) with visual grouping
- Atomic batch reorder via Firestore `writeBatch`

### 🤖 Agent Personas (Team Tab)
Configure AI team members with:
- Custom system prompts and tool access
- Delivery modes (push-to-main vs. PR + test)
- Per-agent scheduling and task routing
- *Coming soon: Relay-based execution*

### 🔌 Connector Framework
Extensible authentication layer with per-user token resolution:
- **GitHub** — OAuth SSO (issue management, code search, repo sync)
- **Groq / Google / Z.ai / Mistral / Kilo** — Personal Access Tokens
- Token cascade: User connector → Environment variable → Graceful error
- Connected/Available grouping in UI

### 🛠️ GitHub Integration
10 built-in AI tools for GitHub operations:
- List repos, issues, PRs, commits
- Get issue/file details, search code
- Create issues from chat
- System prompt enrichment with repo context

### 🎤 Voice I/O
- **Speech-to-Text:** Whisper Large v3 Turbo (via Groq)
- **Text-to-Speech:** Orpheus v1 English, "autumn" voice (via Groq)

### 📊 Data Table
Reusable sortable data table component with:
- Click-to-sort columns (asc → desc → off)
- Text search across all fields
- Export: copy as aligned text, CSV download, JSON download
- Pagination with configurable page size

## Tech Stack

| Layer | Technology |
|-------|-----------|
| **Framework** | Next.js 16.1.6 (App Router, Turbopack) |
| **UI** | Tailwind CSS, shadcn/ui, Radix primitives |
| **Auth** | Firebase Authentication |
| **Database** | Firestore (documents) + Firebase RTDB (real-time) |
| **Hosting** | Firebase App Hosting |
| **AI** | Groq SDK, Google GenAI, Z.ai, Mistral (OpenAI-compat), Kilo Gateway |
| **Visualization** | React Flow (brain graph), Recharts |
| **Package Manager** | pnpm |

## Architecture

```
┌─────────────────────────────────────────────────┐
│                   roncka.com                     │
│              (Firebase App Hosting)              │
├─────────────────────────────────────────────────┤
│  Next.js App Router                             │
│  ├── /           Landing page                   │
│  ├── /dashboard  NexusShell (protected)         │
│  ├── /api/chat   Multi-provider LLM endpoint    │
│  ├── /api/models Dynamic model listing          │
│  ├── /api/sync/* Git sync endpoints             │
│  └── /api/nodes  RTDB node registry             │
├─────────────────────────────────────────────────┤
│  Firestore         │  Firebase RTDB             │
│  ├── users/        │  ├── tasks/                │
│  ├── projects/     │  ├── nodeHeartbeats/       │
│  ├── connectors/   │  └── globalRequests/       │
│  └── model_cache/  │                            │
├─────────────────────────────────────────────────┤
│  Vectra Relay (Edge)                            │
│  ├── Nanobot agent nodes                        │
│  ├── Git-backed workspaces                      │
│  └── Task execution + lifecycle                 │
└─────────────────────────────────────────────────┘
```

## Ecosystem

| Package | Description | Status |
|---------|-------------|--------|
| **[Vectra Nexus](https://roncka.com)** | AI command surface + project management | 🟢 Live |
| **[Vectra Relay](https://github.com/mroncka/vectra-relay)** | Edge process supervisor for agent nodes | 🟡 In Development |

## Screenshots

*Coming soon — the app is live at [roncka.com](https://roncka.com), sign up to explore.*

---

## Roadmap

See [ROADMAP.md](./ROADMAP.md) for the full feature roadmap and upcoming work.

## License

MIT — see [LICENSE](./LICENSE) for details.

## Links

- 🌐 **Live App:** [roncka.com](https://roncka.com)
- 📦 **Source (private):** [github.com/mroncka/vectra-nexus](https://github.com/mroncka/vectra-nexus)
- 🔗 **Relay:** [github.com/mroncka/vectra-relay](https://github.com/mroncka/vectra-relay)
