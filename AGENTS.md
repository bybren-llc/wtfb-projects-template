# Agent Team Reference

This project uses an 11-agent team for collaborative creative development.

## Team Structure

```
┌─────────────────────────────────────────────────────────────────┐
│                        SESSION MANAGER                          │
│                    (Coordination & Workflow)                    │
└─────────────────────────────────────────────────────────────────┘
                                │
        ┌───────────────────────┼───────────────────────┐
        │                       │                       │
        ▼                       ▼                       ▼
┌───────────────┐     ┌───────────────┐     ┌───────────────┐
│ STORY &       │     │ WRITING       │     │ QUALITY &     │
│ STRUCTURE     │     │               │     │ CONTINUITY    │
├───────────────┤     ├───────────────┤     ├───────────────┤
│ Story Analyst │     │ Dialogue      │     │ Continuity    │
│ Story         │     │   Writer      │     │   Editor      │
│   Architect*  │     │ Scene Writer  │     │ Script        │
│               │     │ Scene         │     │   Supervisor* │
│               │     │   Annotator   │     │ Standards     │
│               │     │               │     │   Reviewer    │
└───────────────┘     └───────────────┘     └───────────────┘
                                                    │
                              ┌─────────────────────┘
                              ▼
                    ┌───────────────┐
                    │ RESEARCH &    │
                    │ PRODUCTION    │
                    ├───────────────┤
                    │ Research      │
                    │   Specialist  │
                    │ Production    │
                    │   Coordinator │
                    └───────────────┘

* Has veto/gate authority
```

## Agent Profiles

### Story & Structure

| Agent | Role | Authority |
|-------|------|-----------|
| **Story Analyst** | Break down concepts into scene-by-scene analysis | Domain |
| **Story Architect** | Define and validate narrative structure | **VETO** (structure) |

### Writing

| Agent | Role | Authority |
|-------|------|-----------|
| **Dialogue Writer** | Create distinct character voices and subtext | Domain |
| **Scene Writer** | Handle visual storytelling and action | Domain |
| **Scene Annotator** | Manage notes, synopses, organization | Domain |

### Quality & Continuity

| Agent | Role | Authority |
|-------|------|-----------|
| **Continuity Editor** | Track chronology and consistency | Domain |
| **Script Supervisor** | Verify format and syntax | **GATE** (quality) |
| **Standards Reviewer** | Ensure industry-standard compliance | Domain |

### Research & Production

| Agent | Role | Authority |
|-------|------|-----------|
| **Research Specialist** | Handle accuracy and authenticity | Domain |
| **Production Coordinator** | Manage exports and delivery | Domain |
| **Session Manager** | Initialize sessions, coordinate tasks | Workflow |

## Invocation Patterns

### Direct Invocation
```
Acting as the Story Architect, evaluate the three-act structure of this screenplay.
```

### Task-Based Routing
The Session Manager routes tasks to appropriate agents based on context:
- Scene writing → Scene Writer
- Dialogue polish → Dialogue Writer
- Format check → Script Supervisor
- Export → Production Coordinator

### Multi-Agent Collaboration
Complex tasks may involve multiple agents:
```
Story Analyst → Story Architect → Scene Writer → Continuity Editor
```

## Authority Levels

### Domain Authority
Agent has expertise and decision-making power within their specialty.

### Gate Authority (Script Supervisor)
Controls quality checkpoints:
- Pre-commit validation
- PR merge requirements
- Export readiness verification

### Veto Authority (Story Architect)
Can halt work when:
- Structure is fundamentally broken
- Plot logic fails
- Story lacks clear direction

## Equal Voice Principle

Within their domains, all agents have equal voice:
- Each agent's expertise is respected
- Cross-domain discussions welcome collaboration
- Veto authority used sparingly and with justification

## See Also

- `.claude/agents/` - Claude agent definitions
- `.gemini/agents/` - Gemini agent definitions
- `CLAUDE.md` - Claude Code instructions
- `GEMINI.md` - Gemini CLI instructions
