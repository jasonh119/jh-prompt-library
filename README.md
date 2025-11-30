# jh-prompt-library

A curated collection of prompts, instructions, and configurations for LLM models and AI agents.

## 📋 Overview

This repository contains:
- **AI Agent Configurations** - Modular instructions and memory files for personalized AI assistants
- **Reusable Prompts** - Tested prompts for coding, analysis, and explanations
- **Templates** - Generic assistant templates for various use cases
- **Documentation** - Best practices for prompt engineering and agent configuration

## 🗂️ Repository Structure

```
jh-prompt-library/
├── simtheory/              # SimTheory AI agent configurations
│   ├── sidney-*            # Tech assistant (instructions + memory files)
│   ├── mel-*               # Life assistant (instructions + memory files)
│   └── template-*          # Generic assistant templates
├── general-prompt/         # Reusable prompts
│   ├── email-newsletter-prompt.md
│   ├── explaination-prompt.md
│   └── explaination-prompt-snipets.md
└── .github/                # Repository documentation
    └── github-instructions.md
```

## 🤖 AI Agents

### Sidney - Tech Assistant
**Purpose:** Coding partnership and technical assistance  
**Architecture:** 1 instruction file + 4 memory files (personal, technical, workflow, macOS)  
**Use Cases:** Code review, debugging, email management, technical research

### Mel - Life Assistant  
**Purpose:** Personal life management and family coordination  
**Architecture:** 1 instruction file + 2 memory files (personal, workflow)  
**Use Cases:** Family planning, travel coordination, health & wellness, business guidance

### Templates
- `template-coding-partner.md` - Generic programming assistant
- `template-personal-assistant.md` - Generic personal assistant
- `template-project-manager.md` - Generic project manager

## 📝 Prompts

### Explanation Prompt
**File:** `general-prompt/explaination-prompt.md`  
**Purpose:** Generate Feynman-style explanations with clarity, intuition, and analogies  
**Features:** Simplifies complex topics, includes references and video sources

### Email Newsletter Analysis
**File:** `general-prompt/email-newsletter-prompt.md`  
**Purpose:** Extract and analyze top stories from newsletters  
**Features:** Strategic scoring, research validation, competitive analysis

### Prompt Enhancement Snippets
**File:** `general-prompt/explaination-prompt-snipets.md`  
**Purpose:** Meta-prompts to improve AI responses  
**Includes:** Self-assessment, justification requests, expert-level guidance

## 🏗️ Architecture

### SimTheory Pattern
**1 Instruction File** (behavior) + **Multiple Memory Files** (context)

#### Design Principles
- **Instructions** = HOW the agent behaves (generic, reusable)
- **Memory** = WHAT the agent knows (user-specific, contextual)
- **Conditional Loading** = Load only relevant memories per query

#### Benefits
- Token efficiency (load only what's needed)
- Maintainability (separate behavior from context)
- Scalability (same instructions for multiple users)
- Version control (independent versioning)

## 🚀 Usage

### For AI Agent Configuration
1. Choose base template or existing agent
2. Customize instructions for behavior
3. Create memory files for user context
4. Load conditionally based on query type

### For Prompts
1. Browse `general-prompt/` directory
2. Copy prompt template
3. Customize for your use case
4. Test with target LLM

### Memory File Types
- **Personal** - Identity, family, interests, location
- **Technical** - Tech stack, development environment
- **Workflow** - Email/calendar rules, preferences
- **Platform** - OS-specific guidance (macOS, Windows)

## 📊 Token Optimization

| Component | Token Count |
|-----------|-------------|
| Instructions | ~800-1000 |
| Personal Memory | ~300-500 |
| Technical Memory | ~400-500 |
| Workflow Memory | ~400 |
| Platform Memory | ~300 |

**Example:** Coding help query loads ~1,900 tokens (instructions + technical + workflow)

## 📚 Documentation

- **`.github/github-instructions.md`** - Comprehensive project structure guide
- **`simtheory/sidney-README.md`** - Complete Sidney configuration documentation
- **Memory Headers** - Metadata in YAML format for SimTheory integration

## 🛠️ Development Tools

- **IDEs:** VS Code, Windsurf)
- **AI Assistants:** GitHub Copilot, Claude, Gemini
- **Platforms:** SimTheory for agent deployment
- **Languages:** Python, JavaScript, Tailwind CSS

## 📖 Best Practices

### Creating Prompts
- Use descriptive filenames
- Include examples and context
- Test before committing
- Version significant changes

### Configuring Agents
- Separate behavior from context
- Keep instructions generic
- Make memory user-specific
- Use metadata headers
- Document loading strategy

### Git Workflow
- Commit related changes together
- Write descriptive commit messages
- Keep sensitive info out of version control
- Update docs when structure changes

## 🔒 License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details.

## 📮 Contact

**Author:** jasonh119@github  
**Repository:** [github.com/jasonh119/jh-prompt-library](https://github.com/jasonh119/jh-prompt-library)

## ✅ Todos
- [ ] Add Windsurf-specific prompts
- [ ] Add GitHub Copilot prompts
- [ ] Add more template variations
- [ ] Document prompt testing methodology
