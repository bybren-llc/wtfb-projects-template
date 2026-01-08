# Gemini CLI Harness

This directory contains the multi-agent harness for Google's Gemini CLI.

## Structure

```
.gemini/
├── agents/          # 11 specialized agent profiles
├── commands/        # Slash command definitions (TOML)
├── skills/          # Knowledge base modules
├── README.md        # This file
├── SETUP.md         # Configuration instructions
└── TROUBLESHOOTING.md
```

## Agent Team

The harness coordinates 11 specialized agents organized into four functional areas:

### Story & Structure
- **Story Analyst** - Break down concepts into scene-by-scene analysis
- **Story Architect** - Define and validate narrative structure

### Writing
- **Dialogue Writer** - Create distinct character voices and subtext
- **Scene Writer** - Handle visual storytelling and action description
- **Scene Annotator** - Manage notes, synopses, and organization

### Quality & Continuity
- **Continuity Editor** - Track chronology and consistency
- **Script Supervisor** - Verify format and syntax
- **Standards Reviewer** - Ensure industry-standard compliance

### Research & Production
- **Research Specialist** - Handle accuracy and authenticity
- **Production Coordinator** - Manage exports and delivery
- **Session Manager** - Initialize sessions and coordinate tasks

## Usage

Agents are loaded via the root `GEMINI.md` file using imports:

```markdown
@.gemini/agents/story-analyst.md
@.gemini/skills/story-structure.md
```

## Commands

Available slash commands:

| Command | Purpose |
|---------|---------|
| `/start-scene` | Begin new scene development |
| `/check-format` | Validate format syntax |
| `/check-continuity` | Verify consistency |
| `/analyze-structure` | Review narrative structure |
| `/export-pdf` | Generate PDF output |

See `commands/` for full list.

## Customization

Add project-specific agents, commands, or skills by creating new files in the appropriate directories. Update `GEMINI.md` to import them.
