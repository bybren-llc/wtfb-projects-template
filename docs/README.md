# Docs Directory

This directory contains project documentation, version archives, and development notes.

## Directory Structure

```
docs/
├── README.md              # This file
├── CONTRIBUTING.md        # Contribution guidelines
├── v1-original/           # Version 1 archive (protected)
│   └── .gitkeep
├── v2-development/        # Version 2 development (protected)
│   └── .gitkeep
└── [custom-docs]/         # Your project-specific documentation
```

## Purpose

The docs directory serves multiple purposes:

1. **Version Archives**: Preserve complete snapshots of major versions
2. **Development Notes**: Track creative decisions and research
3. **Collaboration**: Shared documentation for team members
4. **Production Reference**: Information for production teams

## Version Archives Pattern

WTFB projects use a versioned archive pattern inspired by professional screenwriting:

### v1-original/
The first complete version of your project. Once you move to v2, this becomes **read-only historical reference**.

**What to include:**
- Complete screenplay/manuscript file
- Beat sheet at time of completion
- Character registry
- Treatment
- Research notes
- Any supporting documents

**Why keep it:**
- Reference for how the story evolved
- Comparison for revision analysis
- Fallback if v2 goes wrong
- Historical documentation

### v2-development/
Current active development. This is where work happens.

**What to include:**
- Working documents and notes
- Scene-by-scene development files
- Research in progress
- Collaboration notes (writers room sessions)
- Continuity reports

### Adding More Versions

When completing a major revision:

```bash
# Archive current development
mv docs/v2-development docs/v2-final

# Create new development folder
mkdir docs/v3-development

# Copy relevant files forward
cp docs/v2-final/continuity_report.md docs/v3-development/
```

## Protected Paths

The `docs/v*/**` pattern is in `protectedPaths` in `.wtfb/project.json`. This means:

- Template syncs will **never** overwrite your version archives
- Your documentation is safe from automated updates
- You have full control over documentation content

## Recommended Documentation

### For Screenplays

```
docs/
├── v1-original/
│   ├── screenplay-v1.fountain
│   ├── beat-sheet-v1.md
│   ├── treatment-v1.md
│   └── research/
├── v2-development/
│   ├── scenes/
│   │   ├── scene_01_opening.fountain
│   │   └── scene_02_catalyst.fountain
│   ├── continuity_report.md
│   ├── character-deep-dives/
│   │   └── protagonist-analysis.md
│   └── writers-room-notes/
│       └── session-2026-01-08.md
└── research/
    ├── technical-accuracy.md
    └── reference-films.md
```

### For Novels

```
docs/
├── v1-original/
│   ├── manuscript-v1.md
│   ├── outline-v1.md
│   └── world-bible-v1.md
├── v2-development/
│   ├── chapter-notes/
│   ├── timeline-deep-dive.md
│   └── beta-reader-feedback/
└── world/
    ├── magic-system.md
    ├── geography.md
    └── history.md
```

### For Film Production

```
docs/
├── pre-production/
│   ├── location-reports/
│   ├── casting-notes/
│   └── department-breakdowns/
├── production/
│   ├── daily-logs/
│   └── problem-resolution/
└── post-production/
    ├── edit-notes/
    └── vfx-tracking/
```

## CONTRIBUTING.md

This file provides guidelines for contributors:

- How to get started
- Branch naming conventions
- Commit message format
- Code of conduct
- Validation requirements

**Customize it** for your project's specific needs and team norms.

## AI Integration

When AI assistants analyze your project, they may reference documentation:

- **Writers Room sessions** create notes in `docs/v2-development/`
- **Research Specialist** outputs go to `docs/research/`
- **Continuity Editor** updates `docs/v2-development/continuity_report.md`

You can direct AI to specific documentation:
```
Look at docs/v2-development/writers-room-notes/ for previous creative decisions
```

## Best Practices

1. **Archive completely**: When archiving a version, include everything needed to understand it standalone

2. **Date your notes**: Include dates in filenames or headers
   ```
   writers-room-2026-01-08.md
   ```

3. **Link between documents**: Reference related docs
   ```markdown
   See [character analysis](./character-deep-dives/protagonist.md) for more detail.
   ```

4. **Use consistent naming**:
   - Lowercase with hyphens: `beat-sheet-v1.md`
   - Or lowercase with underscores: `beat_sheet_v1.md`
   - Pick one and stick with it

5. **Don't duplicate the screenplay**: Keep the canonical version at root, not in docs

6. **Review before archiving**: Clean up development docs before moving to archive

## Git Workflow

Documentation changes follow the same workflow as creative content:

```bash
# Create a docs branch
git checkout -b docs/add-research-notes

# Make changes
# ...

# Commit
git commit -m "docs: add technical accuracy research"

# Create PR or merge
git checkout main
git merge docs/add-research-notes
```

## Searching Documentation

Use grep or your IDE's search to find information:

```bash
# Find all mentions of a character
grep -r "PROTAGONIST_NAME" docs/

# Find all writers room notes
find docs/ -name "*writers-room*"
```
