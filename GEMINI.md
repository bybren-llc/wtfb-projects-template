# WTFB Project - Gemini CLI Instructions

> This file provides guidance to Google's Gemini CLI for this creative project.

## Project Overview

This is a WTFB (Words To Film By) creative project. Check `.wtfb/project.json` for project type (screenplay, novel, film-production).

## Multi-Agent Harness

This project uses an 11-agent team for collaborative development. See `AGENTS.md` for the complete team reference.

### Loading Agents
@.gemini/agents/story-analyst.md
@.gemini/agents/story-architect.md
@.gemini/agents/dialogue-writer.md
@.gemini/agents/scene-writer.md
@.gemini/agents/scene-annotator.md
@.gemini/agents/continuity-editor.md
@.gemini/agents/script-supervisor.md
@.gemini/agents/standards-reviewer.md
@.gemini/agents/research-specialist.md
@.gemini/agents/production-coordinator.md
@.gemini/agents/session-manager.md

### Loading Skills
@.gemini/skills/fountain-syntax.md
@.gemini/skills/story-structure.md
@.gemini/skills/dialogue-craft.md
@.gemini/skills/scene-analysis.md
@.gemini/skills/continuity-tracking.md

## Project Structure

```
├── *.fountain           # Main screenplay (if screenplay project)
├── manuscript/          # Novel content (if novel project)
├── sourcematerials/     # Research, references, images
├── exports/             # Generated outputs (PDF, FDX, HTML)
├── templates/           # Beat sheets, character registries
├── patterns/            # Reusable structural patterns
├── docs/                # Project documentation
├── marketing/           # Marketing materials and config
└── .gemini/             # This harness
    ├── agents/          # 11 specialized agent profiles
    ├── commands/        # Slash command definitions (TOML)
    └── skills/          # Knowledge base modules
```

## Available Commands

| Command | Purpose |
|---------|---------|
| `/start-scene` | Begin new scene development |
| `/check-format` | Validate Fountain syntax |
| `/check-continuity` | Verify consistency |
| `/analyze-structure` | Review narrative structure |
| `/export-pdf` | Generate PDF output |
| `/scene-list` | List all scenes |
| `/page-count` | Calculate page estimation |
| `/new-character` | Add a new character |

## Git Workflow

### Branch Patterns
- `scene/{slug}` - Single scene work
- `revision/{type}` - Full-script passes
- `character/{name}` - Character-focused work
- `structure/{change}` - Reorganization
- `fix/{issue}` - Targeted fixes
- `export/{format}` - Export preparation

### Commit Format
```
type(scope): description

Types: scene, dialogue, action, structure, revision, character, notes, format, docs, chore
```

## Validation Requirements

Before committing:
1. `/check-format` - Format validation must pass
2. `/check-continuity` - Consistency verified
3. Spell check passes
4. Self-review completed

## Agent Invocation

Invoke agents by role:
```
Acting as the Story Architect, evaluate the three-act structure...
Acting as the Dialogue Writer, refine the voice for [character]...
Acting as the Continuity Editor, verify timeline consistency...
```

## Quality Gates

The Script Supervisor controls quality gates:
- Pre-commit validation
- PR merge requirements
- Export readiness

The Story Architect has stop-the-line authority for structural issues.

## See Also

- `AGENTS.md` - Complete agent team reference
- `.gemini/README.md` - Harness documentation
- `docs/WORKFLOW.md` - Full workflow documentation
- `docs/CONTRIBUTING.md` - Contribution guidelines
