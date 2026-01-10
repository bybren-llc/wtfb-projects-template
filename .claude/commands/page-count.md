---
description: Estimate the current page count and runtime.
---

# /page-count

Estimate the current page count and runtime.

## Arguments
- `[detail]` - Optional: `summary`, `full`, `by-act`

## Workflow

### Step 1: Count Elements
- Total lines of content
- Number of scenes
- Dialogue vs. action ratio

### Step 2: Calculate Pages
Using standard estimation:
- ~55-60 lines per page (action)
- ~35-40 lines per page (dialogue-heavy)
- Account for scene headings, transitions

### Step 3: Estimate Runtime
```
Pages × Genre Factor = Runtime (minutes)
```

Genre factors:
- Action: 0.85-0.95
- Comedy: 1.0
- Drama: 1.0-1.1
- Thriller: 0.9-1.0

### Step 4: Generate Report

## Output Modes

### Summary (Default)
```markdown
## Page Count: [TITLE]

📄 **Pages**: ~[X]
⏱️ **Runtime**: ~[Y] minutes ([Z] hours)
🎬 **Scenes**: [N]

**Target**: [target pages] | **Status**: [over/under/on target]
```

### Full Detail
```markdown
## Page Count: [TITLE]

### Summary
- **Estimated Pages**: [X]
- **Estimated Runtime**: [Y] minutes
- **Total Scenes**: [Z]

### Composition
| Element | Count | % of Script |
|---------|-------|-------------|
| Action | [lines] | [%] |
| Dialogue | [lines] | [%] |
| Scene Headings | [count] | - |
| Transitions | [count] | - |

### By Act
| Act | Pages | % | Target |
|-----|-------|---|--------|
| One | [X] | [%] | 25% |
| Two | [X] | [%] | 50% |
| Three | [X] | [%] | 25% |

### Page Distribution
| Pages | Scene Count | Avg Length |
|-------|-------------|------------|
| 1-25 | [X] | [Y] pages |
| 26-55 | [X] | [Y] pages |
| 56-85 | [X] | [Y] pages |
| 86-end | [X] | [Y] pages |

### Target Comparison
- **Target**: [X] pages
- **Current**: [Y] pages
- **Variance**: [+/-Z] pages
- **Status**: [✓ On target / ⚠️ Over / ⚠️ Under]
```

### By Act
```markdown
## Page Count by Act: [TITLE]

### Act One (Setup)
- Pages: [X]-[Y] ([Z] pages)
- Scenes: [N]
- Target: 25% | Actual: [%]

### Act Two (Confrontation)
- Pages: [X]-[Y] ([Z] pages)
- Scenes: [N]
- Target: 50% | Actual: [%]

### Act Three (Resolution)
- Pages: [X]-[Y] ([Z] pages)
- Scenes: [N]
- Target: 25% | Actual: [%]
```

## Runtime Calculation

### Formula
```
Runtime = Pages × (1.0 - Action_Adjustment)
```

Where Action_Adjustment accounts for:
- Heavy action sequences: -5 to -15%
- Heavy dialogue: +0 to +10%

### Output
```markdown
### Runtime Estimate
- **Pages**: [X]
- **Genre**: [type]
- **Adjustment**: [factor]
- **Estimated Runtime**: [Y] minutes
- **Formatted**: [H]h [M]m
```

## Example Output

```markdown
## Page Count: Seoul Identity

📄 **Pages**: ~98
⏱️ **Runtime**: ~95 minutes (1h 35m)
🎬 **Scenes**: 62

**Target**: 100-110 pages | **Status**: ✓ On target

### Composition
| Element | Count | % |
|---------|-------|---|
| Action | 1,842 lines | 42% |
| Dialogue | 2,534 lines | 58% |
| Scenes | 62 | - |

### By Act
| Act | Pages | Actual | Target |
|-----|-------|--------|--------|
| One | 24 | 24% | 25% ✓ |
| Two | 50 | 51% | 50% ✓ |
| Three | 24 | 24% | 25% ✓ |
```

## Success Criteria
- [ ] Page count estimated
- [ ] Runtime calculated
- [ ] Act proportions shown
- [ ] Target comparison provided
- [ ] Composition breakdown included
