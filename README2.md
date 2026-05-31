# 🤖 Mobile Dev AI Team

> An open-source multi-agent system for Claude Code that brings a full software development team to your mobile projects — Flutter, Android, and iOS.

[![Claude Code](https://img.shields.io/badge/Claude%20Code-Subagents-blue)](https://docs.anthropic.com/en/docs/claude-code/overview)
[![Mobile](https://img.shields.io/badge/Stack-Flutter%20%7C%20Android%20%7C%20iOS-02569B)](https://flutter.dev)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

---

## What is this?

Instead of asking Claude Code to do everything alone, this repo gives you **8 specialized AI agents** that work as a real development team — discussing, reviewing, and challenging each other before and after every feature is built.

The team discusses every feature **before** writing a single line of code, and reviews everything **after** implementation. Nothing ships without the Judge's approval.

---

## The Team

| Agent | Role | When Invoked |
|-------|------|-------------|
| 🗂️ **Project Manager** | Breaks features into tasks, writes acceptance criteria | Start of every feature |
| 🏗️ **Architect** | System design, patterns, tech decisions | Pre-dev & code review |
| 📱 **Senior Mobile Engineer** | Flutter/Android/iOS implementation | After Judge approves plan |
| 🧪 **QA Engineer** | Test plans, writing tests, quality gates | Pre-dev plan & post-dev |
| 🔒 **Security Expert** | OWASP Mobile Top 10, threat modeling | Pre-dev & implementation audit |
| 🎨 **UI/UX Expert** | Material 3, HIG, accessibility, design system | Pre-dev & screen review |
| ⚡ **Performance Analyzer** | Frame rates, memory, battery, jank | Post-dev & on demand |
| ⚖️ **Judge** | Final go/no-go, conflict resolution, ship decisions | After pre-dev & post-dev |

---

## Workflow

```
New Feature Request
      │
      ▼
┌─────────────────────────────────────────────┐
│           PRE-DEVELOPMENT                    │
│  PM → Architect → Security → UI/UX → QA     │
│              └──────► Judge ◄───────────────┘
│                   GO / HOLD                  │
└─────────────────────────────────────────────┘
      │ (only if GO)
      ▼
┌─────────────────────────────────────────────┐
│           DEVELOPMENT                        │
│        Mobile Engineer builds               │
│       + Performance watching               │
└─────────────────────────────────────────────┘
      │
      ▼
┌─────────────────────────────────────────────┐
│           POST-DEVELOPMENT                   │
│  QA + Security + UI/UX + Performance        │
│              + Architect                     │
│              └──────► Judge ◄───────────────┘
│                  SHIP / HOLD                 │
└─────────────────────────────────────────────┘
```

---

## Quick Start

### 1. Install Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

### 2. Clone this repo into your mobile project

```bash
# Copy the .claude folder and CLAUDE.md into your project root
cp -r mobile-dev-agents/.claude your-project/
cp mobile-dev-agents/CLAUDE.md your-project/
cp -r mobile-dev-agents/decisions your-project/
```

Or clone directly and start a new project:

```bash
git clone https://github.com/YOUR_USERNAME/mobile-dev-agents.git
cd mobile-dev-agents
claude
```

### 3. Start Claude Code

```bash
claude
```

### 4. Use slash commands

```bash
# Start a new feature — full team pre-dev discussion
/feature Add offline sync for the orders list

# Review what was just built
/review

# Security + performance deep audit
/audit

# Final check before release
/ship v1.2.0
```

---

## File Structure

```
your-project/
├── CLAUDE.md                          # Orchestrator — team rules & workflow
├── decisions/
│   └── DECISIONS.md                   # All team decisions are logged here
└── .claude/
    ├── agents/
    │   ├── project-manager.md         # PM agent
    │   ├── architect.md               # Architect agent
    │   ├── mobile-engineer.md         # Senior Mobile Engineer agent
    │   ├── qa-engineer.md             # QA Engineer agent
    │   ├── security-expert.md         # Security Expert agent
    │   ├── ui-ux-expert.md            # UI/UX Expert agent
    │   ├── performance-analyzer.md    # Performance Analyzer agent
    │   └── judge.md                   # Judge agent
    └── commands/
        ├── feature.md                 # /feature — pre-dev team discussion
        ├── review.md                  # /review — post-dev team review
        ├── audit.md                   # /audit — security + performance deep dive
        ├── design-review.md           # /design-review — UI/UX + arch review
        └── ship.md                    # /ship — final release check
```

---

## How Agents Work (Claude Code Subagents)

Custom subagents are stored in `.claude/agents/` as Markdown files — they're version-controlled, team-shareable, and far more powerful than ad-hoc prompting. Each agent runs with its own context window and focused instructions.

The main Claude Code session acts as an orchestrator, deciding when to delegate and how to combine results. Subagents can run in parallel when their tasks are independent.

---

## Customizing Agents

Each agent is a plain Markdown file. To customize:

**Change the tech stack** — Edit `mobile-engineer.md` to match your architecture (e.g., change from BLoC to Riverpod).

**Add project conventions** — Add a "Project Conventions" section to any agent.

**Adjust quality bars** — Edit coverage targets in `qa-engineer.md`, performance targets in `performance-analyzer.md`.

**Add agents** — Create a new `.md` file in `.claude/agents/` and reference it in `CLAUDE.md`.

---

## Contributing

This is an open-source project built for the mobile development community.

**To contribute:**
1. Fork the repo
2. Improve an agent's system prompt, add a new agent, or improve the workflow
3. Open a PR with a clear description of what changed and why

**Ideas welcome:**
- DevOps/CI agent (GitHub Actions, Fastlane)
- Localization/i18n agent
- App Store review agent
- Accessibility specialist agent

---

## License

MIT — use freely in personal and commercial projects.

---

## Credits

Built with [Claude Code](https://docs.anthropic.com/en/docs/claude-code/overview) subagent architecture.
Designed for the Flutter & mobile dev community.
