# Contributing to Raw Code

Thanks for wanting to contribute. This project is intended to be a clean-room .NET coding agent implementation.

## Branch workflow

Do not push directly to `main`.

For your own work:

```powershell
git checkout main
git pull
git checkout -b feature/my-change
```

Make your changes, then:

```powershell
dotnet build .\RawCode.sln
git status
git add .
git commit -m "Add my change"
git push -u origin feature/my-change
```

Then open a Pull Request from `feature/my-change` into `main`.

## For external contributors

External contributors should:

1. Fork the repository on GitHub.
2. Create a branch in their fork.
3. Commit their change.
4. Open a Pull Request from their fork branch into your `main` branch.

They do not need write access to your repo to contribute through PRs.

## What to include in a PR

- A short explanation of the change
- Screenshots or terminal output if the change affects CLI behavior
- Any known limitations
- Confirmation that `dotnet build .\RawCode.sln` succeeds

## Guardrails

- Do not commit API keys, tokens, or local settings files.
- Do not copy source code from proprietary/leaked repositories.
- It is okay to implement similar ideas or architecture in original C# code.
- Keep the tool permission model conservative by default.
- Be kind to first-time contributors and explain requested changes clearly.

## Suggested labels

- `feature`
- `bug`
- `docs`
- `good-first-issue`
- `help-wanted`

## Suggested branch naming

- `feature/<short-name>`
- `fix/<short-name>`
- `docs/<short-name>`

## Good first contributions

- Improve docs or examples
- Add tests for one tool
- Add a small read-only tool
- Improve terminal formatting
- Fix one issue from `ROADMAP.md`
