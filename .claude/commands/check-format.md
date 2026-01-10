---
description: Validate Fountain syntax and formatting.
---

# /check-format

Validate Fountain syntax and formatting.

## Arguments
- `[file]` - Optional: specific .fountain file (default: main screenplay)

## Workflow

### Step 1: Load Fountain File
- Identify target .fountain file
- Read complete file content

### Step 2: Syntax Validation

#### Title Page Check
```markdown
## Title Page
- [ ] Title present
- [ ] Author/Credit present
- [ ] Contact information
- [ ] Draft date (recommended)
```

#### Scene Headings Check
```markdown
## Scene Headings
Total: [X] scenes

Issues:
- Line [Y]: Missing time of day
- Line [Z]: Invalid prefix (should be INT/EXT)
```

#### Character/Dialogue Check
```markdown
## Character & Dialogue
Characters found: [X]

Issues:
- Line [Y]: Character without dialogue
- Line [Z]: Orphaned parenthetical
```

#### Element Check
```markdown
## Element Validation

| Element | Count | Issues |
|---------|-------|--------|
| Scene Headings | X | Y |
| Characters | X | Y |
| Dialogue Blocks | X | Y |
| Parentheticals | X | Y |
| Transitions | X | Y |
| Notes | X | Y |
```

### Step 3: Generate Report

```markdown
## Fountain Validation: [FILENAME]

### Status: [VALID / X ERRORS / Y WARNINGS]

### Errors (Must Fix)
[List breaking issues]

### Warnings (Should Review)
[List non-breaking issues]

### Statistics
- Pages: ~[X]
- Scenes: [Y]
- Characters: [Z]

### Ready for Export: [YES/NO]
```

## Common Issues Detected

### Errors (Blocking)
| Issue | Description | Fix |
|-------|-------------|-----|
| Bad scene heading | Doesn't start with INT/EXT | Add proper prefix |
| Orphaned dialogue | No character name | Add character |
| Broken dual dialogue | Missing ^ | Add ^ to second character |

### Warnings (Review)
| Issue | Description | Fix |
|-------|-------------|-----|
| Long action block | 5+ lines | Consider breaking up |
| Missing title page | No metadata | Add title page |
| Inconsistent names | JOHN vs JOHNNY | Standardize |

## Success Criteria
- [ ] All scenes have valid headings
- [ ] All dialogue has character names
- [ ] No orphaned elements
- [ ] Title page complete
- [ ] Export-ready status determined

## Example Output

```markdown
## Fountain Validation: seoul identity.fountain

### Status: 2 ERRORS / 1 WARNING

### Errors (Must Fix)
1. Line 45: Scene heading missing time of day
   Current: `INT. WAREHOUSE`
   Fix: `INT. WAREHOUSE - NIGHT`

2. Line 128: Orphaned parenthetical
   Current: `(beat)` with no following dialogue
   Fix: Add dialogue or convert to action

### Warnings (Should Review)
1. Line 89: Action block is 7 lines
   Consider: Break into shorter paragraphs

### Statistics
- Pages: ~45
- Scenes: 32
- Characters: 8 (speaking)

### Ready for Export: NO (fix errors first)
```
