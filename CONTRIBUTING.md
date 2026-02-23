# Contributing to Vectra Nexus

Thanks for your interest in contributing! Vectra Nexus is actively developed and we welcome community input.

## Getting Started

1. Check the [Roadmap](./ROADMAP.md) for planned features
2. Look at open issues on [GitHub](https://github.com/mroncka/vectra-nexus/issues)
3. Join the discussion on any issue before starting work

## Development Setup

Vectra Nexus is a Next.js application with Firebase backend:

```bash
# Clone the repo
git clone https://github.com/mroncka/vectra-nexus.git
cd vectra-nexus

# Install dependencies
pnpm install

# Set up environment variables
cp .env.example .env.local
# Fill in your Firebase config and API keys

# Start development server
pnpm dev
```

### Prerequisites
- Node.js 18+
- pnpm
- Firebase project with Firestore + RTDB + Auth enabled
- At least one LLM provider API key (Groq recommended for free tier)

## Tech Stack

- **Next.js 16** (App Router, Turbopack)
- **TypeScript** (strict mode)
- **Tailwind CSS** + shadcn/ui
- **Firebase** (Auth, Firestore, RTDB, App Hosting)
- **pnpm** (package manager)

## Code Style

- Atomic commits to `main` with clear messages
- `feat:`, `fix:`, `chore:` conventional commit prefixes
- ESLint + lint-staged via Husky
- TypeScript strict mode — no `any` types

## Submitting Changes

1. Fork the repository
2. Create a feature branch (`feat/your-feature`)
3. Make your changes with atomic commits
4. Run `pnpm lint` and `pnpm typecheck`
5. Open a PR against `main`

## Issue Labels

| Label | Description |
|-------|-------------|
| `enhancement` | New feature or improvement |
| `bug` | Something isn't working |
| `good first issue` | Suitable for newcomers |
| `help wanted` | Looking for contributors |

## Questions?

Open an issue or reach out via GitHub discussions.
