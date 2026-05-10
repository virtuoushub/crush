# Crush

Crush is a terminal-based AI coding assistant written in Go and developed by
[Charm](https://charm.sh). It connects to LLMs and gives them tools to read,
write, and execute code, acting like an AI pair programmer in the terminal.

## Key Features

- Multi-provider support: Anthropic, OpenAI, Gemini, AWS Bedrock, GitHub
  Copilot, Vercel, MiniMax, Hyper, and more.
- Built-in coding tools: bash execution, file viewing and editing, grep, glob,
  and LSP-backed code intelligence.
- Extensibility through MCP (Model Context Protocol) servers and a skill
  system.
- Session persistence with SQLite-backed history.
- Project-specific context via files like `AGENTS.md`, `CRUSH.md`,
  `CLAUDE.md`, and `GEMINI.md`.
- A rich terminal UI built with Bubble Tea v2, Lipgloss, and Glamour.

## Architecture Highlights

- `internal/agent/` - Core LLM session agent and coordinator for named agents
  like `coder` and `task`.
- `internal/ui/` - Bubble Tea v2 terminal UI.
- `internal/config/` - Config service, provider config, and model resolution.
- `internal/agent/tools/` - Self-documenting built-in tools.
- `internal/db/` - SQLite persistence via sqlc and migrations.
- `internal/lsp/` - LSP client management for code intelligence.
- `internal/skills/` - Skill discovery and loading.
- `internal/pubsub/` - Internal publish/subscribe messaging.

## Tech Stack

- Language: Go.
- LLM abstraction: `charm.land/fantasy`.
- TUI: `charm.land/bubbletea/v2`.
- Styling: `charm.land/lipgloss/v2` and `charm.land/glamour/v2`.
- Database: SQLite via sqlc.
- Testing: Testify and Catwalk for snapshot testing.

## Build and Run

```sh
go build .
go run .
task test
task lint:fix
```
