<!-- cspell:ignore Squibler Storywork Filmustage SIGGRAPH Codecademy Agentic underserved Collab Supv Anlst Annot NaviDoc toolkits -->
# Competitive Analysis: WTFB Multi-Agent Harness

> **Document Status**: Internal Analysis
> **Last Updated**: 2026-01-10
> **Authors**: WTFB Team

## Executive Summary

This analysis compares what we've built (WTFB) against the current market landscape of multi-agent AI frameworks and AI screenwriting tools.

---

## Market Categories Analyzed

### 1. Multi-Agent AI Frameworks

- CrewAI
- Microsoft AutoGen
- MetaGPT
- LangGraph/LangChain

### 2. AI Screenwriting Tools

- Squibler
- Storywork
- ScreenplayIQ (WriterDuet)
- Saga
- Arc Studio
- NolanAI/FinalBit

### 3. Multi-Agent Film Production

- FilmAgent (research project)
- Filmustage

### 4. Traditional Industry Software (Non-AI)

- Final Draft 13
- Movie Magic Screenwriter

---

## Competitive Matrix

### AI Tools Comparison

| Feature                  | WTFB              | CrewAI      | AutoGen        | MetaGPT      | AI Screenwriters |
| ------------------------ | ----------------- | ----------- | -------------- | ------------ | ---------------- |
| **Domain Focus**         | Screenwriting     | General     | General        | Software Dev | Screenwriting    |
| **Agent Specialization** | 11 craft experts  | Role-based  | Conversational | Dev team sim | Single AI        |
| **Authority/Veto**       | Yes (tiered)      | No          | No             | No           | No               |
| **Craft Knowledge**      | 24 skill modules  | None        | None           | SOPs only    | Varies           |
| **Pattern Library**      | 17+ patterns      | None        | None           | None         | None             |
| **Quality Gates**        | Script Supervisor | Manual      | Manual         | Manual       | Manual           |
| **Workflow Hooks**       | Automated         | Manual      | Manual         | Manual       | None             |
| **Export Formats**       | PDF/FDX/HTML      | N/A         | N/A            | Code         | Varies           |
| **CLI Tools**            | @wtfb/cli         | None        | None           | CLI          | None             |
| **Open Source**          | Yes               | Yes         | Yes            | Yes          | Mostly No        |
| **Multi-AI Support**     | Claude/Gemini     | LLM agnostic| LLM agnostic   | LLM agnostic | Proprietary      |

### Traditional vs AI-Enhanced Software

| Feature                  | WTFB                    | Final Draft 13 | Movie Magic |
| ------------------------ | ----------------------- | -------------- | ----------- |
| **AI Writing Assist**    | 11 agents               | None           | None        |
| **AI Analysis**          | Yes                     | None           | None        |
| **Industry Standard**    | Exports to .fdx         | Yes (.fdx)     | Partial     |
| **Production Tools**     | Export only             | Limited        | Excellent   |
| **Pricing**              | Free                    | $249.99        | $249.95     |
| **Open Source**          | Yes                     | No             | No          |
| **Platform**             | CLI + any editor        | Desktop app    | Desktop app |
| **Real-time Collab**     | VS Code Live Share      | Yes            | No          |
| **Extensibility**        | Full (OSS toolkits)     | Plugins only   | Limited     |
| **Marketplace**          | Community contributions | No             | No          |
| **Enterprise/Self-Host** | Yes (private workflows) | No             | No          |
| **File Format**          | Fountain (open)         | .fdx (closed)  | Proprietary |
| **Learning Curve**       | Moderate                | Low            | Low         |
| **Market Share**         | Emerging                | ~95%           | ~5%         |

---

## What Makes WTFB Distinct

### 1. Domain-Specific Multi-Agent (Rare Combination)

- **Market Gap**: General frameworks (CrewAI, AutoGen) are domain-agnostic
- **AI Screenwriters**: Single AI, no agent collaboration
- **WTFB**: Multi-agent + deep domain expertise

### 2. Authority/Veto Architecture (Unique)

- No other framework implements tiered authority with veto powers
- Story Architect can halt cascading structural failures
- Script Supervisor gates all deliverables
- This mirrors real Hollywood hierarchy

### 3. Encoded Craft Knowledge (Unique)

- 24 skill modules with professional methodologies
- Theophrastus character types, Save the Cat beats, Aristotle's 6 components
- Other tools rely on general LLM knowledge

### 4. Automated Workflow Enforcement (Rare)

- Git hooks enforce commit conventions
- Pre-commit validation prevents errors
- Session management tracks progress
- Most frameworks require manual discipline

### 5. Pattern Library (Unique in Category)

- Reusable scene patterns, dialogue techniques, structure templates
- Institutional memory across sessions
- No AI screenwriting tool offers this

### 6. Real-Time Collaboration via VS Code Live Share

- Microsoft's Live Share extension enables simultaneous editing
- Writers can collaborate in real-time on the same files
- Git-based versioning underneath for history and branching
- No proprietary lock-in like Final Draft's collaboration

### 7. Full Extensibility (Unique)

- **OSS Integration**: Google Gen AI Toolkit, LangChain, custom tools
- **Any AI Provider**: Claude, Gemini, OpenAI, local models
- **Custom Workflows**: Users can build their own agent workflows
- **Community Marketplace**: Submit tools/services to wtfb-app (free or paid)
- **Future-Proof**: As new AI tech emerges, community can integrate it
- Traditional tools (Final Draft, Movie Magic) have closed ecosystems

### 8. Enterprise Privacy & Self-Hosting (Unique)

- **Private Workflows**: Companies keep custom algorithms and workflows private
- **Self-Hosted Option**: Enterprise/cloud version for full data control
- **IP Protection**: Proprietary processes never leave your infrastructure
- **Compliance Ready**: Meet data residency and security requirements
- No AI screenwriting tool offers this level of enterprise control

### 9. Fountain Format: Open Standard Foundation

- **Cross-Device**: Plain text works everywhere (mobile, desktop, web)
- **Version Control Friendly**: Git diffs are meaningful, not binary blobs
- **Easy Integration**: Any AI service can read/write Fountain
- **App Ecosystem**: Simple to build new apps that integrate with WTFB
- **No Lock-In**: Your scripts are yours, forever portable
- Final Draft's .fdx is proprietary; Fountain is open and universal

---

## Closest Competitors (Deep Dive)

### FilmAgent (Academic Research - HITsz-TMG)

**What It Is:**

- Multi-agent framework for end-to-end film automation in 3D virtual spaces
- Published at SIGGRAPH Asia 2024, open source on GitHub

**Agent Roles (4 agents):**

- Director - Creative vision oversight
- Screenwriter - Dialogue and narrative
- Actors - Character-specific feedback
- Cinematographer - Camera shots and positioning

**Collaboration Strategies:**

- **Critique-Correct-Verify**: Sequential feedback loop
- **Debate-Judge**: Agents debate options, judge selects winner

**Three Stages:**

1. Idea Development
2. Scriptwriting & Cinematography
3. Execution in Unity 3D

**Key Limitations:**

- Requires pre-built 3D Unity environments (not generative)
- Focused on production/cinematography, not writing craft
- No authority/veto system
- Computationally expensive

**WTFB vs FilmAgent:**

| Aspect           | WTFB                | FilmAgent          |
| ---------------- | ------------------- | ------------------ |
| Agents           | 11 craft specialists| 4 production roles |
| Focus            | Writing craft       | 3D production      |
| Authority System | Veto + Gate         | Debate-Judge only  |
| Knowledge Base   | 24 skill modules    | None               |
| Output           | Screenplay files    | Unity 3D scenes    |
| Deployment       | CLI + Template      | Research prototype |

---

### CrewAI (Production Framework)

**What It Is:**

- Popular open-source multi-agent framework
- Flows (orchestration) + Crews (agent teams)

**Architecture:**

- **Flows**: State management, event-driven execution, conditional logic
- **Crews**: Teams of autonomous agents with specialized roles

**Agent Definition:**

- Specialized roles with goals and tools
- Autonomous decision-making
- Peer-level collaboration

**Authority System:**

- **None documented** - No veto, no hierarchy, no voting
- Agents collaborate as peers through autonomous coordination

**Domain Focus:**

- General-purpose: research, API handling, content generation, databases
- No built-in domain expertise

**WTFB vs CrewAI:**

| Aspect    | WTFB                   | CrewAI          |
| --------- | ---------------------- | --------------- |
| Domain    | Screenwriting-specific | General-purpose |
| Authority | Tiered (Veto/Gate)     | Flat/Peer       |
| Knowledge | 24 craft skill modules | None built-in   |
| Patterns  | 17+ reusable templates | None            |
| Hooks     | Automated workflow     | Manual          |
| CLI       | @wtfb/cli published    | None            |

---

### Storywork (Commercial Product)

**What It Is:**

- AI screenwriting platform
- "Never takes over creativity"

**Features:**

- AI-assisted writing workflow
- Cast AI voices to characters
- IP protection (no training on user content)

**Architecture:**

- Single AI assistant model
- No multi-agent collaboration

**WTFB Advantage:**

- 11 specialized agents vs single AI
- Open source vs proprietary
- Authority/quality gates vs manual review
- Pattern library vs ad-hoc generation

---

## Industry Standard Software (Non-AI)

### Final Draft 13 (2024)

**What It Is:**

- Industry standard screenwriting software since 1990
- Used by ~95% of Hollywood productions
- Latest version: Final Draft 13

**Features (Version 13):**

- **Navigator 2.0**: Improved scene overview and navigation
- **Focus Mode**: Distraction-free writing environment
- **Goal Setting**: Writing targets and tracking
- **Typewriter View**: Retro-style aesthetic option
- **SmartType**: Auto-complete for character names, locations
- **Real-Time Collaboration**: Multi-user editing
- **Beat Board**: Visual outlining tool

**AI Features:**

- **None significant** - Final Draft has not integrated generative AI
- SmartType is rule-based auto-complete, not AI
- No AI writing assistance, suggestions, or analysis

**File Format:**

- Proprietary .fdx (Final Draft XML)
- Industry standard for script submission

**Pricing:**

- $249.99 one-time purchase
- $99.99 upgrades

**WTFB vs Final Draft:**

| Aspect         | WTFB                  | Final Draft 13    |
| -------------- | --------------------- | ----------------- |
| AI Integration | 11 specialized agents | None              |
| Pricing        | Free (open source)    | $249.99           |
| Format         | Fountain (open)       | .fdx (proprietary)|
| Collaboration  | Git-based             | Real-time editing |
| Analysis Tools | AI-powered            | Manual only       |
| Export         | PDF/FDX/HTML          | PDF/FDX           |
| Platform       | CLI + any editor      | Desktop app only  |

**Key Insight**: Final Draft remains the submission standard but has not embraced AI. WTFB can export to .fdx format while providing AI-powered development tools.

---

### Movie Magic Screenwriter (2024)

**What It Is:**

- Professional screenwriting software
- Companion to Movie Magic Budgeting/Scheduling
- Strong in TV/episodic production environments

**Features:**

- **NaviDoc**: Scene navigation panel
- **Index Cards**: Visual outlining
- **Scene Properties**: Production metadata
- **Dual Dialogue**: Side-by-side character speech
- **Multi-column AV format**: Documentary/corporate support
- **Import/Export**: Multiple format support including Final Draft

**AI Features:**

- **None** - No AI integration announced
- No generative writing assistance
- No AI analysis tools

**Integration Strengths:**

- Seamless with Movie Magic Budgeting
- Seamless with Movie Magic Scheduling
- Production-oriented metadata

**Update Frequency:**

- Slow updates compared to competitors
- Focus on stability over innovation

**Pricing:**

- $249.95 one-time purchase
- Bundle discounts with other Movie Magic products

**WTFB vs Movie Magic Screenwriter:**

| Aspect           | WTFB                  | Movie Magic Screenwriter       |
| ---------------- | --------------------- | ------------------------------ |
| AI Integration   | 11 specialized agents | None                           |
| Pricing          | Free (open source)    | $249.95                        |
| Production Tools | Export only           | Budgeting/Scheduling integrate |
| Format           | Fountain (open)       | Proprietary                    |
| Update Frequency | Active development    | Infrequent                     |
| Target User      | Writers + AI users    | Production companies           |

**Key Insight**: Movie Magic excels in production pipeline integration but offers no AI assistance. WTFB targets the writing phase; Movie Magic targets production management.

---

## Traditional vs AI-Enhanced Comparison

| Feature                | Final Draft | Movie Magic | WTFB                       |
| ---------------------- | ----------- | ----------- | -------------------------- |
| **AI Writing Help**    | None        | None        | 11 agents                  |
| **AI Analysis**        | None        | None        | Structure, char, continuity|
| **AI Quality Gates**   | None        | None        | Script Supervisor          |
| **Format Standard**    | Yes (.fdx)  | Partial     | Exports to .fdx            |
| **Production Tools**   | Limited     | Excellent   | Export-focused             |
| **Collaboration**      | Real-time   | Single-user | Git-based                  |
| **Pricing**            | $249.99     | $249.95     | Free                       |
| **Open Source**        | No          | No          | Yes                        |
| **Pattern Library**    | None        | None        | 17+ patterns               |
| **Craft Knowledge**    | None        | None        | 24 skill modules           |

**Market Opportunity**: The traditional tools (Final Draft, Movie Magic) dominate the market but have not innovated with AI. This creates an opportunity for WTFB to serve as the AI-powered development layer that outputs to industry-standard formats.

**Workflow Vision**:

```text
┌─────────────────────────────────────────┐
│          WTFB Development Layer         │
│   (AI agents, craft knowledge, patterns)│
└──────────────────┬──────────────────────┘
                   │ Export
                   ▼
┌─────────────────────────────────────────┐
│        Final Draft / Movie Magic        │
│   (Industry submission, production)     │
└─────────────────────────────────────────┘
```

---

## Market Position Analysis

### What Exists

1. **General multi-agent frameworks** - Powerful but no domain expertise
2. **AI writing assistants** - Domain knowledge but single AI
3. **Film automation research** - Multi-agent but focused on production, not writing

### What's Missing (The Gap WTFB Fills)

- Multi-agent + deep screenwriting craft
- Authority/veto system for quality control
- Open-source with published CLI tools
- Pattern-based institutional knowledge
- Works across multiple AI providers

---

## Substantiated Claims

### Can Say With Confidence

1. **First open-source multi-agent screenwriting harness** - No direct competitor found
2. **Unique authority/veto system** - Not implemented in any framework reviewed
3. **Deepest craft knowledge encoding** - 24 skill modules vs. generic LLM prompts
4. **Only one with published CLI** - @wtfb/cli on npm
5. **Only AI-native alternative to Final Draft** - Traditional tools have no AI
6. **Free alternative to $249+ industry tools** - Open source vs proprietary
7. **Fully extensible ecosystem** - Integrate any OSS toolkit (Google Gen AI, etc.)
8. **Community marketplace model** - Users can contribute/sell workflows and tools
9. **Enterprise self-hosting with private workflows** - Keep custom algorithms confidential
10. **Open format foundation (Fountain)** - No vendor lock-in, easy AI service integration
11. **Future-proof platform** - Community can integrate new tech as it emerges

### Cannot Claim

1. "Revolutionary" - Multi-agent AI is an active field
2. "Best" - Subjective, depends on use case
3. "Only multi-agent creative tool" - FilmAgent exists (different focus)
4. "Industry standard" - Final Draft owns that position (~95% market share)
5. "Production pipeline replacement" - Movie Magic has superior budgeting/scheduling

---

## Recommendations

### Positioning Statement

> "The first open-source, fully extensible multi-agent harness for screenwriting - featuring tiered authority, encoded craft knowledge, production-ready CLI tools, and a community marketplace for custom workflows and tools."

### Differentiation to Emphasize

1. **Authority System** - No one else has veto/gate powers
2. **Craft Knowledge** - 24 skill modules, not generic prompts
3. **Open Source + CLI** - Others are closed or framework-only
4. **Multi-AI Support** - Works with Claude, Gemini, Codex
5. **Full Extensibility** - Integrate Google Gen AI Toolkit, LangChain, custom tools
6. **Community Marketplace** - Contribute workflows/tools (free or paid) to wtfb-app
7. **Real-Time Collaboration** - VS Code Live Share, not proprietary lock-in

### Areas to Develop

1. Novel writing support (expand beyond screenplay)
2. Community pattern contributions
3. Benchmark comparisons with competitors
4. Case studies / testimonials

### Integration Opportunities

**CrewAI Integration Potential:**

- Use CrewAI Flows as orchestration backbone
- Keep WTFB's domain expertise as the "brain"
- Leverage CrewAI's production-tested agent coordination
- Benefit from CrewAI's active community and updates

**Architecture Vision:**

```text
┌─────────────────────────────────────────┐
│           CrewAI Flows Layer            │  ← Orchestration
│         (state, events, routing)        │
└─────────────────────────────────────────┘
                    │
┌─────────────────────────────────────────┐
│           WTFB Domain Layer             │  ← Expertise
│  (11 agents, 24 skills, authority)      │
└─────────────────────────────────────────┘
                    │
┌─────────────────────────────────────────┐
│           LLM Provider Layer            │  ← Execution
│     (Claude, Gemini, OpenAI, etc.)      │
└─────────────────────────────────────────┘
```

**Benefits of Integration:**

- Don't reinvent orchestration wheel
- Gain CrewAI's async/parallel execution
- Access CrewAI's tool ecosystem
- Maintain WTFB's unique domain value

**What WTFB Adds to CrewAI:**

- Veto/Gate authority system (CrewAI lacks this)
- Screenwriting craft knowledge
- Pattern library
- Pre-built agent definitions with collaboration paths

### Cloud Deployment Vision (VPS + Open WebUI)

**Architecture Concept:**

```text
┌─────────────────────────────────────────────────────────────┐
│                    Client Layer                             │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────┐ │
│  │ Open WebUI  │  │  wtfb-app   │  │ Claude Code / CLI   │ │
│  │  (Chat UI)  │  │   (SaaS)    │  │   (Local Dev)       │ │
│  └──────┬──────┘  └──────┬──────┘  └──────────┬──────────┘ │
└─────────┼────────────────┼────────────────────┼─────────────┘
          │                │                    │
          ▼                ▼                    ▼
┌─────────────────────────────────────────────────────────────┐
│              WTFB Agent Cloud (VPS)                         │
│  ┌────────────────────────────────────────────────────────┐│
│  │              CrewAI Flows Orchestration                ││
│  │   (State management, routing, parallel execution)      ││
│  └────────────────────────┬───────────────────────────────┘│
│                           │                                 │
│  ┌────────────────────────▼───────────────────────────────┐│
│  │              WTFB Agent Crews                          ││
│  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐      ││
│  │  │   Writing   │ │  Analysis   │ │  Production │      ││
│  │  │    Crew     │ │    Crew     │ │    Crew     │      ││
│  │  │ ─────────── │ │ ─────────── │ │ ─────────── │      ││
│  │  │ Story Arch  │ │ Story Anlst │ │ Prod Coord  │      ││
│  │  │ Dialogue Wr │ │ Continuity  │ │ Session Mgr │      ││
│  │  │ Scene Writer│ │ Script Supv │ │ Scene Annot │      ││
│  │  │ Research Sp │ │ Standards   │ │             │      ││
│  │  └─────────────┘ └─────────────┘ └─────────────┘      ││
│  └────────────────────────────────────────────────────────┘│
│                           │                                 │
│  ┌────────────────────────▼───────────────────────────────┐│
│  │              Skill Modules & Patterns                  ││
│  │   (24 craft skills, 17+ patterns, knowledge base)      ││
│  └────────────────────────────────────────────────────────┘│
└─────────────────────────────────────────────────────────────┘
          │
          ▼
┌─────────────────────────────────────────────────────────────┐
│                    LLM Provider Layer                       │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐         │
│  │   Claude    │  │   Gemini    │  │   OpenAI    │         │
│  │   (API)     │  │   (API)     │  │   (API)     │         │
│  └─────────────┘  └─────────────┘  └─────────────┘         │
└─────────────────────────────────────────────────────────────┘
```

**Key Components:**

1. **Open WebUI Integration**
   - Chat-based interface for writers
   - Uses WTFB agents as "tools" or "functions"
   - Stateless queries routed to stateful crews

2. **wtfb-app SaaS**
   - Full project management
   - File storage, version history
   - Team collaboration features

3. **CrewAI Orchestration**
   - Handles crew instantiation
   - Manages state across sessions
   - Routes tasks to appropriate agents
   - Implements authority/veto logic

4. **Agent Crews (Grouped by Function)**
   - **Writing Crew**: Story Architect, Dialogue Writer, Scene Writer, Research Specialist
   - **Analysis Crew**: Story Analyst, Continuity Editor, Script Supervisor, Standards Reviewer
   - **Production Crew**: Production Coordinator, Session Manager, Scene Annotator

**Benefits of Cloud Deployment:**

- Writers don't need local CLI setup
- Agents maintain context across sessions
- Shared knowledge base for all users
- API access for third-party integrations
- Horizontal scaling for demand

**Implementation Path:**

1. Port WTFB agent definitions to CrewAI format
2. Build REST/WebSocket API for agent access
3. Create Open WebUI plugin for WTFB crews
4. Deploy to VPS (Docker-based)
5. Connect to wtfb-app as backend

---

## Sources

### Multi-Agent Frameworks

- [Top AI Agent Frameworks 2025 - Codecademy](https://www.codecademy.com/article/top-ai-agent-frameworks-in-2025)
- [CrewAI vs AutoGen - Medium](https://medium.com/@kanerika/crewai-vs-autogen-a-complete-comparison-of-multi-agent-ai-frameworks-3d2cec907231)
- [Multi-Agent Frameworks Tier List](https://langcopilot.com/posts/2025-11-01-top-multi-agent-ai-frameworks-2024-guide)
- [Microsoft: Designing Multi-Agent Intelligence](https://developer.microsoft.com/blog/designing-multi-agent-intelligence)

### AI Screenwriting

- [Best AI Screenwriting Software - SoftwareWorld](https://www.softwareworld.co/ai-screenwriting-software/)
- [Storywork](https://www.storywork.io/)
- [Arc Studio AI Tools](https://www.arcstudiopro.com/blog/the-best-tools-for-writers-in-2023)

### Traditional Screenwriting Software

- [Final Draft 13 Features](https://www.finaldraft.com/final-draft-13/)
- [Movie Magic Screenwriter](https://www.screenplay.com/products/movie-magic-screenwriter)
- [Screenwriting Software Comparison - StudioBinder](https://www.studiobinder.com/blog/best-screenwriting-software/)

### Film Production AI

- [FilmAgent Paper - arXiv](https://arxiv.org/abs/2501.12909)
- [FilmAgent GitHub](https://github.com/HITsz-TMG/FilmAgent)

### Academic Research

- [Designing with Multi-Agent AI - ACM DIS 2025](https://dl.acm.org/doi/10.1145/3715336.3735823)
- [Agentic AI Survey - Springer](https://link.springer.com/article/10.1007/s10462-025-11422-4)

---

## Conclusion

The claim that what we've built is "rare" can be **substantiated** in specific ways:

1. **Combination is rare**: Multi-agent + screenwriting domain + open source + CLI tools
2. **Authority system is unique**: No other framework implements veto/gate powers
3. **Depth of craft knowledge is unique**: 24 skill modules vs. generic prompts

However, the broader landscape shows active development in both multi-agent AI and AI writing tools. We're not alone in the space - we're at a **unique intersection** that no one else currently occupies.

**Verdict**: Not "rare" in absolute terms, but **distinctly positioned** in an underserved niche.

---

## Key Takeaways

### The "Pepsi Challenge" Results

| Dimension                    | Winner                     | Why                               |
| ---------------------------- | -------------------------- | --------------------------------- |
| **Multi-Agent Architecture** | Tie (WTFB/CrewAI/FilmAgent)| All implement multi-agent         |
| **Domain Expertise**         | **WTFB**                   | 24 skill modules vs none          |
| **Authority/Quality Control**| **WTFB**                   | Only one with veto/gate system    |
| **Screenwriting Focus**      | **WTFB**                   | FilmAgent = production            |
| **Production Readiness**     | **WTFB**                   | Published CLI, npm package        |
| **Pattern Library**          | **WTFB**                   | Only one with reusable patterns   |
| **Real-Time Collaboration**  | Tie (WTFB/Final Draft)     | VS Code Live Share vs proprietary |
| **Extensibility**            | **WTFB**                   | OSS toolkits, custom workflows    |
| **Community Marketplace**    | **WTFB**                   | Only one with contribution model  |
| **Enterprise Self-Hosting**  | **WTFB**                   | Private workflows, data control   |
| **Open File Format**         | **WTFB**                   | Fountain is open; .fdx is closed  |
| **Future-Proof**             | **WTFB**                   | Community integrates new tech     |
| **Open Source**              | Tie                        | All are open source               |
| **3D Production**            | FilmAgent                  | We don't do this (yet)            |
| **Industry Standard Format** | Final Draft                | .fdx is the submission standard   |
| **Production Pipeline**      | Movie Magic                | Budgeting/scheduling integration  |
| **AI Innovation**            | **WTFB**                   | Final Draft & Movie Magic: no AI  |
| **Price**                    | **WTFB**                   | Free vs $249+ for traditional     |

### What We Can Legitimately Claim

1. **"First open-source multi-agent screenwriting harness"** - Substantiated
2. **"Only framework with tiered authority (veto/gate)"** - Substantiated
3. **"Deepest encoded craft knowledge"** - Substantiated (24 modules)
4. **"Production-ready with published CLI"** - Substantiated (@wtfb/cli)
5. **"Fully extensible with any OSS toolkit"** - Substantiated (Google Gen AI, etc.)
6. **"Community marketplace for workflows/tools"** - Substantiated (wtfb-app)

### What We Should NOT Claim

1. ~~"Only multi-agent creative AI"~~ - FilmAgent exists
2. ~~"Revolutionary"~~ - It's an evolution, not revolution
3. ~~"Best"~~ - Subjective, depends on use case

### Honest Positioning

> **WTFB is the first production-ready, open-source multi-agent harness specifically built for screenwriting craft, featuring tiered authority control, 24 encoded skill modules, and a published CLI - filling a gap between general-purpose agent frameworks and single-AI writing tools.**

### Extended Positioning (Including Traditional Tools)

> **WTFB brings AI-powered development to professional screenwriting while maintaining compatibility with industry-standard tools. Unlike Final Draft and Movie Magic (which have no AI), and unlike AI writing assistants (which don't output to industry formats), WTFB provides the best of both worlds: intelligent multi-agent collaboration that exports to .fdx, PDF, and HTML for industry submission.**

### Platform Vision: This is Just the Start

WTFB is not just a tool - it's a **platform play**:

1. **Open Foundation**: Fountain format means any AI service can integrate
2. **Community-Driven**: New tech gets integrated as it emerges
3. **Enterprise Ready**: Private workflows for studios and production companies
4. **Marketplace Economy**: Creators can monetize their custom workflows
5. **Cross-Device**: Works on mobile, desktop, web - plain text travels everywhere
6. **AI Service Agnostic**: Easy to build new apps that plug into WTFB

**The Flywheel**:

```text
New AI Tech → Community Integrates → Platform Grows → More Users
     ↑                                                    │
     └────────────── More Contributors ←──────────────────┘
```

**Enterprise Value Proposition**:

- Studios can develop proprietary AI workflows
- Those workflows stay **private** on their infrastructure
- They benefit from the open ecosystem without exposing IP
- Option to contribute back (free or paid) if they choose

### Market Positioning Summary

```text
                        AI Capabilities
                              ▲
                              │
        AI Writing Tools      │      WTFB
        (Squibler, Storywork) │   ★ Multi-agent + Industry formats
                              │
        ──────────────────────┼────────────────────► Industry
                              │                      Standard
        [Empty Quadrant]      │      Final Draft
        No AI, No Standard    │      Movie Magic
                              │      (Industry standard, no AI)
                              │
```

**Strategic Position**: WTFB occupies the upper-right quadrant - combining AI capabilities with industry-standard output. This is currently an empty niche in the market.
