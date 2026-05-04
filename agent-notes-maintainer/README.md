# Agent notes maintainer

Maintains `.agents/notes.md` when the parent agent decides a repo lesson should be recorded.

## Agent file

- [`agent_notes_maintainer.toml`](./agent_notes_maintainer.toml)
- Codex name: `notes_maintainer`

## What it does

- Reads repo guidance before editing notes.
- Detects semantically duplicate notes and increments their leading counter.
- Appends new `[0]` notes when the lesson is not already present.
- Promotes notes with count `3` or higher into `AGENTS.md`.
- Prunes stale count-`0` notes older than one month.
- Restricts edits to `.agents/notes.md` and, when promotion is required, `AGENTS.md`.

## Install

```bash
mkdir -p ~/.codex/agents
cp agent_notes_maintainer.toml ~/.codex/agents/
```

## Example prompt

```text
Spawn notes_maintainer to record this repo lesson: <lesson>
```

This agent is based on my SendItToMy workflow, so adapt the repository rules before using it elsewhere.
