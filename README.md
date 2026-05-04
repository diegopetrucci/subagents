# AI agent subagents

Subagents I tend to use with OpenAI Codex.

## Subagents

- [Agent notes maintainer](./agent-notes-maintainer): maintains `.agents/notes.md` when the parent agent decides a repo lesson should be recorded, including duplicate detection, counters, promotion, and stale-note pruning.
- [iOS/macOS test runner](./ios-macos-test-runner): validation-only runner for Apple-platform repos that chooses relevant build/test commands, keeps noisy logs out of the parent thread, and reports concise results.

## Codex custom agent format

Codex custom agents are standalone TOML files. Per the [OpenAI Codex subagents docs](https://developers.openai.com/codex/subagents), each custom agent must define:

- `name`
- `description`
- `developer_instructions`

Optional settings such as `nickname_candidates`, `model`, `model_reasoning_effort`, `sandbox_mode`, `mcp_servers`, and `skills.config` can also be included. If omitted, they inherit from the parent Codex session.

## Installation

Install these as personal Codex agents:

```bash
mkdir -p ~/.codex/agents
cp agent-notes-maintainer/agent_notes_maintainer.toml ~/.codex/agents/
cp ios-macos-test-runner/ios-macos-test-runner.toml ~/.codex/agents/
```

Or install one into a specific project:

```bash
mkdir -p .codex/agents
cp /path/to/subagents/ios-macos-test-runner/ios-macos-test-runner.toml .codex/agents/
```

## Usage

Ask Codex to spawn the custom agent by name, for example:

```text
Spawn agent_notes_mantainer to record this repo lesson: <lesson>
```

```text
Spawn test_runner to validate the current changes and report concise results.
```

These agents currently include some repo-specific assumptions from my own workflows. Treat them as practical examples and adapt the instructions before using them in unrelated repositories.

## License

MIT