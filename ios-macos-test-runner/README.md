# iOS/macOS test runner

Validation-only Codex subagent for Apple-platform repositories.

## Agent file

- [`ios-macos-test-runner.toml`](./ios-macos-test-runner.toml)
- Codex name: `test_runner`

## What it does

- Reads repo guidance before choosing validation commands.
- Inspects the changed files or parent-provided context to choose relevant package, scheme, or target validation.
- Runs build/test commands without editing source, test, project, or documentation files.
- Keeps noisy raw logs inside the subagent context.
- Reports a concise status, commands run, fallbacks used, first actionable failure, and unexpected file changes.

## Install

```bash
mkdir -p ~/.codex/agents
cp ios-macos-test-runner.toml ~/.codex/agents/
```

## Example prompt

```text
Spawn test_runner to validate the current changes and report concise results.
```

This agent is based on my SendItToMy workflow and expects tools such as `rtk`, `.scripts/xcodebuild-safe.sh`, and `xcsift`. Adapt those repository rules before using it elsewhere.
