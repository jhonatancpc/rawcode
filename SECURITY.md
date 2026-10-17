# Security Policy

Raw Code is a local coding agent that can read files, write files, and run shell commands with user approval. That means security matters by design.

## Supported versions

This project is pre-1.0. Security fixes are expected to land on `main` first.

## Reporting a vulnerability

If you find a security issue, please do **not** open a public issue with exploit details.

Instead, contact the maintainer privately first, then open a minimal tracking issue after a fix is ready.

If you do not have a private contact channel yet, open a GitHub issue that says only:

```text
Potential security issue in <area>. Requesting a private disclosure channel.
```

## Security expectations

- API keys and local settings should stay out of git.
- `run_shell`, `write_file`, and `edit_file` should remain approval-gated by default.
- Tools should stay scoped to the active working directory unless a future design explicitly and safely extends that.
- New tool contributions should include a short explanation of permission behavior and failure modes.

## Current hardening ideas

- Add command-risk classification for shell usage
- Add diff previews before file edits
- Add configurable allow/deny rules by tool and path
- Add test coverage for path traversal and unsafe writes
