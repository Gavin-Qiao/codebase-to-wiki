# Codebase to Wiki

A skill for AI coding agents that converts codebases into structured Obsidian wikis through human-in-the-loop iterative refinement.

<p align="center">
  <a href="https://agentskills.io/"><img src="https://img.shields.io/badge/Agent_Skills-v1.0-7c3aed" alt="Agent Skills"></a>
  <a href="./LICENSE"><img src="https://img.shields.io/badge/License-GPL--3.0-blue" alt="License"></a>
</p>

---

## Overview

Codebase to Wiki transforms arbitrary codebases into navigable Obsidian knowledge graphs. It operates through three distinct modes:

| Mode | Description |
|------|-------------|
| **Fresh** | Plan wiki structure collaboratively from scratch |
| **Midway** | Continue from tracked progress after interruption |
| **Debug** | Diagnose and fix issues in existing wikis |

The skill enforces human-in-the-loop checkpoints at every decision point, ensuring the generated documentation reflects accurate domain understanding rather than automated guesswork.

---

## Features

- **User-defined hierarchy** with nested depth (not constrained to 3 levels)
- **Mandatory Mermaid graphs** at non-atomic levels for visual navigation
- **Index paragraphs** with embedded wikilinks for composable narratives
- **Four node types** to represent different documentation patterns:
  - `code-bound` - 1:1 mapping to file/function/class
  - `code-spanning` - Concepts across multiple files
  - `conceptual` - Architecture, math, design patterns
  - `external` - Third-party dependencies
- **Incremental persistence** via `.wiki-progress.md` for graceful recovery
- **Optional test coverage** documentation per-module or per-node

---

## Installation

Clone the repository to your agent's skills directory:

```bash
git clone https://github.com/Gavin-Qiao/codebase-to-wiki.git /path/to/skills/codebase-to-wiki
```

Or add as a submodule:

```bash
git submodule add https://github.com/Gavin-Qiao/codebase-to-wiki.git /path/to/skills/codebase-to-wiki
```

---

## Directory Structure

```
codebase-to-wiki/
├── SKILL.md                       # Agent skill instructions
├── LICENSE                        # GPL-3.0
├── README.md                      # This file
└── references/
    ├── templates.md               # Frontmatter schemas and note templates
    └── mermaid-patterns.md        # Diagram patterns and conventions
```

---

## Usage

The skill activates when users request codebase documentation or wiki creation. Common triggers include:

- "Create a wiki for this codebase"
- "Document this project structure"
- "Generate Obsidian notes for this repository"
- "Continue documenting where we left off"
- "Fix broken links in my wiki"

### Generated Wiki Structure

```
wiki-root/
├── HOME.md                    # Codebase overview with mermaid graph
├── .wiki-progress.md          # Progress tracking (hidden)
├── ModuleA/
│   ├── ModuleA.md             # Module narrative with index paragraph
│   ├── Component.md           # Atomic node
│   └── SubModule/
│       ├── SubModule.md       # Sub-narrative
│       └── Function.md        # Granular node
└── ModuleB/
    └── ...
```

---

## Compatibility

This skill is designed for AI coding agents that support the [Agent Skills](https://agentskills.io/) specification. Tested with:

- Claude Code
- Gemini CLI
- Other agentic coding tools with skills support

### Requirements

- File system access for reading codebases and writing wiki files
- Markdown rendering capability
- Mermaid diagram support (for generated graphs)

---

## Anti-Patterns

This skill should **NOT** be used for:

- Code under active development (documents will become stale)
- Generated or minified code
- Vendor directories (`node_modules`, `vendor`, etc.)
- During major refactoring efforts
- When API reference docs (Swagger, TypeDoc) are the actual need

---

## References

| Resource | Description |
|----------|-------------|
| [SKILL.md](./codebase-to-wiki/SKILL.md) | Complete agent instructions |
| [templates.md](./codebase-to-wiki/references/templates.md) | Frontmatter schemas for all node types |
| [mermaid-patterns.md](./codebase-to-wiki/references/mermaid-patterns.md) | Diagram conventions and examples |
| [Agent Skills Spec](https://agentskills.io/specification) | Format specification |

---

## Author

**Mohan Qiao**

---

## License

This project is licensed under the **GNU General Public License v3.0** - see the [LICENSE](./LICENSE) file for details.
