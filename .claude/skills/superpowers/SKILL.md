# superpowers Development Patterns

> Auto-generated skill from repository analysis

## Overview

The superpowers repository is a JavaScript-based Claude plugin system that provides enhanced functionality through a structured plugin architecture. It emphasizes cross-platform compatibility, particularly addressing Windows-specific execution challenges, and maintains a robust release management system with comprehensive documentation.

## Coding Conventions

### File Naming
- Use **kebab-case** for all filenames
  ```
  plugin-manager.js
  session-start.sh
  release-notes.md
  ```

### Import/Export Style
- Use **named exports** with **alias imports**
  ```javascript
  // Good
  import { PluginManager as PM } from './plugin-manager.js';
  export { createPlugin, validateManifest };
  
  // Avoid default exports
  ```

### Commit Message Format
- Follow conventional commit format with prefixes
- Keep messages around 54 characters
  ```
  feat: add Windows hook compatibility layer
  fix: resolve plugin manifest validation error
  docs: update installation guide for macOS
  refactor: simplify release workflow scripts
  ```

### Testing
- Test files follow pattern: `*.test.*`
- Place tests in `tests/` directory with descriptive names
  ```
  tests/plugin/test-manifest-validation.sh
  tests/hooks/test-windows-execution.sh
  ```

## Workflows

### Release Version Management
**Trigger:** When preparing a new version release
**Command:** `/release`

1. Update `.claude-plugin/plugin.json` with new version number
2. Update `.claude-plugin/marketplace.json` with latest metadata
3. Document all changes in `RELEASE-NOTES.md` following existing format
4. Ensure all plugin manifest dependencies are properly versioned
5. Test installation across platforms before finalizing release

Example plugin.json update:
```json
{
  "version": "1.2.3",
  "name": "superpowers",
  "description": "Enhanced Claude functionality"
}
```

### Fix Windows Hooks
**Trigger:** When Windows users report hook execution failures
**Command:** `/fix-windows-hooks`

1. Update `hooks/hooks.json` configuration with Windows-compatible paths
2. Modify `hooks/run-hook.cmd` wrapper script for better compatibility
3. Update `hooks/session-start` with cross-platform execution logic
4. Add or modify `.gitattributes` for proper line ending handling
5. Document Windows-specific fixes in `RELEASE-NOTES.md`

Example hook configuration:
```json
{
  "windows": {
    "executor": "cmd.exe",
    "wrapper": "hooks/run-hook.cmd"
  }
}
```

### Update Skill Documentation
**Trigger:** When adding new skill requirements or workflow changes
**Command:** `/update-skill`

1. Locate relevant skill file in `skills/*/SKILL.md`
2. Add new integration requirements section if needed
3. Update workflow documentation with step-by-step instructions
4. Add usage restrictions or guidelines for new features
5. Ensure examples are current and functional

### Update Installation Documentation
**Trigger:** When installation process changes or platform-specific issues are found
**Command:** `/update-install-docs`

1. Update `.codex/INSTALL.md` with latest installation steps
2. Sync changes across `docs/README.codex.md` and `docs/README.opencode.md`
3. Update `.opencode/INSTALL.md` with platform-specific variations
4. Add missing prerequisites and verification steps
5. Test installation instructions on target platforms

### Add Test Coverage
**Trigger:** When implementing TDD approach or validating new features
**Command:** `/add-tests`

1. Create test scripts in `tests/` directory following naming convention
2. Add `run-test.sh` script for automated execution
3. Implement test cases covering expected behavior patterns
4. Ensure tests are cross-platform compatible
5. Update documentation with testing instructions

Example test structure:
```bash
#!/bin/bash
# tests/plugin/test-manifest-validation.sh

test_valid_manifest() {
    result=$(validate_manifest "valid-plugin.json")
    assertEquals "success" "$result"
}

test_invalid_version() {
    result=$(validate_manifest "invalid-version.json")
    assertEquals "error" "$result"
}
```

## Testing Patterns

Tests in this repository follow shell script patterns with descriptive function names:
- Use `test_` prefix for test functions
- Include both positive and negative test cases
- Provide clear assertion messages
- Test cross-platform compatibility where applicable

## Commands

| Command | Purpose |
|---------|---------|
| `/release` | Create new version release with manifest updates |
| `/fix-windows-hooks` | Address Windows-specific hook execution issues |
| `/update-skill` | Update skill documentation and requirements |
| `/update-install-docs` | Update installation guides across platforms |
| `/add-tests` | Add test coverage for new functionality |