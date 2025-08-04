# 5 Starter Agents - Integration Guide

## 🚀 Your Simplified Agent Setup

### The Core Team:
1. **python-generator** - Creates code with Context7
2. **code-reviewer** - Ensures quality 
3. **doc-writer** - Documents everything
4. **test-engineer** - Tests with Context7
5. **claude-status** - Tracks everything

## 📁 Required Files Structure

```
project/
├── .claude/
│   └── agents/
│       ├── python-generator.md
│       ├── code-reviewer.md
│       ├── doc-writer.md
│       ├── test-engineer.md
│       └── claude-status.md
├── PROJECT_SCOPE.md    # Your project structure (create once)
├── Claude.md           # AI dashboard (auto-maintained)
├── AGENT_LOG.md        # Agent activity log (auto-updated)
└── src/               # Your code
```

## 🔄 How They Work Together

### Every Agent:
1. **Reads** these files first:
   - PROJECT_SCOPE.md (for context)
   - Claude.md (for status)
   - AGENT_LOG.md (for history)

2. **Does** its specific job

3. **Writes** to AGENT_LOG.md:
   - What it did
   - What it found
   - What should happen next

4. **Updates** Claude.md if needed

## 📝 Common Workflows

### Workflow 1: New Feature
```bash
# Step 1: Generate code
"Use python-generator to create a user authentication module"
# → Reads context, uses Context7 for latest patterns, logs activity

# Step 2: Test it
"Use test-engineer to create tests for the authentication module"
# → Reads what was created, writes comprehensive tests, logs results

# Step 3: Review everything  
"Use code-reviewer to check the authentication implementation"
# → Reviews both code and tests, logs findings

# Step 4: Document it
"Use doc-writer to document the authentication API"
# → Creates docs based on implementation, logs what was documented

# Step 5: Update dashboard
"Use claude-status to update the project dashboard"
# → Aggregates all activities, updates Claude.md
```

### Workflow 2: Bug Fix
```bash
# Step 1: Review issue
"Use code-reviewer to analyze the payment processing bug"
# → Identifies issues, logs findings

# Step 2: Fix it
"Use python-generator to fix the payment validation issue"
# → Implements fix, logs changes

# Step 3: Test fix
"Use test-engineer to verify the payment fix works"
# → Tests edge cases, logs results

# Step 4: Update status
"Use claude-status to log the bug fix completion"
# → Updates metrics
```

## 🎯 The Magic of AGENT_LOG.md

Each agent adds entries like:
```markdown
### 14:30 - python-generator
**Task**: Create user authentication module
**Status**: ✅ Success
**Output**: Created auth.py (245 lines)
**Next**: test-engineer should test this
---

### 14:35 - test-engineer  
**Task**: Test authentication module
**Status**: ⚠️ Issues found
**Coverage**: 87%
**Found**: Missing validation for empty password
**Next**: python-generator should fix
---
```

This creates a **conversation between agents**!

## 💡 Best Practices

### 1. **Start Simple**
```bash
# Don't chain everything at once
# Start with single agents:
"Use python-generator to create a hello world endpoint"
```

### 2. **Read the Logs**
```bash
# After each agent:
"Show me the last entry in AGENT_LOG.md"
# Learn what happened!
```

### 3. **Let Agents Suggest Next Steps**
Each agent recommends what should happen next based on what they found.

### 4. **Daily Status Check**
```bash
# End of day:
"Use claude-status to summarize today's work"
# Get insights and metrics
```

## 🛠️ Initial Setup

### 1. Create PROJECT_SCOPE.md manually:
```markdown
# Project Scope

## Overview
Simple Python API with FastAPI

## Structure
- src/ - Source code
- tests/ - Test files
- docs/ - Documentation

## Tech Stack
- Python 3.11
- FastAPI
- PostgreSQL
- Pytest

## Standards
- Type hints required
- 80% test coverage minimum
- Google-style docstrings
```

### 2. Initialize AGENT_LOG.md:
```markdown
# Agent Activity Log

## Start Date: [TODAY]

---
```

### 3. Initialize Claude.md:
```bash
"Use claude-status to initialize the AI dashboard"
```

## 🚨 Common Issues & Solutions

### "Agent doesn't know project structure"
→ Make sure PROJECT_SCOPE.md exists and is detailed

### "Agents repeating work"
→ Check AGENT_LOG.md - agents should read previous entries

### "Context7 not working"
→ Verify MCP is installed: `claude mcp list`

### "Logs getting too long"
→ Archive weekly: `mv AGENT_LOG.md archives/AGENT_LOG_week1.md`

## 📈 What Success Looks Like

After 1 week, you should see:
- Clean AGENT_LOG.md showing agent collaboration
- Claude.md with trending metrics
- Efficient workflows emerging
- Time savings documented
- Quality improvements tracked

## 🎮 Quick Commands Cheatsheet

```bash
# Generate code
"python-generator: implement [feature]"

# Review code
"code-reviewer: check [file/feature]"

# Write tests
"test-engineer: test [component]"

# Document
"doc-writer: document [feature]"

# Update status
"claude-status: update dashboard"

# Check specific log
"Show me python-generator's last entry in AGENT_LOG.md"

# See today's activities
"Show me today's entries in AGENT_LOG.md"
```

## 🏁 Next Steps

1. **Week 1**: Use agents individually
2. **Week 2**: Try simple 2-agent chains
3. **Week 3**: Full workflows
4. **Week 4**: Analyze patterns and optimize

Remember: The logs are your friend - they show exactly how agents work together!