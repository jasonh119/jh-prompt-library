# Sidney - AI Tech Assistant

**Version:** 2.0  
**Last Updated:** November 30, 2025  
**Platform:** SimTheory

---

## Overview

Sidney is an AI assistant designed to provide personal assistance and coding partnership support. The assistant is configured through a single instruction file and multiple memory context files optimized for SimTheory's architecture.

---

## File Structure

```
simtheory/
├── sidney-README.md                # This file
├── sidney-instructions.md          # Core behavioral directives (REQUIRED)
└── Memory Files (load conditionally):
    ├── sidney-memory-personal.md   # Personal life, interests, family
    ├── sidney-memory-technical.md  # Tech stack, development environment
    ├── sidney-memory-workflow.md   # Email, calendar, coding rules
    └── sidney-memory-macos.md      # Platform-specific guidance
```

---

## File Descriptions

### **sidney-instructions.md** (Required - Always Load)
- **Purpose:** Defines Sidney's core behavior, personality, and operating modes
- **Contains:** Identity, interaction guidelines, operational modes (Personal Assistant, Coding Partner)
- **Type:** Generic behavioral directives (not user-specific)
- **Token Estimate:** ~800-1000 tokens

### **sidney-memory-personal.md** (Conditional Load)
- **Purpose:** User's personal context and life details
- **Contains:** Location, family, interests, hobbies, business, travel patterns
- **Load When:** Personal questions, lifestyle topics, scheduling around personal events
- **Token Estimate:** ~300 tokens

### **sidney-memory-technical.md** (Conditional Load)
- **Purpose:** User's technical expertise and development environment
- **Contains:** Tech stack, programming languages, tools, AI/ML focus, learning areas
- **Load When:** Coding questions, technical troubleshooting, development tasks
- **Token Estimate:** ~500 tokens

### **sidney-memory-workflow.md** (Conditional Load)
- **Purpose:** Operational rules and user-specific preferences
- **Contains:** Email/calendar rules, coding preferences, communication style
- **Load When:** Email tasks, calendar management, workflow automation
- **Token Estimate:** ~400 tokens

### **sidney-memory-macos.md** (Conditional Load)
- **Purpose:** Platform-specific guidance for macOS
- **Contains:** Keyboard shortcuts, terminal usage, app preferences, learning needs
- **Load When:** macOS-specific questions, OS navigation, system configuration
- **Token Estimate:** ~300 tokens

---

## Loading Strategy for SimTheory

### Always Load
- `sidney-instructions.md`

### Conditional Loading (Based on Query Type)

| Query Type | Memory Files to Load |
|------------|---------------------|
| **Email Management** | workflow |
| **Calendar/Scheduling** | workflow, personal |
| **Coding/Development** | technical, workflow |
| **Personal Questions** | personal |
| **macOS Help** | macos, (technical if dev-related) |
| **General Tech Support** | technical |

### Example Combinations

**"Read my emails and summarize"**
- Load: instructions + workflow

**"Help me debug this Python code"**
- Load: instructions + technical + workflow

**"What are my weekend plans?"**
- Load: instructions + personal + workflow

**"How do I take a screenshot on macOS?"**
- Load: instructions + macos

---

## Operating Modes

### Mode 1: Personal Assistant
- Email management (Gmail & Outlook)
- Calendar scheduling
- Task reminders
- Communication drafting

### Mode 2: Coding Partner
- Code review and debugging
- Architecture guidance
- Best practices
- Technology research

---

## Key Features

### Communication Style
- Addresses user by name (from memory context)
- Comprehensive, detailed responses
- Multiple source validation
- Step-by-step guidance
- Collaborative problem-solving

### Privacy & Security
- Discretion with personal information
- Privacy-first recommendations
- Local/self-hosted solution preference

### Learning Support
- Hands-on practical examples
- Clear explanations for new concepts
- Multiple information sources
- Video resources when relevant

---

## Maintenance Guidelines

### Updating User Information
1. **Personal changes** → Edit `sidney-memory-personal.md`
2. **Tech stack changes** → Edit `sidney-memory-technical.md`
3. **Workflow/preference changes** → Edit `sidney-memory-workflow.md`
4. **macOS-related changes** → Edit `sidney-memory-macos.md`

### Updating Behavior
- **Only edit** `sidney-instructions.md` for behavioral changes
- Keep user-specific facts OUT of instructions

### Version Control
- Update `last_updated` field in file metadata
- Increment version number for major changes
- Commit with descriptive messages

---

## Token Optimization

### Total Token Usage by Scenario

| Scenario | Files Loaded | Approx. Tokens |
|----------|--------------|----------------|
| Email task | instructions + workflow | ~1,200 |
| Coding help | instructions + technical + workflow | ~1,900 |
| Personal query | instructions + personal | ~1,100 |
| macOS help | instructions + macos | ~1,100 |
| Full context | all files | ~2,400 |

---

## Design Principles

### Separation of Concerns
- **Instructions** = HOW Sidney behaves (universal)
- **Memory** = WHAT Sidney knows about user (specific)

### Benefits
1. **Scalability:** Same instructions can serve multiple users
2. **Maintainability:** Update facts without touching behavior
3. **Token Efficiency:** Load only relevant context
4. **Clarity:** Clear separation of behavior vs. data
5. **Version Control:** Independent versioning of behavior and context

---

## Metadata Headers

All files include metadata for SimTheory integration:

```yaml
---
version: 1.0
last_updated: 2025-11-30
type: [instructions|memory]
memory_type: [personal|technical|workflow|platform]
user: Jas
priority: [high|medium|low]
auto_apply: [email,calendar,coding]
---
```

---

## Future Enhancements

### Potential Additional Memory Files
- `sidney-memory-preferences.md` - UI/UX preferences, notification settings
- `sidney-memory-contacts.md` - Frequent contacts, relationship context
- `sidney-memory-projects.md` - Active projects, goals, milestones
- `sidney-memory-windows.md` - Windows 11 platform-specific guidance

### Conditional Logic
- Time-based context loading (work hours vs. personal time)
- Location-based preferences
- Task history for pattern recognition

---

## Support & Contact

**User:** Jas  
**Email:** jason.ai@thehelbigs.net  
**Repository:** jh-prompt-library  
**Assistant Platform:** SimTheory

---

## Changelog

### Version 2.0 (2025-11-30)
- Restructured from monolithic files to modular architecture
- Separated instructions from memory contexts
- Created 4 domain-specific memory files
- Added metadata headers for SimTheory integration
- Enabled conditional memory loading
- Deleted obsolete files (memory-base.md, memory-tech-assistant.md)

### Version 1.0 (Previous)
- Initial implementation with combined instruction/memory files
- Single instruction file with embedded user context
