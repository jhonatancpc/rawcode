# Raw Code

Raw Code is a clean-room **.NET coding agent** built for developers who want a transparent, hackable, terminal-first AI pair programmer in C#.

> Agentic coding, but in .NET. Local-first workflow, approval-gated tools, session memory, and provider adapters you can actually read and extend.

**Not affiliated with Anthropic, OpenAI, or Microsoft.**

## Why Raw Code?

Most coding-agent projects live in Python, TypeScript, or Rust. Raw Code is an experiment in building that experience in **idiomatic C#/.NET** so .NET developers can understand, modify, and extend the whole stack without leaving their ecosystem.

## What it can do today

- Interactive terminal REPL with slash commands
- Azure OpenAI and Anthropic provider adapters
- Runtime loop with tool calling and session persistence
- Approval-gated `edit_file`, `write_file`, and `run_shell`
- Auto-approved read/discovery tools like `read_file`, `list_files`, `search_text`
- Session todo tracking with `/todos`
- Tool catalog with `/tools`
- Live status events while the agent thinks and runs tools

## Solution shape

- `src/RawCode.App` - console host and dependency injection setup
- `src/RawCode.Core` - agent loop, contracts, and core models
- `src/RawCode.Infrastructure` - permissions, tool execution, and session persistence
- `src/RawCode.Providers.Anthropic` - Azure OpenAI and Anthropic model-provider adapters
- `tests/RawCode.Core.Tests` - room for unit tests around the runtime and policies

## Architectural flow

```text
User Prompt
   |
   v
RawCode.App
   |
   v
AgentRuntime
   |----> SessionStore
   |----> LlmClient
   |----> ToolExecutor
   |----> PermissionService
   |
   v
Console Output
```

## Getting started

From the repo root:

```powershell
dotnet build .\RawCode.sln
dotnet run --project .\src\RawCode.App
```

You should see a `Raw Code` splash screen and then:

```text
[default @ raw-code] raw-code>
```

If no provider credentials are configured yet, Raw Code starts a first-run setup wizard and saves local settings to:

```text
%LocalAppData%\RawCode\settings.json
```

That file is outside the repo so you do not commit secrets by accident.

You can also inspect the safe template here:

```text
src/RawCode.App/appsettings.example.json
```

## Useful interactive commands

```text
/doctor
/tools
/todos
/show-session
/session my-session
/cd C:\path\to\repo
/exit
```

Example prompt:

```text
Inspect this repository, create a todo list, then explain the architecture.
```

## How the loop works

1. Read a prompt from the CLI.
2. Load a session from disk.
3. Ask the configured model provider for the next step.
4. If the model requests a tool, validate permission and execute it.
5. Feed the tool result back into the loop.
6. Print the final assistant message.

## Security note

`read_file`, `list_files`, `search_text`, `todo_read`, and `todo_write` run automatically.
`write_file`, `edit_file`, and `run_shell` require explicit user approval.

Do not commit API keys to the repo. Prefer the first-run setup wizard, environment variables, or a local-only settings file.

## Contributing

See `CONTRIBUTING.md`.

## Roadmap

See `ROADMAP.md`.

## Responsible disclosure

See `SECURITY.md`.
