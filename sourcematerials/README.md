# Source Materials Directory

This directory contains research, reference documents, and source materials that inform your creative project. These files provide context and accuracy for your work.

## Directory Structure

```
sourcematerials/
├── README.md          # This file
├── .gitkeep           # Preserves empty directory
└── [your materials]   # Research docs, PDFs, images, etc.
```

## Purpose

Source materials serve several purposes:

1. **Research**: Background information for authenticity
2. **Reference**: Documents you're adapting or inspired by
3. **Context**: AI assistants can reference these for accuracy
4. **Documentation**: Record of your research process

## What to Include

### Research Documents

- Historical records
- Technical documentation
- Interview transcripts
- News articles
- Academic papers

### Visual References

- Location photos
- Character inspiration images
- Period reference imagery
- Mood boards

### Audio/Video

- Interview recordings
- Documentary clips
- Reference performances
- Music inspiration

### Adaptation Sources

- Original works being adapted
- Rights documentation
- Previous versions

## File Organization

Organize by category or topic:

```
sourcematerials/
├── research/
│   ├── historical-context.md
│   ├── technical-accuracy/
│   │   ├── military-procedure.pdf
│   │   └── legal-research.md
│   └── interviews/
├── visual-reference/
│   ├── locations/
│   ├── characters/
│   └── period/
├── adaptation/
│   └── original-source.pdf
└── INDEX.md           # Master list of materials
```

## Gitignore Configuration

Large files are gitignored by default:

```gitignore
# From .gitignore
sourcematerials/*.pdf
sourcematerials/*.doc
sourcematerials/*.docx
```

**Why gitignore:**
- PDFs and docs can be large (megabytes)
- May have copyright restrictions
- Not needed for code review
- Can be shared via other means

**What IS tracked:**
- Markdown notes and summaries
- INDEX.md and organization files
- Small text files
- .gitkeep placeholders

## Creating an INDEX.md

Track your source materials with an index:

```markdown
# Source Materials Index

## Research Documents

| File | Description | Date Added | Status |
|------|-------------|------------|--------|
| `military-procedure.pdf` | Navy JAG court procedures | 2026-01-08 | Reviewed |
| `breathalyzer-law.md` | California DUI interlock laws | 2026-01-05 | In progress |

## Visual Reference

| File | Description | Source |
|------|-------------|--------|
| `bar-reference-01.jpg` | Dive bar interior | Personal photo |
| `uniform-reference.png` | Navy dress uniform | Wikipedia |

## Not Included (Local Only)

| Description | Reason |
|-------------|--------|
| Full book PDF | Copyright - keep local |
| Raw interview audio | Privacy - summarized in notes |
```

## AI Integration

AI assistants can reference source materials for accuracy:

```
# Example prompt
Check my military dialogue against sourcematerials/research/military-procedure.pdf
```

**WTFB Chunking Pattern:**

For large documents, chunk them for AI processing:

```
sourcematerials/
└── wtfb-chunks/
    ├── INDEX.md
    ├── source-chunk-01-pages-1-25.txt
    ├── source-chunk-02-pages-26-50.txt
    └── source-chunk-03-pages-51-75.txt
```

This pattern (from racoon-rescue) makes large references AI-accessible.

## Protected Path

`sourcematerials/**` is in `protectedPaths` in `.wtfb/project.json`. This means:

- Template syncs will **never** touch your source materials
- Your research is safe from automated updates
- Full control over what's included

## Best Practices

### 1. Document Your Sources

For each source, note:
- Where it came from
- When you accessed it
- How it's relevant
- Any copyright considerations

### 2. Summarize Large Documents

Create markdown summaries of PDFs:

```markdown
# Summary: Military Court Procedure

Source: sourcematerials/military-procedure.pdf

## Key Points

1. Court martial proceedings differ from civilian court...
2. JAG officers serve as both prosecution and defense...

## Relevant Quotes

> "The accused has the right to..." (p. 45)

## Notes for Project

- Our scene needs to show X
- Character would know Y
- Technical term is "Z"
```

### 3. Respect Copyright

- Don't commit copyrighted PDFs to public repos
- Note licensing for everything
- Use quotes/excerpts fairly
- Get permissions for adaptation

### 4. Organize by Project Phase

```
sourcematerials/
├── pre-writing/       # Initial research
├── development/       # Active reference
└── production/        # Production-specific (locations, etc.)
```

### 5. Keep It Relevant

Remove materials that are no longer needed. Archive if unsure:

```bash
# Archive old research
mv sourcematerials/old-research.pdf ~/project-archives/
```

## Research Workflow

### Starting a Project

1. Create initial research questions
2. Gather source materials
3. Create INDEX.md
4. Summarize key documents
5. Chunk large documents if needed

### During Development

1. Reference materials as you write
2. Add new sources as discovered
3. Update INDEX.md
4. Ask AI to verify accuracy

### For Production

1. Compile location reference
2. Gather visual references for departments
3. Document technical requirements
4. Create production-specific summaries

## Troubleshooting

**File too large for git:**
- Add to .gitignore
- Store locally or in cloud storage
- Create markdown summary for git

**Can't find a source:**
- Check INDEX.md
- Search with: `grep -r "keyword" sourcematerials/`
- Review git history if accidentally deleted

**AI can't read PDF:**
- Convert to text/markdown
- Use chunking pattern
- Provide relevant excerpts in prompt
