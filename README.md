# BASH Framework Project

## Overview

An intelligent coding agent framework for building robust automations using the BASH Framework (Blueprints, Agents, Scripts, History) - an architecture that enforces a clear separation of concerns between AI-driven probabilistic reasoning and deterministic code execution.

## Philosophy

The BASH framework is built on a core principle: **AI handles reasoning, code handles execution**. This decoupling creates a system that is both effective and reliable by:

- Eliminating compounding errors from sequential AI tasks
- Providing deterministic, testable execution layers
- Maintaining clear audit trails and context preservation
- Enabling continuous learning and improvement

## Architecture

### Layer 1: Blueprints (Workflow SOPs)
**Location:** `blueprints/`

Markdown-based Standard Operating Procedures that serve as the source of truth for workflows. Each blueprint defines:
- Objective
- Required inputs
- Step-by-step process
- Expected outputs
- Edge case handling
- Validation criteria

### Layer 2: Agents (The Orchestrator)
The AI reasoning engine responsible for:
- Reading context and selecting appropriate scripts/blueprints
- Executing scripts in correct sequence
- Handling ambiguity and edge cases
- Verifying outputs and deciding next steps
- Recovering gracefully from failures

### Layer 3: Scripts (Deterministic Execution)
**Location:** `scripts/`

Python scripts that handle all deterministic operations:
- Atomic and modular (one responsibility per script)
- Clear success/failure messaging via stdout/stderr
- Robust error handling
- Type-hinted and well-documented
- Never contain hardcoded credentials

### Layer 4: History (The Changelog)
**Location:** `history/changelog.md`

System-wide version tracking using semantic versioning:
- **Major (X.0.0):** Breaking changes requiring Blueprint/script updates
- **Minor (0.X.0):** New backward-compatible capabilities
- **Patch (0.0.X):** Bug fixes and refinements

## Directory Structure

```
.tmp/               # Temporary/disposable intermediate files
blueprints/         # Workflow SOPs in Markdown
scripts/            # Deterministic Python scripts
history/            # Changelog and persistent system records
deliverables/       # Final outputs
.env               # API keys and environment variables (gitignored)
requirements.txt   # Python dependencies
```

## Getting Started

### Prerequisites

```bash
python3 -m pip install -r requirements.txt
```

### Environment Setup

1. Copy `.env.example` to `.env`
2. Add your API keys and credentials to `.env`
3. Never commit `.env` or credential files to version control

## Usage

The Agent (AI) orchestrates the system by:

1. **Reading the request** - Understanding user intent
2. **Selecting the blueprint** - Choosing the appropriate workflow
3. **Executing scripts** - Running deterministic operations in sequence
4. **Verifying outputs** - Checking results against expected criteria
5. **Logging changes** - Recording evolution in changelog

## Development Principles

### Prioritize Reuse Over Creation
Before creating new scripts:
1. Audit `scripts/` for existing capabilities
2. Refactor near-matches rather than duplicating
3. Only create new scripts when no alternative exists

### Debug Systematically
When failures occur:
1. **Analyze:** Read full traceback to identify root cause
2. **Fix:** Patch the script
3. **Record:** Log error and solution in changelog
4. **Update:** Amend relevant Blueprint to prevent recurrence

### Maintain Living Workflows
Blueprints are persistent assets:
- Amend and improve existing files
- Document constraints and optimizations
- Never overwrite without permission
- Preserve original intent while enhancing robustness

### Adaptation Loop
Transform failures into learning:
1. **Diagnose** - Identify failure point
2. **Repair** - Apply appropriate fix
3. **Verify** - Confirm fix works
4. **Standardize** - Update Blueprint
5. **Log** - Record in changelog and update requirements.txt

## Security Best Practices

- Never hardcode credentials
- Always use `.env` for sensitive data
- Validate and sanitize all external inputs
- Implement rate limiting for API calls
- Keep credential files in `.gitignore`
- Never log or expose secrets in output

## Version History

See `history/changelog.md` for detailed version history and evolution.

## License

MIT License. Copyright (c) 2026