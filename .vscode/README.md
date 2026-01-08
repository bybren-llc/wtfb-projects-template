# .vscode Directory

This directory contains VS Code workspace configuration for optimal WTFB project development.

## Files

```
.vscode/
├── README.md          # This file
├── extensions.json    # Recommended extensions
└── settings.json      # Workspace settings
```

## extensions.json

Defines recommended VS Code extensions for the team.

### Recommended Extensions

| Extension | Purpose |
|-----------|---------|
| **Better Fountain** | Fountain screenplay syntax highlighting, preview, PDF export |
| **Code Spell Checker** | Spell checking for all text files |
| **markdownlint** | Markdown linting and formatting |
| **Markdown All in One** | Markdown editing enhancements |
| **Prettier** | Code formatting |
| **GitLens** | Enhanced git integration |
| **GitHub Pull Requests** | PR management from VS Code |

### Installing Extensions

When you open the project in VS Code:
1. A notification appears: "This workspace has extension recommendations"
2. Click "Install All" to install recommended extensions
3. Or press `Cmd/Ctrl+Shift+X`, filter by `@recommended`

### Adding Extensions

To recommend additional extensions:

```json
{
  "recommendations": [
    "existing.extension",
    "new.extension-id"
  ]
}
```

Find extension IDs in the VS Code marketplace or by right-clicking an installed extension.

## settings.json

Workspace-specific VS Code settings that apply to everyone working on the project.

### Key Settings

#### Editor Settings
```json
{
  "editor.formatOnSave": true,    // Auto-format when saving
  "editor.wordWrap": "on",        // Wrap long lines
  "editor.rulers": [80, 100],     // Visual guides at 80 and 100 chars
  "files.autoSave": "afterDelay", // Auto-save after 1 second
  "files.trimTrailingWhitespace": true
}
```

#### Spell Checker
```json
{
  "cSpell.customDictionaries": {
    "project-words": {
      "name": "project-words",
      "path": "${workspaceFolder}/.cspell/project-words.txt",
      "addWords": true
    }
  }
}
```

The spell checker uses a project-specific dictionary at `.cspell/project-words.txt`. Add character names, locations, and custom terms there.

#### Fountain Settings
```json
{
  "fountain.general.sceneNumbering": true,
  "fountain.pdf.scene_numbers": "right",
  "fountain.pdf.print_title_page": true,
  "[fountain]": {
    "editor.wordWrap": "on",
    "editor.lineNumbers": "on"
  }
}
```

Better Fountain extension settings for screenplay display and export.

#### Markdown Settings
```json
{
  "[markdown]": {
    "editor.wordWrap": "on",
    "editor.quickSuggestions": {
      "other": true,
      "comments": false,
      "strings": false
    }
  },
  "markdownlint.config": {
    "MD013": false,  // Allow long lines
    "MD033": false,  // Allow inline HTML
    "MD041": false   // Allow non-H1 first heading
  }
}
```

#### Git Settings
```json
{
  "git.enableSmartCommit": true,
  "git.autofetch": true
}
```

## User vs Workspace Settings

| Setting Type | Location | Scope |
|--------------|----------|-------|
| User | `~/.config/Code/User/settings.json` | All projects |
| Workspace | `.vscode/settings.json` | This project only |

Workspace settings **override** user settings. This ensures consistency across the team.

## Adding to .gitignore

Some teams exclude `.vscode/`:
```gitignore
.vscode/
```

We **include** `.vscode/` because:
- Consistent experience across team
- Recommended extensions help onboarding
- Workspace settings ensure formatting consistency
- No sensitive data in these files

If you need local overrides, create `.vscode/settings.local.json` (gitignored).

## Customization

### Per-User Overrides

For personal preferences that shouldn't affect the team:

1. Open Command Palette (`Cmd/Ctrl+Shift+P`)
2. "Preferences: Open User Settings"
3. Add your personal overrides

### Per-Project Additions

To add project-specific settings:

1. Edit `.vscode/settings.json`
2. Add new settings
3. Commit the change

**Caution:** Avoid settings that might not work for all team members (paths, OS-specific settings).

## Extension-Specific Setup

### Better Fountain

After installing:
1. Open a `.fountain` file
2. Preview: `Cmd/Ctrl+Shift+V`
3. Export PDF: `Cmd/Ctrl+Shift+P` → "Fountain: Export PDF"

### Code Spell Checker

To add words to dictionary:
1. Hover over underlined word
2. Click "Quick Fix" or `Cmd+.`
3. Select "Add to workspace dictionary"

Words are saved to `.cspell/project-words.txt`.

### GitLens

Features enabled by default:
- Line blame annotations
- File history
- Commit graph

Customize in VS Code settings under "GitLens".

## Troubleshooting

**Extensions not installing:**
- Check internet connection
- Try manual install from marketplace
- Verify extension ID is correct

**Settings not applying:**
- Reload window: `Cmd/Ctrl+Shift+P` → "Reload Window"
- Check for JSON syntax errors
- Verify file is in `.vscode/` (not root)

**Fountain preview not working:**
- Ensure Better Fountain is installed
- File must have `.fountain` extension
- Try reopening the file

**Spell checker ignoring custom words:**
- Verify `.cspell/project-words.txt` exists
- Check path in settings.json
- Reload window
