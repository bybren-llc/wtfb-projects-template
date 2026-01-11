# WTFB Capability Contract Specification

Version: 1.0.0
Status: MVP

## Purpose

This document defines how WTFB capabilities (skills, commands, hooks, agents) are identified, versioned, and extended across the template and marketplace ecosystem.

## Canonical Identifier: `wtfbId`

Every WTFB capability has a **canonical identifier** (`wtfbId`) that uniquely identifies it across the ecosystem.

### Format

```
{namespace}:{capability-name}
```

### Namespace Assignment

| Source | Namespace | Example |
|--------|-----------|---------|
| Template (OSS) | `wtfb:` | `wtfb:story-structure` |
| Marketplace Screenwriting | `wtfb-screenwriting:` | `wtfb-screenwriting:advanced-structure` |
| Marketplace Novel | `wtfb-novel:` | `wtfb-novel:chapter-pacing` |
| Marketplace Film Production | `wtfb-film-production:` | `wtfb-film-production:call-sheet` |

### Requirement by Capability Type

| Capability | wtfbId Required? | Rationale |
|------------|------------------|-----------|
| Skills | **REQUIRED** | Primary extension point; all skills need registry identity |
| Commands | **RECOMMENDED** | Required only if they participate in replace/extend semantics |
| Hooks | **OPTIONAL** | Only if you need policy selection or analytics |
| Agents | **OPTIONAL** | MVP: agents are add-only, not replaced; useful for analytics |

### Filesystem Safety

- The `name:` field remains kebab-case and matches the directory name
- The `wtfbId:` field contains the namespace (`:` is allowed in YAML strings)
- No changes to directory structure are required

## Capability Contract

Every **marketplace** capability must declare a relationship type. Template capabilities do not need a relationship type (they are the baseline).

### Relationship Types (exactly one required)

| Type | Meaning | When to Use |
|------|---------|-------------|
| `provides` | New capability with no template dependency | Premium-only features not in template |
| `extends` | Additive enhancement (safe to run alongside base) | Enhanced version that adds to template capability |
| `replaces` | Explicit override (only one active at a time) | Premium version that supersedes template capability |

### Compatibility Gates (optional)

These fields are optional and can be combined with any relationship type:

| Field | Purpose | Example |
|-------|---------|---------|
| `requires` | Hard dependencies on other capabilities | Another plugin's skill must be installed |
| `compat` | Version ranges for compatibility | Template version, plugin version, harness version |

## Schema Definition

### Template Capability (Skill Example)

```yaml
---
name: story-structure
wtfbId: wtfb:story-structure
description: Three-act screenplay structure with beat placement.
---
# Story Structure

(skill content)
```

### Marketplace Capability: `provides`

New capability with no template dependency.

```yaml
---
name: showrunner-workflow
wtfbId: wtfb-screenwriting:showrunner-workflow
description: Professional showrunner workflow for TV writers' rooms.

# Relationship type (exactly one required)
provides: true                    # Boolean form (preferred)
# OR
provides: {}                      # Object form (also valid)

# Optional compatibility gates
compat:
  template: ">=1.0.0 <2.0.0"
  plugin: ">=1.0.0"
---
# Showrunner Workflow

(skill content)
```

### Marketplace Capability: `extends`

Additive enhancement that works alongside the template capability.

```yaml
---
name: advanced-structure
wtfbId: wtfb-screenwriting:advanced-structure
description: |
  Advanced screenplay structure workflow layered on top of base.
  Includes beat diagnostics, scene-to-beat mapping, rewrite recommendations.

# Relationship type (exactly one required)
extends:
  wtfbId: wtfb:story-structure    # Points to template wtfbId

# Optional compatibility gates
compat:
  template: ">=1.0.0 <2.0.0"
  plugin: ">=1.0.0 <2.0.0"
---
# Advanced Structure

## What This Adds Beyond Baseline
- Beat diagnostics (variance thresholds + severity)
- Scene to beat mapping table
- Rewrite plan recommendations by act/sequence
```

### Marketplace Capability: `replaces`

Explicit override that supersedes the template capability.

```yaml
---
name: story-structure-pro
wtfbId: wtfb-screenwriting:story-structure-pro
description: |
  Replaces baseline story structure with professional-grade version.
  More diagnostics, tighter outputs, clearer rewrite directives.

# Relationship type (exactly one required)
replaces:
  wtfbId: wtfb:story-structure    # Points to template wtfbId

# Optional compatibility gates
compat:
  template: ">=1.0.0 <2.0.0"
  plugin: ">=1.0.0 <2.0.0"
---
# Story Structure Pro

When selected, this skill is used instead of the template version.
```

### With Dependencies

```yaml
---
name: production-rewrite
wtfbId: wtfb-screenwriting:production-rewrite
description: Production-level rewrite workflow with beat tracking.

extends:
  wtfbId: wtfb:rewriting-methodology

# Optional: requires other capabilities
requires:
  - wtfbId: wtfb-screenwriting:beat-diagnostics

compat:
  template: ">=1.0.0 <2.0.0"
  plugin: ">=1.0.0"
  harness: ">=0.9.0"
---
```

## Precedence Control

### Configuration Location

Precedence policy is owned by the project in `.wtfb/project.json`:

```json
{
  "plugins": {
    "installed": ["wtfb-screenwriting", "wtfb-film-production"],
    "precedence": ["wtfb-screenwriting", "wtfb-film-production"]
  }
}
```

### Selection Rules

1. **Template always loads first** (foundation layer)
2. **Plugins load in precedence order** (or installation order if not specified)
3. **Contract type determines behavior**:
   - `provides`: new capability added to registry
   - `extends`: both base and enhanced available; orchestrator may prefer enhanced
   - `replaces`: premium supersedes base when plugin is enabled
4. **Later in precedence wins** if multiple plugins provide the same capability

### Fallback Behavior

- If `precedence` array is missing: use installation order
- If compatibility check fails: skip that capability, log warning

## Override Policy by Capability Type (MVP)

| Capability | extends | replaces | Notes |
|------------|---------|----------|-------|
| Skills | Allowed | Allowed | Primary monetization lane |
| Commands | Allowed | Prefer parallel | Add premium commands alongside base |
| Hooks | Minimal | Minimal | Keep minimal and reviewable |
| Agents | Add new only | Not allowed | Do not replace template agents for MVP |

## Validation Rules

### Required Checks

1. **Schema validation**: All skills must have `wtfbId: wtfb:*` or `wtfbId: {plugin}:*`
2. **Contract validation**: Marketplace capabilities must have exactly one of `provides`, `extends`, or `replaces`
3. **No duplicate wtfbId**: Each wtfbId must be unique within a plugin
4. **Reference validation**: `extends.wtfbId` and `replaces.wtfbId` must reference existing template capabilities

### Invalid Combinations

```yaml
# INVALID: Multiple relationship types
extends:
  wtfbId: wtfb:story-structure
replaces:
  wtfbId: wtfb:dialogue-craft
```

```yaml
# INVALID: Missing relationship type (for marketplace capabilities)
name: advanced-structure
wtfbId: wtfb-screenwriting:advanced-structure
description: ...
# No provides/extends/replaces declared
```

## Third-Party Plugin Author Rules

To enable multiple marketplaces to coexist without conflicts, third-party plugin authors must follow these rules:

### Namespace Uniqueness (Required)

Every third-party plugin must use a unique namespace prefix in `wtfbId`:

| Context | wtfbId Format | Example |
|---------|---------------|---------|
| Template hub | `wtfb:{name}` | `wtfb:story-structure` |
| Official WTFB plugins | `wtfb-{plugin}:{name}` | `wtfb-screenwriting:advanced-structure` |
| Third-party plugins | `{vendor}:{name}` | `acme-writing:custom-beats` |

**Reserved namespaces** (do not use):
- `wtfb:` - Template hub only
- `wtfb-screenwriting:` - Official WTFB plugin
- `wtfb-novel-writing:` - Official WTFB plugin
- `wtfb-film-production:` - Official WTFB plugin

### Relationship Contract (Required for Marketplace)

Every marketplace skill that touches a template capability must declare exactly one of:
- `provides` - New capability not in template
- `extends` - Builds on template capability
- `replaces` - Supersedes template capability

### Compatibility Gates (Recommended)

Include `compat.template` semver range on all marketplace skills:

```yaml
compat:
  template: ">=1.0.0 <2.0.0"
```

### Collision Resolution

If two plugins extend/replace the same hub `wtfbId`:
- Winner determined by `.wtfb/project.json` `plugins.precedence`
- Later in array wins
- Plugin authors must not assume they always win

### CI Scope

- **Template CI**: Enforces hub rules only (`wtfb:` + skill compliance)
- **Marketplace CI**: Enforces spoke rules (`{plugin}:` + relationship fields + compat)

## Reference

- [Claude Code Plugin Overview](https://deepwiki.com/anthropics/claude-plugins-official/1-overview)
- [WTFB User Access Tiers](./USER_ACCESS_TIERS.md)
- [WTFB Plugin Architecture](./PLUGIN_ARCHITECTURE.md)
