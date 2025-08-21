# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a personal collection of Claude agent definitions. Each `.md` file in the root directory defines a specialized agent with specific capabilities and tools.

## Available Agents

- **agent-architect-cleaner**: Architecture analysis and aggressive repository cleanup
- **agent-claude-status**: Dashboard and metrics tracking 
- **agent-code-reviewer**: Comprehensive Python code review
- **agent-doc-writer**: Documentation generation and maintenance
- **agent-prompt-engineer**: Transforms vague ideas into precise technical prompts
- **agent-python-generator**: Modern Python 3.10+ code generation
- **agent-test-engineer**: Comprehensive test suite creation
- **agent-researcher**: Research best practices and design optimal solutions

## Critical Documentation Rules

**Root Directory Files (ONLY these allowed):**
- README.md, CHANGELOG.md, CONTRIBUTING.md, LICENSE
- Claude.md (AI metrics dashboard)
- AGENT_LOG.md (Agent activity log)

**All other documentation MUST go in docs/ subdirectories:**
```
docs/
├── architecture/        # Architecture & technical design
├── project-management/  # Project management docs
├── development/         # Development guides
├── features/           # Feature documentation
└── api/               # API documentation
```

## Mandatory Requirements (PFLICHT!)

**All agents MUST:**
1. **CREATE these files if missing:**
   - `AGENT_LOG.md` (root) - Initialize with header
   - `Claude.md` (root) - Create AI dashboard template
   - `docs/architecture/PROJECT_SCOPE.md` - Generate from codebase

2. **MAINTAIN AGENT_LOG.md after EVERY session:**
   - Document all activities, findings, and recommendations
   - Include timestamps and agent names
   - Track inter-agent communication
   - This is MANDATORY (PFLICHT!) - no exceptions

3. **Specific agent responsibilities:**
   - **agent-architect-cleaner**: Creates missing meta-files, maintains PROJECT_SCOPE.md
   - **agent-prompt-engineer**: Creates missing files, documents generated prompts
   - **agent-researcher**: Creates missing files, saves research to `research/` directory
   - **All other agents**: Must update AGENT_LOG.md after each session

## Development Workflow

1. **Making Changes to Agents:**
   - Edit the agent's `.md` file directly
   - Maintain YAML frontmatter (name, description, tools)
   - Update examples if behavior changes

2. **Testing Agent Changes:**
   - Use the Task tool with appropriate `subagent_type`
   - Verify tool access matches the agent's needs
   - Test with realistic scenarios from the agent's examples

3. **Agent Communication:**
   - All agents write to AGENT_LOG.md for inter-agent communication
   - Agents read AGENT_LOG.md to understand previous work
   - agent-architect-cleaner maintains PROJECT_SCOPE.md and ERROR_LOG.md

## Common Commands

```bash
# View repository status
git status

# View recent changes
git diff

# View commit history  
git log --oneline -10

# Stage and commit changes
git add <file>
git commit -m "Update agent: <description>"
```

## Important Conventions

- **AGENT_LOG.md Maintenance**: PFLICHT! Every agent must write detailed session reports
- **File Creation**: agent-architect-cleaner, agent-prompt-engineer, and agent-researcher must create missing essential files
- **Session Documentation**: All agents must document their work in AGENT_LOG.md without exception

- **German Documentation**: Agent_Docs/DEVELOPMENT_GUIDE.md contains German text with development guidelines
- **Tool Lists**: Ensure agents have all required tools in their frontmatter
- **File Naming**: Generated files follow pattern: `[type]-[description]-[date].md`
- **Agent Coordination**: Use AGENT_LOG.md for tracking all agent activities

## Repository Structure

```
/
├── *.md                    # Agent definitions
├── Agent_Docs/            # Agent development documentation
│   ├── DEVELOPMENT_GUIDE.md
│   ├── Agent_Chain_Examples.md
│   └── Prompt Engineer Template.md
└── .git/                  # Git repository
```