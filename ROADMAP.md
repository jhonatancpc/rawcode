# Raw Code Roadmap

This roadmap is intentionally practical: ship a useful .NET-native coding agent in small, reviewable slices.

## Near term

- Streaming model output in the interactive shell
- A richer status/todo panel with better terminal layout
- Safer patch-style editing and diff previews before approval
- Better shell safety checks and command classification
- Built-in `git status` / `git diff` summary commands
- Configurable model/provider switching from the REPL
- Unit/integration tests around the runtime, tools, and permissions

## Medium term

- Local plugin/tool loading model for community extensions
- MCP client support for external tools/resources
- Sub-agent or background task orchestration
- Token/cost usage summaries per session
- Exportable session transcripts
- Better file tree and code search UX

## Long term

- Optional local web UI or TUI frontend
- LSP-aware code navigation and symbol search
- Multi-provider benchmark harness
- A packageable `raw-code` CLI release flow

## Product principles

- Keep C# code readable and contributor-friendly.
- Keep destructive operations approval-gated by default.
- Prefer clean-room implementation and original docs/prompts.
- Make behavior observable: users should see what tool is running and why.
