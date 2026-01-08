# /export-html

Generate an HTML preview of the screenplay.

## Arguments
- `[output]` - Optional: Output filename (default: auto-generated)
- `[style]` - Optional: `screen`, `print`, `minimal`

## Workflow

### Step 1: Pre-Export Validation
- Check Fountain syntax
- Verify content is complete

### Step 2: Execute Export

#### Recommended: VS Code + Better Fountain Extension

The easiest method uses the [Better Fountain](https://marketplace.visualstudio.com/items?itemName=piersdeseilligny.betterfountain) extension:

1. Open your `.fountain` file in VS Code
2. Press `Ctrl+Shift+P` (or `Cmd+Shift+P` on macOS)
3. Type "Fountain: Export to HTML"
4. Choose output location

> **Extension Link**: [Better Fountain on VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=piersdeseilligny.betterfountain)

#### Alternative: CLI Tools (for automation)

For CI/CD pipelines or scripted exports:

```bash
# First-time setup
npm install -g afterwriting

# Export
afterwriting --source screenplay.fountain --html --output output.html
```

### Step 3: Verify Output
- Confirm file created
- Check renders in browser
- Verify formatting

### Step 4: Report Results

```markdown
## HTML Export Complete

📄 **File**: [filename].html
📊 **Size**: [X] KB
✅ **Status**: Success

Open in browser to preview.
```

## Style Options

### Screen (Default)
Optimized for on-screen reading:
- Responsive layout
- Comfortable reading width
- Dark mode support (if styled)

### Print
Optimized for printing from browser:
- Paper-sized pages
- Print margins
- Page breaks

### Minimal
Clean, minimal styling:
- Basic formatting
- Fast loading
- Easy to customize

## Use Cases

### Quick Preview
- Generate HTML
- Open in browser
- Review without PDF export

### Web Sharing
- Host HTML file
- Share URL with collaborators
- No special software needed

### Read on Device
- Transfer HTML to tablet/phone
- Read in browser
- Responsive formatting

## Filename Convention

```
[Title]_v[Version]_[YYYYMMDD].html

Example:
Seoul_Identity_v1.0_20251227.html
```

## Example Output

```markdown
## HTML Export Complete

📄 **File**: Seoul_Identity_v1.0_20251227.html
📊 **Size**: 156 KB
✅ **Status**: Success

### Preview
To view: Open file in web browser

### Features
- Responsive reading layout
- Proper screenplay formatting
- Print-friendly (Ctrl/Cmd + P)

### Notes
- [[Notes]] are hidden in output
- Sections not displayed
- Synopses not displayed
```

## Configuration

### HTML Options
```json
{
  "html_use_paper_size": true,
  "html_scenes_numbers": "none",
  "html_print_dialogue_numbers": false
}
```

## Error Handling

### Common Issues
| Error | Cause | Fix |
|-------|-------|-----|
| Export fails | Syntax error | Run `/check-format` |
| Bad formatting | CSS issue | Check style option |
| Won't open | Browser issue | Try different browser |

## Success Criteria
- [ ] HTML file created
- [ ] Opens in browser
- [ ] Formatting correct
- [ ] Readable on screen
