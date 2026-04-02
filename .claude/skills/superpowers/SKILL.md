```markdown
# superpowers Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you how to contribute to the `superpowers` JavaScript codebase. You'll learn the project's coding conventions, commit patterns, and the main workflows for releasing versions, updating server logic, refining review loops, maintaining contributor guidelines, and documenting Codex/OpenCode compatibility. This guide is ideal for new contributors or anyone aiming to maintain consistency and quality in the repository.

## Coding Conventions

- **File Naming:**  
  Use `kebab-case` for all file and directory names.  
  _Example:_  
  ```
  skills/brainstorming/scripts/start-server.sh
  docs/superpowers/specs/2026-03-23-codex-app-compatibility-design.md
  ```

- **Import Style:**  
  Use alias imports where appropriate.  
  _Example:_  
  ```js
  import { brainstorm } from '@skills/brainstorming/scripts/server.js';
  ```

- **Export Style:**  
  Use named exports for all modules.  
  _Example:_  
  ```js
  // In skills/brainstorming/scripts/server.js
  export function startServer() { ... }
  export function stopServer() { ... }
  ```

- **Commit Messages:**  
  - Prefix with `fix:`, `docs:`, `feat:`, or `chore:`
  - Keep messages concise (average ~58 characters)
  _Examples:_  
  ```
  feat: add Codex compatibility docs
  fix: resolve brainstorm server crash on shutdown
  docs: update contributor guidelines
  ```

## Workflows

### Release Version Bump
**Trigger:** When a new version of the project is ready to be released.  
**Command:** `/release`

1. Update `.claude-plugin/marketplace.json`
2. Update `.claude-plugin/plugin.json`
3. Update `.cursor-plugin/plugin.json` (sometimes)
4. Update `package.json`
5. Update `RELEASE-NOTES.md`
6. Update or create `.version-bump.json` (sometimes)
7. Update `gemini-extension.json` (sometimes)
8. Run the version bump script:  
   ```sh
   bash scripts/bump-version.sh
   ```
9. Commit all updated files with a release message, e.g.:
   ```
   chore: release vX.Y.Z
   ```

### Update Brainstorm Server Implementation
**Trigger:** When making changes to the brainstorm server's behavior, structure, or reliability.  
**Command:** `/update-brainstorm-server`

1. Edit `skills/brainstorming/scripts/server.cjs` or `server.js`
2. Edit `skills/brainstorming/scripts/start-server.sh` and/or `stop-server.sh`
3. Optionally update `skills/brainstorming/visual-companion.md`
4. Update or fix related tests in `tests/brainstorm-server/`
5. Update `RELEASE-NOTES.md` to describe changes

_Example test file:_  
```
tests/brainstorm-server/server.test.js
```

### Skill Spec or Plan Review Loop Update
**Trigger:** When improving or changing the review process for plans/specs in skills.  
**Command:** `/update-review-loop`

1. Edit `skills/brainstorming/SKILL.md` and/or `skills/writing-plans/SKILL.md`
2. Edit `skills/brainstorming/spec-document-reviewer-prompt.md` and/or `skills/writing-plans/plan-document-reviewer-prompt.md`
3. Update `RELEASE-NOTES.md` to document review process changes

### Add or Update Contributor Guidelines
**Trigger:** When improving contributor onboarding, filtering PRs, or clarifying community standards.  
**Command:** `/update-contributor-guidelines`

1. Edit or add `CLAUDE.md`, `AGENTS.md`, `CODE_OF_CONDUCT.md`
2. Edit or add `.github/PULL_REQUEST_TEMPLATE.md`
3. Edit or add issue templates in `.github/ISSUE_TEMPLATE/`

_Example:_  
```
.github/ISSUE_TEMPLATE/bug_report.md
```

### Add or Update Codex/OpenCode Compatibility Docs
**Trigger:** When documenting compatibility plans, specs, or tool mappings for Codex App or OpenCode.  
**Command:** `/codex-opencode-docs`

1. Add or update files in `docs/superpowers/specs/*codex-app-compatibility*.md`
2. Add or update files in `docs/superpowers/plans/*codex-app-compatibility*.md`
3. Add or update `skills/using-superpowers/references/codex-tools.md`
4. Edit `docs/README.codex.md` or `docs/README.opencode.md` as needed

## Testing Patterns

- **Test File Naming:**  
  All test files use the `*.test.js` pattern.  
  _Example:_  
  ```
  tests/brainstorm-server/server.test.js
  ```

- **Testing Framework:**  
  Not explicitly specified; check test files for framework usage.

- **Test Structure:**  
  Organize tests by feature or server component, e.g., `tests/brainstorm-server/`.

## Commands

| Command                       | Purpose                                                        |
|-------------------------------|----------------------------------------------------------------|
| /release                      | Prepare and publish a new release version                      |
| /update-brainstorm-server     | Update or refactor brainstorm server logic and tests           |
| /update-review-loop           | Refine or revert review loop logic in skill markdowns/prompts  |
| /update-contributor-guidelines| Add or revise contributor guidelines and templates             |
| /codex-opencode-docs          | Add or update Codex/OpenCode compatibility documentation       |
```
