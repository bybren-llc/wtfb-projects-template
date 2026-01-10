---
description: Generate a Final Draft XML file from the Fountain screenplay.
---

# /export-fdx

Generate a Final Draft XML file from the Fountain screenplay.

## Arguments
- `[output]` - Optional: Output filename (default: auto-generated)

## Workflow

### Step 1: Pre-Export Validation
Run format validation:
- Check Fountain syntax
- Note potential compatibility issues
- Verify elements will transfer

### Step 2: Execute Export

#### Recommended: VS Code + Better Fountain Extension

The easiest method uses the [Better Fountain](https://marketplace.visualstudio.com/items?itemName=piersdeseilligny.betterfountain) extension:

1. Open your `.fountain` file in VS Code
2. Press `Ctrl+Shift+P` (or `Cmd+Shift+P` on macOS)
3. Type "Fountain: Export to FDX"
4. Choose output location

> **Extension Link**: [Better Fountain on VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=piersdeseilligny.betterfountain)

#### Alternative: CLI Tools (for automation)

For CI/CD pipelines or scripted exports, use screenplain (Python):

```bash
# One-time installation (requires Python 3.8+ and pipx)
pipx install screenplain

# Export to FDX
screenplain --format fdx screenplay.fountain exports/fdx/output.fdx
```

> **Note**: `afterwriting` only supports PDF export, not FDX. Use Better Fountain or screenplain for FDX.

#### macOS: Highland 2

[Highland 2](https://quoteunquoteapps.com/highland-2/) offers native FDX export:
- Open `.fountain` file in Highland 2
- File → Export → Final Draft

### Step 3: Verify Output
- Confirm file created
- Check file size
- Note any conversion warnings

### Step 4: Report Results

```markdown
## FDX Export Complete

📄 **File**: [filename].fdx
📊 **Size**: [X] KB
✅ **Status**: Success

### Compatibility Notes
[Any conversion issues or warnings]
```

## FDX Compatibility

### Elements That Transfer Well
- Scene headings
- Action/description
- Character names
- Dialogue
- Parentheticals
- Transitions

### Elements That May Not Transfer
- [[Notes]] - May be lost
- Sections (#) - May be lost
- Synopses (=) - May be lost
- Boneyard - May be lost or converted
- Some emphasis formatting

### Post-Import Review
After opening in Final Draft:
1. Check scene headings format
2. Verify dialogue alignment
3. Review any complex formatting
4. Check dual dialogue
5. Verify transitions

## Filename Convention

```
[Title]_v[Version]_[YYYYMMDD].fdx

Example:
Seoul_Identity_v1.0_20251227.fdx
```

## Use Cases

### Collaboration
When working with someone who uses Final Draft:
- Export FDX
- They import and work
- They export FDX
- You convert back or continue in FD

### Agency/Studio Request
Some recipients specifically request Final Draft format:
- Export FDX
- Verify formatting
- Deliver

### Backup Format
FDX is a standard interchange format:
- More portable than .fountain for some workflows
- Opens in multiple applications

## Example Output

```markdown
## FDX Export Complete

📄 **File**: Seoul_Identity_v1.0_20251227.fdx
📊 **Size**: 312 KB
✅ **Status**: Success

### Conversion Report
- Scenes: 62 ✓
- Characters: 8 ✓
- Dialogue blocks: 234 ✓

### Compatibility Notes
- 5 [[notes]] not transferred (Fountain-specific)
- 3 sections not transferred (Fountain-specific)
- All core elements converted successfully

### Recommended
After importing to Final Draft:
- Review scene heading formatting
- Check dual dialogue (scenes 15, 42)
- Verify transitions alignment
```

## Error Handling

### Common Issues
| Error | Cause | Fix |
|-------|-------|-----|
| Export fails | Syntax error | Run `/check-format` |
| Missing content | Conversion issue | Check source file |
| Wrong formatting | FDX limitation | Manual fix in FD |

## Success Criteria
- [ ] FDX file created
- [ ] Core elements converted
- [ ] Compatibility notes documented
- [ ] File opens in Final Draft (if available)
