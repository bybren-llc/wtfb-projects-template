# Workflow Guide

This document describes the complete workflow for WTFB creative projects.

## Branch Strategy

### Protected Branches

| Branch | Purpose | Protection |
|--------|---------|------------|
| `main` | Production-ready drafts | PR required, no direct pushes |
| `draft/v{N}` | Major versions (e.g., `draft/v1`) | PR required |
| `draft/v{N}-{qualifier}` | Named variants (e.g., `draft/v2-polish`) | PR required |

### Working Branches

Pattern: `type/kebab-case-description`

| Type | Purpose | Examples |
|------|---------|----------|
| `scene/{slug}` | Single scene or sequence | `scene/opening`, `scene/midpoint-reveal` |
| `revision/{type}` | Full-script revision pass | `revision/dialogue`, `revision/action` |
| `character/{name}` | Character-focused work | `character/protagonist-arc` |
| `structure/{change}` | Structural reorganization | `structure/reorder-act2` |
| `fix/{issue}` | Targeted fixes | `fix/continuity-sc15`, `fix/format` |
| `export/{format}` | Export preparation | `export/table-read`, `export/competition` |

**Naming rules:** Type prefix + 2-5 words in kebab-case. No special characters except hyphens.

## Workflow Lifecycle

### 1. Branch Creation

```bash
git checkout main  # or draft/v{N}
git pull origin main
git checkout -b scene/your-scene-name
```

Announce your work:
```
[Branch Created] scene/your-scene-name
From: main
Purpose: Write the opening coffee shop confrontation
Target: main
```

### 2. Work Phase

- Make atomic commits with standardized messages
- Push periodically: `git push -u origin scene/your-scene-name`
- Run validation: `/check-format` and `/check-continuity`

### 3. Pull Request

Create PR when ready:
```bash
gh pr create --base main --title "scene: add opening coffee shop confrontation"
```

Complete the PR checklist:
- [ ] Format validation passes
- [ ] Continuity check passes
- [ ] Spell check passes
- [ ] Self-review completed

### 4. Merge

- **Squash merge**: `scene/*`, `fix/*`, `export/*` (clean history)
- **Regular merge**: `revision/*`, `structure/*`, `character/*` (preserve history)

### 5. Cleanup

```bash
git branch -d scene/your-scene-name
git push origin --delete scene/your-scene-name
```

## Commit Message Format

Pattern: `type(scope): description`

### Types

| Type | Purpose |
|------|---------|
| `scene` | New or modified scene content |
| `dialogue` | Dialogue improvements |
| `action` | Action line changes |
| `structure` | Structural reorganization |
| `revision` | Revision pass changes |
| `character` | Character development |
| `notes` | Notes and annotations |
| `format` | Formatting fixes |
| `docs` | Documentation updates |
| `chore` | Maintenance tasks |

### Examples

- `scene(act1): add opening coffee shop sequence`
- `dialogue(protagonist): polish voice in apartment scenes`
- `fix(continuity): correct timeline in scenes 15-18`
- `revision(action): tighten action lines throughout`
- `structure(act2): reorder midpoint sequence`

## Definition of Done

### All Branches

- [ ] `/check-format` passes
- [ ] `/check-continuity` passes
- [ ] Spell check passes
- [ ] Self-review completed

### By Branch Type

| Branch | Additional Requirements |
|--------|------------------------|
| `scene/*` | Scene has clear purpose, advances plot or reveals character |
| `revision/*` | Full script impact assessed, changes documented |
| `character/*` | Character voice consistent throughout script |
| `structure/*` | Structure analysis run, pacing verified |
| `fix/*` | Issue demonstrably fixed, no regressions |
| `export/*` | Export generates successfully, reviewed for errors |
| `draft/*` → `main` | Full validation + ready for external delivery |

## Quick Decision Tree

**Writing new content?**
- Single scene → `scene/{slug}`
- Full revision pass → `revision/{type}`
- Character-focused → `character/{name}`

**Improving existing?**
- Dialogue polish → `revision/dialogue`
- Action tightening → `revision/action`
- Character work → `character/{name}`
- Reorganizing → `structure/{change}`

**Fixing problems?**
- Format issues → `fix/format-{desc}`
- Continuity errors → `fix/continuity-{desc}`
- General bugs → `fix/{issue}`

**Preparing for export?**
- Table read → `export/table-read`
- Competition → `export/competition`
- General → `export/{purpose}`

## Validation Commands

```bash
npm run validate        # Full validation suite
npm run lint:fountain   # Fountain syntax only
npm run lint:md         # Markdown linting
npm run lint:spell      # Spell check
```

## Agent Team

See `AGENTS.md` for the complete 11-agent team reference:
- Story & Structure: Story Analyst, Story Architect
- Writing: Dialogue Writer, Scene Writer, Scene Annotator
- Quality: Continuity Editor, Script Supervisor, Standards Reviewer
- Production: Research Specialist, Production Coordinator, Session Manager

## See Also

- `CONTRIBUTING.md` - Contribution guidelines
- `AGENTS.md` - Agent team reference
- `CLAUDE.md` - Claude Code instructions
- `GEMINI.md` - Gemini CLI instructions
