---
name: release-version-bump
description: Workflow command scaffold for release-version-bump in superpowers.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /release-version-bump

Use this workflow when working on **release-version-bump** in `superpowers`.

## Goal

Prepare and publish a new release version, updating plugin manifests, release notes, and package files.

## Common Files

- `.claude-plugin/marketplace.json`
- `.claude-plugin/plugin.json`
- `.cursor-plugin/plugin.json`
- `package.json`
- `RELEASE-NOTES.md`
- `.version-bump.json`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Update .claude-plugin/marketplace.json
- Update .claude-plugin/plugin.json
- Update .cursor-plugin/plugin.json (sometimes)
- Update package.json
- Update RELEASE-NOTES.md

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.