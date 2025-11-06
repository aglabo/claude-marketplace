# CLAUDE.md

This file provides guidance to Claude Code when working with code in this repository.

## Project Overview

This is an **OSS Project Starter Template** for bootstrapping open source projects with pre-configured development tools focused on code quality, security, and consistent formatting.

**Tech Stack**: TypeScript, dprint, lefthook, gitleaks, secretlint, commitlint

## Essential Commands

### Code Formatting

- `dprint fmt` - Format all files
- `dprint check` - Check formatting without changes

### Git Hooks

- `lefthook install` - Install Git hooks
- `lefthook run pre-commit` - Run pre-commit checks manually

### Security Scanning

- `gitleaks protect --config ./configs/gitleaks.toml --staged` - Scan staged files for secrets
- `secretlint --secretlintrc ./configs/secretlint.config.yaml --secretlintignore .gitignore --maskSecrets [files]` - Run secretlint

### Commit Validation

- `commitlint --config ./configs/commitlint.config.js --edit` - Validate commit message

## Directory Structure

```
.
├── .github/workflows/    # CI/CD (secrets scanning)
├── .serena/              # Serena MCP configuration
├── configs/              # Tool configurations
│   ├── commitlint.config.js
│   ├── gitleaks.toml
│   └── secretlint.config.yaml
├── dprint.jsonc          # Formatter config
├── lefthook.yml          # Git hooks config
└── .editorconfig         # Editor settings
```

## Git Hook Workflow

**lefthook** manages two hook stages:

1. **pre-commit** (parallel):
   - `gitleaks` - Scans staged files for secrets
   - `secretlint` - Additional secret detection with masking

2. **commit-msg**:
   - `commitlint` - Validates Conventional Commits format

## Code Style

### Formatting Rules (dprint)

- **Line width**: 120 characters
- **Indentation**: 2 spaces (default)
- **Line endings**: LF (Unix-style)
- **TypeScript**: Single quotes, always use braces, force arrow function parentheses
- **Special cases**: PowerShell (4 spaces), Git configs (tabs)

### Commit Message Format (Conventional Commits)

```
<type>(<scope>): <subject>
```

**Allowed types**: `feat`, `fix`, `chore`, `docs`, `test`, `refactor`, `perf`, `ci`, `config`, `release`, `merge`, `build`, `style`, `deps`

**Rules**:

- Header max length: 72 characters
- Subject must not use start-case or pascal-case

## Task Completion Checklist

When completing a task:

1. Format code: `dprint fmt`
2. Stage changes: `git add .`
3. Commit (hooks run automatically): `git commit`
4. Push: `git push`

**Note**: Pre-commit hooks automatically run security scans. Never commit files containing secrets.

## Serena MCP Integration

This project uses **Serena MCP** for AI-assisted development. Memory files in `.serena/` contain:

- Project overview and tech stack
- Code style and conventions
- Suggested commands
- Task completion checklist
- Codebase structure
- Design patterns and guidelines

Reference these memories for detailed project context.

## Dependencies

External tools (install via Scoop on Windows):

- lefthook, delta, commitlint, gitleaks, secretlint, dprint

These are NOT bundled with the repository.
