# Personal Claude Agents

This repository contains my personal collection of Claude agent definitions and configurations.

## Overview

These agents are specialized tools designed to assist with various development tasks:

- **architect-cleaner**: Architecture analysis and aggressive repository cleanup agent
- **claude-status**: Dashboard and metrics tracking agent
- **code-reviewer**: Comprehensive code review agent for Python projects
- **doc-writer**: Documentation generation and maintenance agent
- **prompt-engineer**: Transforms vague ideas into precise technical prompts
- **python-generator**: Modern Python 3.10+ code generation with Context7 integration
- **test-engineer**: Comprehensive test suite creation agent

## 📁 CRITICAL: Documentation Organization Rules

**ALL agents MUST follow these documentation placement rules:**

### Files Allowed in Project Root:
Only these files should exist in the project root directory:
- `README.md` - Project overview
- `CHANGELOG.md` - Version history
- `CONTRIBUTING.md` - Contribution guidelines
- `LICENSE` - License file
- `Claude.md` - AI metrics dashboard (managed by claude-status)
- `AGENT_LOG.md` - Agent activity log (all agents write here)

### Documentation Structure:
ALL other documentation MUST be placed in the appropriate `docs/` subdirectory:
```
docs/
├── README.md              # Documentation index
├── architecture/          # Architecture & technical design
│   ├── ARCHITECTURE.md
│   ├── ARCHITECTURE_REVIEW.md
│   └── PROJECT_SCOPE.md
├── project-management/    # Project management docs
│   ├── ERROR_LOG.md
│   ├── CLEANUP_REPORT.md
│   └── CHANGELOG_PR.md
├── development/          # Development guides
├── features/            # Feature documentation
├── api/                # API documentation
├── setup/              # Setup and configuration guides
└── archive/            # Old/deprecated documentation
```

### Agent-Specific Rules:

1. **architect-cleaner**: 
   - Creates docs in `docs/architecture/` and `docs/project-management/`
   - NEVER creates .md files in project root
   - Must create directories if they don't exist

2. **doc-writer**:
   - Updates documentation in appropriate `docs/` subdirectories
   - Can update README.md in root
   - Creates new docs in correct subdirectories

3. **All other agents**:
   - Should not create documentation files
   - Only update AGENT_LOG.md (root) and Claude.md (root)
   - Report findings to AGENT_LOG.md for doc-writer to process

## Structure

Each agent definition is stored as a markdown file containing:
- Agent description and capabilities
- Tool access permissions
- Usage examples
- Specific workflows and best practices

## Usage

These agent definitions are designed to be used with Claude Code and can be invoked through the Task tool with the appropriate `subagent_type` parameter.

## Recent Updates (2025-01-04)

- **architect-cleaner**: Updated to enforce proper documentation structure, no longer creates files in project root
- Documentation organization rules added to prevent cluttered root directories
- All agents now required to follow strict file placement guidelines

## Contributing

This is a personal repository for maintaining my agent definitions. Feel free to fork and adapt for your own use.