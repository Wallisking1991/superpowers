---
name: update-brainstorm-server-implementation
description: Workflow command scaffold for update-brainstorm-server-implementation in superpowers.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /update-brainstorm-server-implementation

Use this workflow when working on **update-brainstorm-server-implementation** in `superpowers`.

## Goal

Implement or refactor brainstorm server logic, scripts, and related tests.

## Common Files

- `skills/brainstorming/scripts/server.cjs`
- `skills/brainstorming/scripts/server.js`
- `skills/brainstorming/scripts/start-server.sh`
- `skills/brainstorming/scripts/stop-server.sh`
- `skills/brainstorming/visual-companion.md`
- `tests/brainstorm-server/server.test.js`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit skills/brainstorming/scripts/server.cjs or server.js
- Edit skills/brainstorming/scripts/start-server.sh and/or stop-server.sh
- Edit skills/brainstorming/visual-companion.md (sometimes)
- Update or fix related tests in tests/brainstorm-server/
- Update RELEASE-NOTES.md to describe changes

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.