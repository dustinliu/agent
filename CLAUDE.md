# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Skill Linker** — a Python CLI tool that copies AI agent skills from source directories to multiple IDE skill directories (Claude Code, Cursor, Antigravity/Gemini). It reads `skills_config.toml` to determine which skills to copy, where to find them, and which IDE targets to deploy to.

## Common Commands

```bash
# Install dependencies
uv sync

# makefile targets
make test          # Run tests with coverage
make lint          # Run ruff linting
make format-check  # Check code formatting
make push          # Full CI pipeline + deploy
make clean         # Clean generated files
```

## Architecture

Single-module Python project using `uv` for dependency management:

- `deploy.py` — entire application logic: config parsing (TOML), skill discovery across multiple source directories, and copying skill directories to IDE targets. Entry point is `main()`, core logic in `link_skills()`.
- `test_deploy.py` — pytest test suite (37 tests) organized by test classes per function (`TestFindSkillInSources`, `TestExpandPath`, `TestLoadConfig`, `TestCopySkill`, `TestLinkSkills`).
- `skills_config.toml` — configuration: skill names list, source directory paths, and target IDE directories with enable/disable flags.
- `skills/` — local skill definitions. Each skill is a directory with `SKILL.md` and optional `assets/` and `references/` subdirectories.

## Conventions

- Python >=3.11 required (uses `tomllib` from stdlib)
- all the skills I want to  modifiy located in the project root directory `skills/`
- Linting: ruff with rules F, E, W, I, N, UP, B, C4, SIM
- Formatting: ruff format (double quotes, spaces, unix line endings)
- Coverage threshold: 85% (configured in `pyproject.toml`)
- Source code and comments in English
