# Vectra Nexus — Roadmap

This document tracks upcoming features, current development priorities, and the longer-term vision for Vectra Nexus.

> Last updated: February 2026

## 🚧 In Progress

### Save Project Chat History ([#14](https://github.com/mroncka/vectra-nexus/issues/14))
Persist chat conversations per project so context is retained across sessions.
- Store chat messages in Firestore under each project
- Load previous conversation when switching back to a project
- Message pagination for long conversations

### GitHub Context in System Prompt ([#3](https://github.com/mroncka/vectra-nexus/issues/3))
Automatically inject relevant GitHub context into the AI system prompt:
- Open issue/PR counts, recent commits
- Issues assigned to the user
- Graceful degradation when no GitHub token is configured
- Target: under 500 tokens of context

### GitHub Actions from Chat ([#4](https://github.com/mroncka/vectra-nexus/issues/4))
Enable the LLM to take GitHub actions directly from the chat interface:
- Create issues with title, body, labels
- Comment on existing issues
- Close/reopen issues
- PR summary and review
- Confirmation required for destructive actions

### GitHub Data Sync ([#6](https://github.com/mroncka/vectra-nexus/issues/6))
Link a GitHub repo to a Vectra project with bidirectional awareness:
- Issues sync as tasks (GitHub → Vectra, one-way)
- Labels map to tags, assignees to agents
- Activity feed: recent commits, PR merges
- Repo link configuration in project settings

## 📋 Planned

### Context Components Visualization ([#11](https://github.com/mroncka/vectra-nexus/issues/11))
Visualize what context is assembled and sent to the LLM:
- Show included components (system prompt, project data, connectors, tools)
- Token usage breakdown per component
- Helps users understand what the model "sees"

### Preview Chat Context ([#13](https://github.com/mroncka/vectra-nexus/issues/13))
Show a read-only preview of the full assembled context:
- Expandable panel/modal with raw context
- Includes system prompt, conversation history, tool definitions, injected context
- Debugging and transparency tool

### Compact Chat Context ([#12](https://github.com/mroncka/vectra-nexus/issues/12))
Allow users to compress chat context to fit more into the model's context window:
- Toggle/button to compact context
- Configurable aggressiveness (light trim vs. heavy summarization)
- Show token savings from compaction

### GitHub AI Tools Expansion ([#5](https://github.com/mroncka/vectra-nexus/issues/5))
Extend the existing 10 GitHub AI tools with additional capabilities:
- `github_search_code` — search code in a repo
- `github_get_file` — read file contents
- Enhanced tool result formatting for LLM context windows
- Cross-provider compatibility (Groq, Google, Z.ai, Mistral, Kilo)

## 🔮 Future Vision

### Relay Execution Layer
- Team members execute tasks via Vectra Relay nodes
- Agent-to-node routing based on capabilities
- Distributed task queuing with priority lanes

### Multi-User Collaboration
- Shared projects with role-based access
- Real-time presence indicators
- Comment threads on tasks and chat messages

### Plugin / Skills System
- User-installable skill packs
- Custom tool definitions per project
- Marketplace for community-built connectors

### Advanced Orchestration
- Multi-step task chains with conditional branching
- Parallel execution across multiple agents
- Automated retry with fallback strategies

### Analytics Dashboard
- Token usage tracking per provider/model
- Task completion metrics and agent performance
- Cost estimation and optimization suggestions

---

## ✅ Recently Shipped

*Shipped in the last 48 hours (Feb 22-23, 2026):*

- **Markdown rendering in chat** — GFM, syntax highlighting, copy button on code blocks
- **Separated tool I/O cards** — Visual distinction between tool calls and tool results
- **DataTable skill** — Sortable, searchable, exportable data tables
- **Section-based project management** — Main/side project types with grouped layout
- **Dynamic model listing** — API-driven model discovery with 24h Firestore cache
- **Kilo Code Gateway** — Access to 500+ models via single endpoint
- **Mistral AI provider** — 4 models including Codestral
- **Landing page** — Product page at roncka.com with route restructure
- **Code review hardening** — Error handling, security fixes, race condition guards
- **Team tab** — AI team member management with delivery configuration
- **Git sync** — Per-project private repos with backup submodules
- **GitHub integration** — OAuth connector, 10 AI tools, system prompt enrichment
- **Voice I/O** — Whisper STT + Orpheus TTS
- **Connector framework** — Per-user token management with cascade resolution
