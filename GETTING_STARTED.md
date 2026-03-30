# 🔌 Getting Started: Wiring The Agency to Your AI Tools

> **The short version:** Each agent is a markdown file containing a specialist persona. When you place that file where your AI tool can read it, the tool can adopt that persona on demand. This guide walks you through exactly how that works for every supported tool.

---

## How It Works (The Mental Model)

Agent files in this repository are **structured system prompts** written in markdown. They define:

- A specialist's identity, expertise, and communication style
- The deliverables they produce (code, documents, plans)
- The workflows and processes they follow
- The quality bar they hold themselves to

When your AI tool reads one of these files, it knows how to *become* that specialist when you ask it to. You are not installing plugins or running services — you are giving the AI a detailed role description it can step into.

```
You (request) → AI Tool (reads agent file) → Specialist responds
```

Nothing else is required. The agents are plain text. There is no runtime, no server, no API key, and no additional dependency.

---

## Step 0: Clone the Repository

```bash
git clone https://github.com/msitarzewski/agency-agents.git
cd agency-agents
```

All commands in this guide assume you are in the cloned directory unless otherwise noted.

---

## Step 1: Pick Your Tool

| Tool | Scope | Format | Best for |
|------|-------|--------|----------|
| [Claude Code](#claude-code) | User-wide | `.md` | Full agent suite, conversational workflows |
| [GitHub Copilot](#github-copilot) | User-wide | `.md` | IDE-integrated agents, VS Code / JetBrains |
| [Cursor](#cursor) | Per-project | `.mdc` | Inline code editing with specialist context |
| [Aider](#aider) | Per-project | `CONVENTIONS.md` | CLI pair programming |
| [Windsurf](#windsurf) | Per-project | `.windsurfrules` | Codeium's IDE with inline rules |
| [Gemini CLI](#gemini-cli) | User-wide | Extension | Google Gemini in the terminal |
| [Antigravity](#antigravity) | User-wide | `SKILL.md` | Gemini skills via Antigravity |
| [OpenCode](#opencode) | Per-project | `.md` | OpenCode project agents |
| [OpenClaw](#openclaw) | User-wide | Workspace | OpenClaw agent workspaces |
| [Qwen Code](#qwen-code) | Per-project | `.md` | Alibaba Qwen SubAgents |

---

## Claude Code

**How it works:** Claude Code reads `.md` files from `~/.claude/agents/`. Any file with valid YAML frontmatter is available as a named agent. You reference agents by name in conversation.

### Install

```bash
# Install all agents
./scripts/install.sh --tool claude-code

# Or manually install a single category
cp engineering/*.md ~/.claude/agents/
```

### Activate an Agent

In any Claude Code session, reference the agent by name:

```
Activate Frontend Developer and help me build a login form in React.
```

```
Use the Reality Checker to evaluate whether this feature is production-ready.
```

```
Switch to Backend Architect mode. I need to design a REST API for a todo app.
```

### Verify Installation

```bash
ls ~/.claude/agents/ | head -10
```

You should see agent files like `engineering-frontend-developer.md`, `testing-reality-checker.md`, etc.

---

## GitHub Copilot

**How it works:** GitHub Copilot reads `.md` agent files from `~/.github/agents/` and `~/.copilot/agents/`. The same native format as Claude Code — no conversion needed.

### Install

```bash
# Install all agents
./scripts/install.sh --tool copilot

# Or manually install a category
cp engineering/*.md ~/.github/agents/
cp engineering/*.md ~/.copilot/agents/
```

### Activate an Agent

In any Copilot session (VS Code Chat, GitHub.com, JetBrains):

```
Activate Frontend Developer and review this component for accessibility issues.
```

```
Use the Security Engineer agent to audit this authentication flow.
```

---

## Cursor

**How it works:** Cursor reads `.mdc` rule files from `.cursor/rules/` inside your project directory. Rules are project-scoped — you install them per project, not globally. Each agent becomes a rule that Cursor references during code editing.

### Install

```bash
# Run from your project root
cd /path/to/your/project

# Step 1: Generate the .mdc rule files (one-time, or after adding agents)
/path/to/agency-agents/scripts/convert.sh --tool cursor

# Step 2: Install into your project
/path/to/agency-agents/scripts/install.sh --tool cursor
```

### Activate an Agent

With Cursor rules installed, reference the agent in Cursor Chat or inline edit:

```
@Frontend Developer build me a TypeScript utility for debouncing API calls.
```

Or mention the agent role naturally:

```
Using the Backend Architect approach, design the database schema for this feature.
```

### Verify Installation

```bash
ls .cursor/rules/ | head -5
```

You should see `.mdc` files for each agent.

---

## Aider

**How it works:** Aider reads `CONVENTIONS.md` from your project root automatically on startup. All agents are consolidated into this single file. When Aider starts, it reads the conventions and applies them to every interaction.

### Install

```bash
# Run from your project root
cd /path/to/your/project

/path/to/agency-agents/scripts/install.sh --tool aider
```

### Activate an Agent

Start Aider as usual — the agents are already loaded. Reference them in your prompts:

```bash
aider --message "Activate Backend Architect: design the API schema for a blog platform"
```

Or interactively:

```
> Activate Frontend Developer. Refactor this component to use React hooks.
```

---

## Windsurf

**How it works:** Windsurf reads `.windsurfrules` from your project root. Like Aider, all agents are consolidated into this file and active for every session in that project.

### Install

```bash
# Run from your project root
cd /path/to/your/project

/path/to/agency-agents/scripts/install.sh --tool windsurf
```

### Activate an Agent

In Windsurf's Cascade panel:

```
Activate Security Engineer. Review this OAuth implementation for vulnerabilities.
```

---

## Gemini CLI

**How it works:** Gemini CLI loads extensions from `~/.gemini/extensions/`. The agents are packaged as a single extension with individual skill files. Because the extension manifest is generated, you need to run `convert.sh` before installing.

### Install

```bash
# Step 1: Generate the Gemini CLI extension (required on fresh clone)
./scripts/convert.sh --tool gemini-cli

# Step 2: Install the extension
./scripts/install.sh --tool gemini-cli
```

### Activate an Agent

In your Gemini CLI session:

```
Use the Frontend Developer skill to build a responsive navigation component.
```

---

## Antigravity

**How it works:** Antigravity installs skill files to `~/.gemini/antigravity/skills/`. Each agent becomes a separate `SKILL.md` prefixed with `agency-` to avoid naming conflicts.

### Install

```bash
./scripts/install.sh --tool antigravity
```

### Activate an Agent

Reference the skill in your Antigravity session:

```
Use the agency-backend-architect skill to design a caching layer.
```

---

## OpenCode

**How it works:** OpenCode reads agent `.md` files from `.opencode/agents/` inside your project. Project-scoped — install per project.

### Install

```bash
# Run from your project root
cd /path/to/your/project

/path/to/agency-agents/scripts/install.sh --tool opencode
```

### Activate an Agent

In your OpenCode session:

```
Activate the DevOps Automator agent to write a GitHub Actions workflow for this project.
```

---

## OpenClaw

**How it works:** OpenClaw workspaces live at `~/.openclaw/agency-agents/`. Each agent is converted to a workspace containing three files: `SOUL.md` (identity), `AGENTS.md` (capabilities), and `IDENTITY.md` (context). After installation, run `openclaw gateway restart` to activate new agents.

### Install

```bash
# Step 1: Generate OpenClaw workspaces
./scripts/convert.sh --tool openclaw

# Step 2: Install and register
./scripts/install.sh --tool openclaw

# Step 3: Restart the gateway
openclaw gateway restart
```

### Activate an Agent

```
openclaw invoke agency-frontend-developer "Build a responsive pricing table component"
```

---

## Qwen Code

**How it works:** Qwen Code reads SubAgent `.md` files from `.qwen/agents/` in your project. After installing, run `/agents manage` inside Qwen Code to refresh the agent list.

### Install

```bash
# Run from your project root
cd /path/to/your/project

/path/to/agency-agents/scripts/install.sh --tool qwen
```

### Activate an Agent

Inside Qwen Code, use `/agents manage` to select the installed agents, then reference them by name:

```
@Frontend Developer create a TypeScript interface for a User model with validation.
```

---

## Using Multiple Agents Together

Individual agents are powerful. Multi-agent workflows are transformative.

### The Basic Pattern

Agents do not share memory by default. The pattern for multi-agent work is:

1. Activate the first agent and get its output
2. Copy that output into your next prompt
3. Activate the next agent with the previous output as context

```
# Step 1
Activate Sprint Prioritizer.

Project: a task management SaaS.
Timeline: 6 weeks.
Stack: Next.js + PostgreSQL.

Produce a sprint plan.

---

# Step 2 — paste the sprint plan output into this prompt
Activate Backend Architect.

Sprint plan: [paste Sprint Prioritizer output here]

Design the database schema and API structure for this project.
```

### Common Workflows

**Feature build (3 agents)**
```
Sprint Prioritizer → Backend Architect → Frontend Developer
```

**Quality gate (1 agent)**
```
Reality Checker → validates any deliverable, requires evidence
```

**Marketing launch (4 agents)**
```
Growth Hacker → Content Creator → Social Media Strategist → Analytics Reporter
```

**Full project lifecycle (NEXUS)**
```
Agents Orchestrator → activates all phases automatically
```

See `strategy/QUICKSTART.md` for ready-to-copy orchestration prompts, and `examples/` for complete worked workflows.

---

## Your First Agent: A Complete Walkthrough

Here is a concrete end-to-end example using Claude Code (the simplest setup).

### 1. Install

```bash
git clone https://github.com/msitarzewski/agency-agents.git
cd agency-agents
./scripts/install.sh --tool claude-code
```

### 2. Verify

```bash
ls ~/.claude/agents/ | grep frontend
# engineering-frontend-developer.md
```

### 3. Open a Claude Code session and activate

```
Activate Frontend Developer.

I'm building a Next.js SaaS app. I need a reusable Modal component that:
- Accepts a title, body content (as React children), and onClose callback
- Traps focus when open
- Closes on Escape key or backdrop click
- Is accessible (WCAG 2.1 AA)
- Uses Tailwind CSS

Deliver the component with TypeScript types and a usage example.
```

### 4. What you will get

The Frontend Developer agent produces:

- A typed `Modal.tsx` component
- Full accessibility implementation (focus trap, ARIA attributes, keyboard handlers)
- A usage example showing how to wire it into a page
- Notes on Core Web Vitals impact

This is not a generic AI response — the agent applies its specialist expertise, follows its defined workflow, and delivers according to its stated success metrics.

---

## Selecting Agents for Your Task

Use this as a quick decision guide:

| Task | Agent(s) to use |
|------|----------------|
| Build a React/Vue/Angular component | Frontend Developer |
| Design a database schema or API | Backend Architect |
| Write or review infrastructure code | DevOps Automator |
| Audit code for security issues | Security Engineer |
| Set up CI/CD or release pipelines | DevOps Automator |
| Review code before merging | Code Reviewer |
| Write technical documentation | Technical Writer |
| Create a brand identity | Brand Guardian |
| Write SEO-optimized content | Content Creator |
| Plan sprints and milestones | Sprint Prioritizer + Senior Project Manager |
| Validate a feature before shipping | Reality Checker |
| Grow a community | Reddit Community Builder, Growth Hacker |
| Build for iOS/Android | Mobile App Builder |
| Implement ML features | AI Engineer |
| Run a full product discovery | NEXUS (see `strategy/QUICKSTART.md`) |

The full roster is in `README.md`. Each agent lists when to use it.

---

## Regenerating Integration Files

After adding or modifying agents, regenerate all integration formats:

```bash
./scripts/convert.sh           # All tools
./scripts/convert.sh --tool cursor   # One tool only
```

Then reinstall:

```bash
./scripts/install.sh --tool cursor
```

---

## Persistent Memory Across Sessions

By default, agents do not remember previous conversations. For multi-day or multi-agent projects, wire in an MCP-compatible memory server:

```bash
# Any MCP memory server with remember/recall/rollback support works.
# See integrations/mcp-memory/README.md for setup.
```

With memory wired in, agents can store their deliverables and pick up where they left off:

```
Activate Backend Architect.

Project: RetroBoard. Recall previous context for this project
and design the API schema.
```

See `examples/workflow-with-memory.md` for the full pattern.

---

## Further Reading

| Document | What it covers |
|----------|---------------|
| `README.md` | Full agent roster with descriptions |
| `strategy/QUICKSTART.md` | NEXUS orchestration in 5 minutes |
| `strategy/nexus-strategy.md` | Complete multi-agent doctrine (800+ lines) |
| `examples/workflow-startup-mvp.md` | 4-week MVP build, step by step |
| `examples/workflow-with-memory.md` | Multi-agent workflow with persistent context |
| `integrations/README.md` | All supported tools reference |
| `CONTRIBUTING.md` | How to write and submit your own agents |
