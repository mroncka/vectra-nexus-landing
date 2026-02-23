# Vectra Nexus — Feature Guide

Detailed documentation of all current features in Vectra Nexus.

## AI Chat

The primary interface is a chat surface where you interact with AI models using natural language.

### Capabilities
- **Streaming responses** — Real-time token-by-token output
- **Markdown rendering** — GitHub Flavored Markdown with tables, lists, code blocks
- **Syntax highlighting** — Automatic language detection with copy-to-clipboard
- **Tool calling** — AI can invoke GitHub tools, search code, manage issues
- **Tool transparency** — Separate cards show tool inputs and outputs
- **Voice input** — Click to record, transcribed via Whisper Large v3 Turbo
- **Voice output** — AI responses read aloud via Orpheus TTS ("autumn" voice)
- **Stop streaming** — Cancel generation mid-response
- **Message queue** — Messages queue if AI is still responding

### Models

Choose from 500+ models across 5 providers. Each provider connects via Personal Access Token (PAT) or OAuth:

**Groq** (fast inference)
- Llama 3.3 70B Versatile
- Llama 3.1 8B Instant
- Groq Compound (multi-model reasoning)
- Qwen3 32B

**Google Gemini** (multimodal)
- Gemini 3 Flash

**Z.ai / Zhipu** (default provider)
- GLM-5
- GLM-4.7 Flash

**Mistral** (code-optimized)
- Magistral Medium
- Mistral Medium 3
- Mistral Small 3.1
- Codestral

**Kilo Code Gateway** (aggregation — 500+ models)
- Claude Sonnet 4.5
- Claude Haiku 4.5
- GPT-5.2
- Kilo Auto (automatic model selection)
- + hundreds more via OpenAI-compatible API

## Project Management

### Projects
- Create projects with name, icon, description
- Organize into sections (main / side)
- Drag-to-reorder within sections
- Inline rename and delete
- Icon picker with curated set

### Tasks
- Nested under projects in Firestore
- Status tracking with lifecycle management
- Assignable to team members or AI agents
- Delivery mode configuration (push-to-main vs. PR)

### Team Members
- Add AI agent team members per project
- Configure system prompts and available tools
- Set delivery mode preferences
- Schedule-based task routing (planned)

### Git Sync
- Link any project to a private GitHub repo
- One-click sync pushes project state
- Backup submodule system (`nexus-backup`)
- Configured per-project in settings

## Connectors

Per-user authentication management:

| Connector | Auth Type | Scope |
|-----------|-----------|-------|
| GitHub | OAuth SSO | Repos, issues, PRs, code |
| Groq | PAT | Model inference |
| Google Gemini | PAT | Model inference |
| Z.ai (Zhipu) | PAT | Model inference |
| Mistral | PAT | Model inference |
| Kilo Gateway | PAT | 500+ model access |

**Token Resolution Order:**
1. Per-user Firestore connector token
2. Environment variable fallback
3. Graceful error with provider-specific hint

## GitHub Integration

### 10 Built-in AI Tools
1. `github_list_repos` — List user's repositories
2. `github_list_issues` — List issues (with state/label filters)
3. `github_get_issue` — Full issue details + comments
4. `github_create_issue` — Create new issue with labels
5. `github_list_pulls` — List pull requests
6. `github_list_commits` — Recent commits with filters
7. `github_search_code` — Search code across repo
8. `github_get_file` — Read file contents
9. `github_create_comment` — Comment on issues
10. `github_close_issue` — Close/reopen issues

### System Prompt Enrichment
When a GitHub connector is active, the AI automatically knows about:
- Open issue and PR counts
- Recent commit summaries
- Issues assigned to you

## Brain Graph

Visual topology of connected nodes and their relationships:
- React Flow-based interactive graph
- Dagre layout for automatic positioning
- Real-time node status via RTDB heartbeats
- Expandable node details

## Data Table

Reusable component for structured data display:
- **Sort** — Click column headers to cycle asc → desc → off
- **Search** — Full-text search across all fields
- **Export** — Copy as aligned text, download CSV, download JSON
- **Paginate** — Configurable rows per page
- Zero external dependencies (built on shadcn primitives)

## Providers & Models Tab

Dedicated UI panel for managing LLM providers:
- Provider cards with connection status
- Model preview with capabilities
- Dynamic model listing from API
- Refresh button to update cached models
