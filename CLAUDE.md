# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This repository contains a collection of **Claude Code Skills** for AgnoAGI development. It provides comprehensive, production-ready guidance for building AI agents using the Agno framework (formerly Phidata) with various model providers and deployment strategies.

### Included Skills

Located in `.claude/skills/`, containing 5 professional skills (~118KB total):

1. **Python_AI_Fundamentals** (16KB) - Essential Python patterns for AI/ML development including NumPy, Pandas, PyTorch, async programming, type hints, testing, and best practices

2. **Ollama_LocalModels** (21KB) - Complete integration guide for Ollama local models including installation, streaming, embeddings, RAG, vision models, and FastAPI integration

3. **AgnoAGI_Agents** (23KB) - Comprehensive Agno framework guide covering basic agents, multi-agent systems, reasoning agents, custom tools, memory, knowledge bases, and production patterns

4. **PaidModels_Integration** (25KB) - Integration with commercial APIs including Claude (Anthropic), OpenAI, Google Gemini, Groq, with function calling, vision, caching, and cost tracking

5. **Production_Deployment** (26KB) - Production deployment strategies using Docker, Kubernetes, FastAPI, monitoring (Prometheus/Sentry), CI/CD pipelines, and security best practices

## Working with Skills

### Viewing Skills

```bash
# List all skills
ls -lh .claude/skills/*/SKILL.md

# View skill sizes
du -sh .claude/skills/*

# View skill metadata (frontmatter)
head -n 10 .claude/skills/AgnoAGI_Agents/SKILL.md

# Search across all skills
grep -r "pattern" .claude/skills/ --include="SKILL.md"

# View examples in a skill
grep -A 10 "```python" .claude/skills/AgnoAGI_Agents/SKILL.md
```

### Editing Skills

Each skill follows this structure:

```
.claude/skills/
├── SkillName/
│   └── SKILL.md          # Main skill content
└── README.md             # Overview and usage instructions
```

**SKILL.md format:**
```markdown
---
name: Skill Display Name
description: Brief description for Claude Code
version: 1.0.0
---

# Skill Content

Comprehensive documentation, examples, patterns...
```

**Important when editing skills:**
- Maintain YAML frontmatter (name, description, version)
- Include complete, runnable code examples
- Add context about when to use patterns
- Include error handling and best practices
- Link to official documentation
- Use clear section headers for navigation

### Adding New Skills

To create a new skill:

```bash
# Create skill directory
mkdir .claude/skills/NewSkill_Name

# Create SKILL.md with proper frontmatter
cat > .claude/skills/NewSkill_Name/SKILL.md << 'EOF'
---
name: New Skill Name
description: Expert guidance for...
version: 1.0.0
---

# Content here
EOF

# Update .claude/skills/README.md to list the new skill
```

### Testing Skills

Skills are automatically loaded by Claude Code. To verify:

```bash
# Check skill file exists and has correct permissions
test -f .claude/skills/AgnoAGI_Agents/SKILL.md && echo "Skill file exists"

# Validate frontmatter structure (should show YAML)
head -n 5 .claude/skills/AgnoAGI_Agents/SKILL.md | grep -E "^(---|name:|description:)"

# Count code examples in a skill
grep -c '```python' .claude/skills/AgnoAGI_Agents/SKILL.md
```

## Key Architecture Notes

### Multi-Language Documentation

- Primary documentation is in Spanish (INSTRUCCIONES_SKILLS.md, README files)
- Skill content includes both English and Spanish examples
- Code examples and patterns are language-agnostic

### Skill Loading Strategy

Claude Code automatically loads skills based on context. When users mention:
- "agent" or "Agno" → loads AgnoAGI_Agents
- "Ollama" or "local model" → loads Ollama_LocalModels
- "Claude API" or "OpenAI" → loads PaidModels_Integration
- "Docker" or "deploy" → loads Production_Deployment
- "Python" or "async" → loads Python_AI_Fundamentals

Multiple skills can be loaded simultaneously for complex tasks.

### Skill Content Philosophy

Skills contain:
- **Complete examples**: Full, working code that can be copy-pasted
- **Production patterns**: Real-world implementations, not toy examples
- **Error handling**: Proper exception handling and validation
- **Best practices**: Type hints, logging, testing approaches
- **Context**: When to use each pattern and why

## Git Workflow

### Development Branch

Work is done on feature branches following the pattern:
```
claude/[task-description]-[session-id]
```

Example: `claude/initialize-project-011CUPDSpxfUphSciLaBZrMd`

### Push Requirements

**CRITICAL**: Branch names must start with `claude/` and end with matching session ID, otherwise push will fail with 403.

```bash
# Correct push command
git push -u origin claude/feature-name-sessionID

# Network retry strategy: up to 4 retries with exponential backoff (2s, 4s, 8s, 16s)
```

### Fetch/Pull Operations

```bash
# Fetch specific branch
git fetch origin claude/branch-name

# Pull with retry support (same exponential backoff as push)
git pull origin claude/branch-name
```

## Common Commands

### Skill Development

```bash
# View all skills with metadata
for skill in .claude/skills/*/SKILL.md; do
  echo "=== $(basename $(dirname $skill)) ==="
  head -n 5 "$skill"
done

# Search for specific API usage across skills
grep -r "OpenAIChat" .claude/skills/ --include="SKILL.md" -A 3

# Count total lines of documentation
wc -l .claude/skills/*/SKILL.md
```

### Validation

```bash
# Ensure all skills have frontmatter
for skill in .claude/skills/*/SKILL.md; do
  if ! head -n 1 "$skill" | grep -q "^---$"; then
    echo "Missing frontmatter: $skill"
  fi
done

# Check for broken code blocks (unmatched ```)
for skill in .claude/skills/*/SKILL.md; do
  count=$(grep -c '```' "$skill")
  if [ $((count % 2)) -ne 0 ]; then
    echo "Unmatched code blocks in $skill"
  fi
done
```

## Important Notes

1. **No package.json or build system**: This is a documentation repository, not a code project. There are no npm/build/test commands.

2. **Skills are self-contained**: Each skill should be independently useful without requiring other skills.

3. **Version compatibility**: Skills reference current versions of libraries (as of October 2025). Check for updates when editing.

4. **File size awareness**: Skills range from 16-26KB. Keep content comprehensive but focused. If a skill exceeds ~30KB, consider splitting it.

5. **Code examples must be tested**: All Python examples should be valid, runnable code with proper imports and error handling.

6. **Documentation references**: Always include links to official documentation (Agno, Ollama, Anthropic, OpenAI, etc.)

## Repository Context Files

- **INSTRUCCIONES_SKILLS.md**: Comprehensive Spanish-language guide for using these skills with Claude Code, including setup, examples, troubleshooting, and quick-start templates

- **.claude/skills/README.md**: Overview of all skills with usage instructions, integration options, and common use cases

These files are valuable references when users ask how to use the skills or need examples.
