# WTFB Projects Template

<p align="center">
  <a href="https://github.com/bybren-llc/wtfb-projects-template/releases/latest">
    <img src="https://img.shields.io/github/v/release/bybren-llc/wtfb-projects-template?include_prereleases&style=flat-square&color=blue" alt="Version">
  </a>
  <a href="https://github.com/bybren-llc/wtfb-projects-template/blob/main/LICENSE">
    <img src="https://img.shields.io/github/license/bybren-llc/wtfb-projects-template?style=flat-square" alt="License">
  </a>
  <a href="https://github.com/bybren-llc/wtfb-projects-template/actions/workflows/validate.yml">
    <img src="https://img.shields.io/github/actions/workflow/status/bybren-llc/wtfb-projects-template/validate.yml?style=flat-square&label=validation" alt="Validation">
  </a>
  <a href="https://github.com/bybren-llc/wtfb-projects-template/stargazers">
    <img src="https://img.shields.io/github/stars/bybren-llc/wtfb-projects-template?style=flat-square" alt="Stars">
  </a>
</p>

<p align="center">
  <strong>Multi-AI harness template for creative projects</strong><br>
  Screenplay | Novel | Film Production
</p>

<p align="center">
  <a href="#features">Features</a> •
  <a href="#quick-start">Quick Start</a> •
  <a href="#ai-harness">AI Harness</a> •
  <a href="#documentation">Documentation</a> •
  <a href="#contributing">Contributing</a>
</p>

---

## Features

| Feature | Description |
|---------|-------------|
| **Multi-AI Support** | Claude Code, Gemini CLI, OpenAI Codex |
| **11-Agent Team** | Specialized agents for every aspect of creative development |
| **30+ Commands** | Workflow, writing, analysis, and export commands |
| **17 Patterns** | Story structure, scene, dialogue, and character patterns |
| **Upstream Sync** | Weekly template updates via GitHub Actions |
| **Validation Stack** | Fountain syntax, Markdown lint, spell check |
| **Marketing Ready** | WTFB platform, GitHub Pages, commerce integration |

---

## Quick Start

### Option 1: GitHub Template

```bash
# Create a new repository from this template
gh repo create my-screenplay --template bybren-llc/wtfb-projects-template --clone
cd my-screenplay

# Initialize project
./scripts/init-project.sh my-screenplay screenplay

# Install dependencies
npm install
```

### Option 2: Clone Directly

```bash
git clone https://github.com/bybren-llc/wtfb-projects-template.git my-project
cd my-project
./scripts/init-project.sh my-project screenplay
npm install
```

### Install Plugin (Claude Code)

```bash
/plugin install wtfb-screenwriting@github.com/bybren-llc/wtfb-claude-marketplace/plugins/screenwriting
```

---

## AI Harness

### Agent Team

| Agent | Role | Authority |
|-------|------|-----------|
| **Story Architect** | Structure & beat placement | VETO (structure) |
| **Story Analyst** | Scene-by-scene analysis | Domain |
| **Dialogue Writer** | Character voice & subtext | Domain |
| **Scene Writer** | Visual storytelling | Domain |
| **Continuity Editor** | Timeline & consistency | Domain |
| **Script Supervisor** | Format compliance | GATE (quality) |
| **Standards Reviewer** | Industry standards | Domain |
| **Research Specialist** | Accuracy & authenticity | Domain |
| **Production Coordinator** | Exports & delivery | Domain |
| **Session Manager** | Workflow coordination | Workflow |
| **Scene Annotator** | Notes & organization | Domain |

### Commands

**Workflow:** `/start-scene`, `/end-session`, `/check-format`, `/check-continuity`, `/stuck`

**Writing:** `/new-scene`, `/new-character`, `/format-dialogue`, `/add-transition`

**Analysis:** `/analyze-character`, `/analyze-structure`, `/scene-list`, `/page-count`, `/arc-check`

**Export:** `/export-pdf`, `/export-fdx`, `/export-html`, `/export-all`

**WTFB Methodology:** `/writers-room`, `/theme-discovery`, `/story-check`, `/power-analysis`

---

## Project Structure

```
your-project/
├── .claude/              # Claude Code harness (via plugin)
├── .gemini/              # Gemini CLI harness
├── .wtfb/                # Project configuration
│   ├── project.json      # Type, plugins, sync settings
│   └── ai-harness/       # Multi-AI instructions
├── patterns/             # Story, scene, dialogue, character patterns
├── templates/            # Beat sheets, registries, worksheets
├── docs/                 # WORKFLOW.md, CONTRIBUTING.md
├── exports/              # Generated PDF, FDX, HTML
├── sourcematerials/      # Research, references
├── marketing/            # Platform integration
└── your-screenplay.fountain
```

---

## Documentation

| Document | Description |
|----------|-------------|
| [CLAUDE.md](CLAUDE.md) | Claude Code instructions |
| [GEMINI.md](GEMINI.md) | Gemini CLI instructions |
| [AGENTS.md](AGENTS.md) | Full agent team reference |
| [docs/WORKFLOW.md](docs/WORKFLOW.md) | Git workflow guide |
| [docs/CONTRIBUTING.md](docs/CONTRIBUTING.md) | Contribution guidelines |

---

## Validation

```bash
# Run all validation
npm run validate

# Individual checks
npm run lint:fountain    # Fountain syntax
npm run lint:md          # Markdown lint
npm run lint:spell       # Spell check
```

---

## Branch Strategy

| Branch | Purpose |
|--------|---------|
| `main` | Stable drafts only |
| `draft/v1`, `draft/v2` | Major versions |
| `scene/[name]` | Scene-specific work |
| `revision/[type]` | Revision passes |
| `character/[name]` | Character development |

---

## Contributing

See [CONTRIBUTING.md](docs/CONTRIBUTING.md) for guidelines.

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'feat: add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## Related Repositories

| Repository | Description |
|------------|-------------|
| [wtfb-claude-marketplace](https://github.com/bybren-llc/wtfb-claude-marketplace) | Plugin system for Claude Code |
| [seoul-identity](https://github.com/bybren-llc/seoul-identity) | Example screenplay project |

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- [Fountain](https://fountain.io/) - Markup syntax for screenwriting
- [Claude Code](https://claude.ai/claude-code) - Anthropic's CLI for Claude
- [Gemini CLI](https://github.com/google-gemini/gemini-cli) - Google's CLI for Gemini

---

<p align="center">
  <strong>Words To Film By</strong><br>
  <a href="https://wordstofilmby.com">Website</a> •
  <a href="mailto:dev@wordstofilmby.com">Contact</a> •
  <a href="https://wordstofilmby.com/projects/wtfb-projects-template/sponsor">Sponsor</a>
</p>

<p align="center">
  <sub>Built with the WTFB Multi-AI Harness</sub>
</p>
