# Project Structure Guide

This document outlines the structure and organization of the jh-prompt-library repository, a collection of prompts, instructions, and configurations for LLM models and AI agents.

## Overview

This is a prompt and instruction library designed for:
- **AI Agent Configuration** - Instructions and memory files for AI assistants (Sidney, Mel)
- **LLM Prompts** - Reusable prompts for coding, life questions, and examples
- **GitHub Workflows** - Version control guides and best practices
- **Agent Memory Management** - Structured memory context for personalized AI interactions

## Project Structure

```
jh-prompt-library/
├── .github/                         # GitHub-specific files
│   └── github-instructions.md       # This file - project documentation
├── .git/                            # Git repository metadata
├── .gitignore                       # Files to ignore in version control
├── simtheory/                       # SimTheory agent configurations
│   ├── sidney-instructions.md       # Tech assistant behavioral directives
│   ├── sidney-memory-*.md          # Tech assistant memory contexts
│   ├── mel-instructions.md         # Life assistant behavioral directives
│   ├── mel-memory-*.md             # Life assistant memory contexts
│   ├── template-*.md               # Generic assistant templates
│   └── sidney-README.md            # Sidney configuration documentation
├── general-prompt/                  # General purpose prompts
│   ├── email-newsletter-prompt.md  # Newsletter analysis template
│   └── explaination-prompt.md      # Feynman-style explanation prompt
├── github-instructions/             # Git & GitHub guides (if exists)
│   ├── README.md                   # Overview of Git guides
│   ├── git-basics.md               # Essential Git commands
│   ├── git-branching.md            # Branch strategies
│   └── git-troubleshooting.md      # Common issues & solutions
├── simtheory-backup/               # Backup files (gitignored)
└── README.md                       # Repository overview
```

## Directory Details

### `/simtheory/` - AI Agent Configurations
SimTheory agent configuration files following a modular architecture:

#### Instructions Files (Behavioral)
- **`sidney-instructions.md`** - Tech assistant behavior and modes
- **`mel-instructions.md`** - Life assistant behavior and focus areas

#### Memory Files (Context)
- **`sidney-memory-personal.md`** - Professional identity and work context
- **`sidney-memory-technical.md`** - Tech stack and development environment
- **`sidney-memory-workflow.md`** - Email/calendar/coding rules
- **`sidney-memory-macos.md`** - Platform-specific guidance
- **`mel-memory-personal.md`** - Personal life and family context
- **`mel-memory-workflow.md`** - Life assistant workflow rules

#### Templates
- **`template-coding-partner.md`** - Generic coding assistant template
- **`template-personal-assistant.md`** - Generic personal assistant template
- **`template-project-manager.md`** - Generic project manager template

#### Documentation
- **`sidney-README.md`** - Comprehensive guide for Sidney configuration

### `/general-prompt/` - Reusable Prompts
General-purpose prompts for various LLM interactions:
- Newsletter analysis templates
- Explanation prompts
- Prompt snippets and experiments

### `/github-instructions/` - Version Control Guides
Git and GitHub reference materials:
- Basic commands and workflows
- Branching strategies
- Troubleshooting guides

## File Naming Conventions

### AI Agent Files
- **Instructions**: `{agent-name}-instructions.md` (e.g., `sidney-instructions.md`)
- **Memory**: `{agent-name}-memory-{type}.md` (e.g., `sidney-memory-technical.md`)
- **Templates**: `template-{role}.md` (e.g., `template-coding-partner.md`)

### Prompts
- **Descriptive names**: `{purpose}-prompt.md` (e.g., `email-newsletter-prompt.md`)
- **Kebab-case**: Use hyphens for word separation

### Documentation
- **README files**: Always `README.md` or `{agent-name}-README.md`
- **Markdown format**: All documentation uses `.md` extension

## Agent Configuration Architecture

### SimTheory Integration Pattern

**Single Instruction File** + **Multiple Memory Files**

#### Design Principles
1. **Instructions** = HOW the agent behaves (generic, reusable)
2. **Memory** = WHAT the agent knows about user (specific, contextual)

#### Loading Strategy
- **Always Load**: `{agent}-instructions.md`
- **Conditional Load**: Memory files based on query type

#### Example Loading Patterns

**Sidney (Tech Assistant)**
- Email task: instructions + workflow memory
- Coding help: instructions + technical + workflow memory
- macOS question: instructions + macos memory

**Mel (Life Assistant)**
- Personal task: instructions + personal + workflow memory
- Family planning: instructions + personal memory
- Travel planning: instructions + personal + workflow memory

## Memory File Organization

### Types of Memory Files
1. **Personal** - Identity, family, interests, location
2. **Technical** - Tech stack, tools, development environment
3. **Workflow** - Email/calendar rules, coding preferences
4. **Platform** - OS-specific guidance (macOS, Windows)

### Memory Metadata Headers
```yaml
---
version: 1.0
last_updated: YYYY-MM-DD
memory_type: [personal|technical|workflow|platform]
user: {username}
assistant: {agent-name}
priority: [high|medium|low]
---
```

## Best Practices

### Creating New Prompts
1. **Use descriptive filenames** that indicate purpose
2. **Include context** and examples in the prompt
3. **Version prompts** that undergo significant changes
4. **Test prompts** with target LLM before committing

### Configuring Agents
1. **Separate behavior from context** - instructions vs memory
2. **Keep instructions generic** for reusability
3. **Make memory specific** with user details
4. **Use metadata headers** for SimTheory integration
5. **Document loading strategy** in README files

### Git Workflow
1. **Commit related changes together** (e.g., instruction + memory updates)
2. **Use descriptive commit messages** explaining what changed and why
3. **Keep sensitive information out** of version control
4. **Update documentation** when structure changes

### File Maintenance
1. **Update `last_updated` field** in metadata when editing
2. **Version major changes** (increment version number)
3. **Archive outdated files** to backup directory
4. **Remove duplicates** promptly

## Token Optimization

### Memory File Sizing
- **Instructions**: ~800-1000 tokens
- **Personal Memory**: ~300-500 tokens  
- **Technical Memory**: ~400-500 tokens
- **Workflow Memory**: ~400 tokens
- **Platform Memory**: ~300 tokens

### Loading Efficiency
- Load only relevant memory files per query
- Combine independent memories when needed
- Avoid loading all memories simultaneously

## Future Considerations

As the library grows, consider adding:

- **`/prompts/`** - Organized by category (coding, writing, analysis)
- **`/agents/`** - Additional agent configurations beyond SimTheory
- **`/templates/`** - More generic templates for different use cases
- **`/examples/`** - Real-world examples and case studies
- **`/testing/`** - Prompt testing results and comparisons
- **Version control** for prompts (v1, v2 directories)

## Maintenance Guidelines

### Regular Reviews
- Review and update agent memories quarterly
- Archive outdated prompts
- Test prompts with latest LLM versions
- Update documentation for structural changes

### Quality Standards
- All prompts should be tested before merging
- Documentation should be clear and comprehensive
- Metadata headers should be complete and accurate
- Commit messages should explain the "why" not just "what"

This structure provides a maintainable foundation for managing AI agent configurations and prompt libraries while ensuring scalability and ease of use.
