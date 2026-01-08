# AI Harness Directory

This directory contains portable AI instruction files that enable your project to work with multiple AI assistants: Claude, Gemini, Codex, and future systems.

## Philosophy

The WTFB AI Harness is designed around **AI portability**. Your creative project should work with any capable AI assistant, not be locked to a single provider.

### Core Principles

1. **Single Source of Truth**: `schema.json` defines capabilities; AI-specific files adapt it
2. **Graceful Degradation**: Each AI uses what it can, ignores what it can't
3. **Human Readable**: All files are Markdown/JSON for easy editing
4. **Version Controlled**: Changes tracked in git like any other code

## Files

### schema.json

The unified capability schema. This is the **canonical definition** of what AI assistants can do with your project.

```json
{
  "version": "1.0.0",
  "projectTypes": {
    "screenplay": {
      "format": "fountain",
      "mainFile": "*.fountain",
      "plugin": "wtfb-screenwriting"
    }
  },
  "capabilities": { ... },
  "agents": [ ... ],
  "commands": { ... },
  "resources": { ... }
}
```

**Sections:**

| Section | Purpose |
|---------|---------|
| `projectTypes` | Defines format and plugin per type |
| `capabilities` | What the AI can do (write, analyze, validate, export) |
| `agents` | Specialized roles available |
| `commands` | Available commands by project type |
| `resources` | File paths for templates, patterns, etc. |

### CLAUDE.md

Instructions for **Claude Code** (Anthropic's CLI tool).

**What it contains:**
- Project overview with type detection
- Full command reference organized by project type
- Fountain format reference (for screenplays)
- Repository structure guide
- Git workflow and commit conventions
- Validation instructions
- Plugin installation commands

**Special features for Claude:**
- Uses Claude Code's `/command` syntax
- References `.wtfb/project.json` for dynamic type detection
- Integrates with Claude Code plugins
- Supports Claude's multi-agent system via `/writers-room`

### GEMINI.md

Instructions for **Google Gemini**.

**Adapted for Gemini's style:**
- More structured capability mapping
- Table-based command reference
- Explicit file location documentation
- Clear output format requirements

**Key differences from Claude:**
- Less reliance on tool integration
- More explicit instruction format
- Focus on capability boundaries

### CODEX.md

Instructions for **OpenAI GPT/Codex** models.

**Adapted for OpenAI's style:**
- System context framing
- Command interface as tables
- Structured response format
- Validation checklist approach

**Key differences:**
- More prescriptive response structure
- Explicit acknowledgment patterns
- Step-by-step validation flow

## How AI Selection Works

When you use an AI with your project:

1. **Claude Code**: Reads `CLAUDE.md` (symlinked to root) automatically
2. **Gemini**: Point it to `.wtfb/ai-harness/GEMINI.md`
3. **GPT/Codex**: Include `.wtfb/ai-harness/CODEX.md` in context
4. **Other AIs**: Use `schema.json` as a reference

## Command Mapping

All AIs support the same core commands, but invocation differs:

| Action | Claude | Gemini/Codex |
|--------|--------|--------------|
| Start scene | `/start-scene desc` | `/start-scene desc` |
| Check format | `/check-format` | `/check-format` |
| Export PDF | `/export-pdf` | `/export-pdf` |

The command prefix `/` is universal. The AI reads the instruction file to understand what each command does.

## Adding Custom Commands

To add a project-specific command:

1. **Update schema.json:**
```json
{
  "commands": {
    "screenplay": [
      ...existing,
      {"name": "my-command", "args": "[arg]", "description": "What it does"}
    ]
  }
}
```

2. **Update each AI file** with the command documentation

3. **Implement the command** (if it requires tooling) in `scripts/`

## Agent System

The schema defines specialized agents:

```json
{
  "agents": [
    {
      "id": "story-architect",
      "role": "Structure and beat sheet design",
      "capabilities": ["structure", "scene-sequencing", "pacing"],
      "projectTypes": ["screenplay", "novel"]
    }
  ]
}
```

Different AIs use agents differently:
- **Claude**: Native agent support via plugins and `/writers-room`
- **Gemini/Codex**: Simulated via prompting (ask to "act as Story Architect")

## Extending for New AIs

To add support for a new AI system:

1. Create a new file: `NEW_AI.md`
2. Study the AI's instruction format
3. Adapt the content from existing files
4. Map commands and capabilities appropriately
5. Test with the new AI

**Template structure:**
```markdown
# NEW_AI.md - [AI Name] Integration

## Project Context
[How to introduce the project]

## Capabilities
[Reference to schema.json]

## Commands
[Format appropriate for this AI]

## Output Requirements
[What format to use for responses]
```

## Best Practices

1. **Keep files in sync**: Changes to capabilities should update ALL AI files
2. **Test with each AI**: Verify commands work as expected
3. **Document limitations**: Note when an AI can't do something
4. **Use schema.json as source**: AI files should derive from, not contradict, the schema
5. **Version together**: Bump schema version when making breaking changes

## Troubleshooting

**AI doesn't recognize a command:**
- Check that the command is in the AI's instruction file
- Verify the command is in schema.json
- Ensure the instruction file is in the AI's context

**AI uses wrong format:**
- Check the format reference section in the AI file
- Provide an example of correct format
- Reference existing files as examples

**AI ignores project type:**
- Ensure `.wtfb/project.json` has correct `projectType`
- Check that the AI file references project.json
- Explicitly state the project type in your prompt
