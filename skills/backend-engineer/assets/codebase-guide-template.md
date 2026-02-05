# Codebase Guide

> Quick reference for developers. Update when architecture changes.

## Overview

[1-2 sentences: What does this service/application do?]

## Directory Structure

```
project-root/
├── src/
│   ├── api/           # API endpoints
│   ├── models/        # Data models
│   ├── services/      # Business logic
│   ├── repositories/  # Data access layer
│   └── utils/         # Shared utilities
├── tests/
│   ├── unit/
│   └── integration/
├── docs/
└── config/
```

[Adjust structure to match actual project]

## Architecture

### Layer Overview

```
┌─────────────────────────────────────┐
│            API Layer                │  Request/Response handling
├─────────────────────────────────────┤
│          Service Layer              │  Business logic
├─────────────────────────────────────┤
│        Repository Layer             │  Data access
├─────────────────────────────────────┤
│           Database                  │  Data storage
└─────────────────────────────────────┘
```

### Key Components

#### [Component 1 Name]
- **Location:** `src/[path]`
- **Purpose:** [What it does]
- **Key files:**
  - `file1.py` - [Description]
  - `file2.py` - [Description]

#### [Component 2 Name]
- **Location:** `src/[path]`
- **Purpose:** [What it does]
- **Key files:**
  - `file1.py` - [Description]

## Configuration

- **Environment variables:** `config/.env`
- **App settings:** `config/settings.py`

| Variable | Description | Required |
|----------|-------------|----------|
| `DATABASE_URL` | Database connection string | Yes |
| `API_KEY` | External API key | No |

## Testing

Run tests:
```bash
pytest tests/
```

Coverage report:
```bash
pytest --cov=src tests/
```

## Common Patterns

### [Pattern 1: e.g., Error Handling]
[Brief description and example]

### [Pattern 2: e.g., Dependency Injection]
[Brief description and example]

## Changelog

| Date | Change | Author |
|------|--------|--------|
| YYYY-MM-DD | Initial architecture | [Name] |
