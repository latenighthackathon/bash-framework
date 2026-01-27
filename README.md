# BASH Framework Project
![thumbnail of BASH framework](/.github/img/bash-framework.png)

## Overview

An intelligent coding agent framework for building robust automations using the BASH Framework (Blueprints, Agents, Scripts, History) - an architecture that enforces a clear separation of concerns between AI-driven probabilistic reasoning and deterministic code execution.

## Philosophy

The BASH framework is built on a core principle: **AI handles reasoning, code handles execution**. 
![thumbnail detailing separation of concerns](/.github/img/aivscode.png)

This decoupling creates a system that is both effective and reliable by:

- Eliminating compounding errors from sequential AI tasks
- Providing deterministic, testable execution layers
- Maintaining clear audit trails and context preservation
- Enabling continuous learning and improvement

Why this is helpful:

In LLM-only solutions, assuming your AI agent is 90% successful in processing each step, after 5 consecutive steps, accuracy and success rates can plummet to 59%. 

![thumbnail detailing blueprints](/.github/img/successfalloff.png)

By ensuring all tasks are handled by predictable, deterministic code/scripts, we reduce the impact of compounding errors by the overall system.

## Architecture

### Layer 1: Blueprints (Workflow SOPs)
Blueprints translates the user's request/automation idea into an actionable strategy and SOP via a detailed Markdown file. This is automatically created by the agent and can be tailored/customized to your specific needs.

**Location:** `blueprints/`

![thumbnail detailing blueprints](/.github/img/blueprints.png)

Markdown-based Standard Operating Procedures that serve as the source of truth for workflows. Each blueprint defines:
- Objective
- Required inputs
- Step-by-step process
- Expected outputs
- Edge case handling
- Validation criteria

### Layer 2: Agents (The Orchestrator)

![thumbnail detailing agents](/.github/img/agents.png)

The AI reasoning engine responsible for:
- Reading context and selecting appropriate scripts/blueprints
- Executing scripts in correct sequence
- Handling ambiguity and edge cases
- Verifying outputs and deciding next steps
- Recovering gracefully from failures

### Layer 3: Scripts (Deterministic Execution)
**Location:** `scripts/`

![thumbnail detailing scripts](/.github/img/scripts.png)

Python scripts and tools that handle all deterministic operations:
- Atomic and modular (one responsibility per script)
- Clear success/failure messaging via stdout/stderr
- Robust error handling
- Type-hinted and well-documented
- Never contain hardcoded credentials

### Layer 4: History (The Changelog)
**Location:** `history/changelog.md`

![thumbnail detailing changelog](/.github/img/history.png)

System-wide version tracking using semantic versioning:
- **Major (X.0.0):** Breaking changes requiring Blueprint/script updates
- **Minor (0.X.0):** New backward-compatible capabilities
- **Patch (0.0.X):** Bug fixes and refinements

## Directory Structure After Project is Initialized

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

### Recommended Setup:

**VS Studio Code + Claude Code extension** OR
**Claude Code/Claude Code CLI**

1. In your project folder, simply copy/paste the contents from the provided `claude.md` file in this repo into your claude.md file. Save your changes.
2. In VS Studio Code -> Claude Code chat (Or in Claude Code), type in "initialize this project based on my updated claude.md file"
3. Once setup is complete, you're ready to ask Claude to build your desired automation!

## BASH Operational Flow

The Agent (AI) orchestrates the system by:

1. **Reading the request** - Understanding user intent
2. **Selecting or Creating the `blueprints/`** - Choosing the appropriate Blueprint SOP, or creating one if it does not exist yet
3. **Executing or Creating the `scripts/`** - Running deterministic operations in sequence, or creating the scripts if the capability does not exist yet
4. **Verifying outputs** - Checking results against expected criteria
5. **Logging changes** - Recording evolution in changelog

### Prioritize Reuse Over Creation

Before creating new scripts:
1. Audit `scripts/` for existing capabilities
2. Refactor near-matches rather than duplicating
3. Only create new scripts when no alternative exists

### Debug Systematically, Patch, Log

![thumbnail detailing blueprints](/.github/img/selfrepairloop.png)

When failures occur:
1. **Diagnose:** Read full traceback to identify root cause
2. **Fix:** Patch the script
3. **Verify:** Run test execution and validate that the patch works
4. **Standardize and Document:** Update appropriate SOPs in `blueprints/`
4. **Log:** Create date-stamped update in `history/changelog.md`

### Maintain Living Workflows
Blueprints are persistent assets:
- Amend and improve existing files
- Document constraints and optimizations
- Never overwrite without permission
- Preserve original intent while enhancing robustness

### Adaptation/Self-Improvement Loop
Transform failures into learning:
1. **Diagnose** - Identify failure point
2. **Repair** - Apply appropriate fix
3. **Verify** - Confirm fix works
4. **Standardize** - Update Blueprint
5. **Log** - Record in changelog and update requirements.txt

## Follows Security Best Practices

- Never hardcode credentials
- Always use `.env` for sensitive data
- Validate and sanitize all external inputs
- Implement rate limiting for API calls
- Keep credential files in `.gitignore`
- Never log or expose secrets in output

## Version History

Track code changes made by the agent(s) in `history/changelog.md` for detailed version history and code evolution.

## License

[MIT License](https://github.com/latenighthackathon/bash-framework/blob/main/LICENSE). Copyright (c) 2026