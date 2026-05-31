<div align="center">

# 🤖 Mobile Dev AI Team

**A full AI development team for your mobile projects — built on Claude Code subagents**

[![Claude Code](https://img.shields.io/badge/Claude%20Code-Subagents-6366F1?style=for-the-badge&logo=anthropic&logoColor=white)](https://docs.anthropic.com/en/docs/claude-code/overview)
[![Flutter](https://img.shields.io/badge/Flutter-Primary%20Stack-02569B?style=for-the-badge&logo=flutter&logoColor=white)](https://flutter.dev)
[![Android](https://img.shields.io/badge/Android-Kotlin-3DDC84?style=for-the-badge&logo=android&logoColor=white)](https://developer.android.com)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

*8 specialized agents that discuss, design, build, review, and ship together — before and after every feature*

[Quick Start](#-quick-start) • [The Team](#-the-team) • [How It Works](#-how-it-works) • [Commands](#-slash-commands) • [Token Tips](#-minimizing-token-usage) • [Customize](#-customizing-agents)

</div>

---

## 🧠 What Is This?

Instead of asking Claude Code to do everything in one giant prompt, this repo gives you **8 specialized AI agents** that work as a real software development team.

The team **discusses every feature before writing a single line of code** and **reviews everything after implementation**. Nothing ships without the Judge's approval.

```
You type:  /feature Add biometric login

  PM          → Breaks down tasks + acceptance criteria
  Architect   → Proposes technical approach (local_auth + flutter_secure_storage)
  Security    → Flags: PIN fallback can bypass biometric — needs mitigation
  UI/UX       → Defines all states: enrolled / failed / locked-out
  QA          → Writes test plan before code exists
  Judge       → 🟢 GO — with condition: fallback must re-authenticate

  Mobile Engineer → Implements
  
  [post-dev]
  QA + Security + UI/UX + Performance + Architect → all report
  Judge → 🚀 SHIP
```

---

## 👥 The Team

| Agent | Role | Triggered |
|-------|------|-----------|
| 🗂️ **Project Manager** | Breaks features into tasks, writes acceptance criteria, tracks progress | Start of every feature |
| 🏗️ **Architect** | System design, pattern selection, tech decisions, code review | Pre-dev + post-dev |
| 📱 **Mobile Engineer** | Flutter/Android/iOS implementation — clean, tested, production code | After Judge approves plan |
| 🧪 **QA Engineer** | Test plans (before coding), test writing, coverage validation | Pre-dev plan + post-dev gate |
| 🔒 **Security Expert** | OWASP Mobile Top 10, threat modeling, auth review, data storage audit | Pre-dev design + post-dev audit |
| 🎨 **UI/UX Expert** | Material 3, Apple HIG, accessibility (WCAG 2.1 AA), all UI states | Any UI/screen changes |
| ⚡ **Performance Analyzer** | Frame rates, memory leaks, widget rebuilds, battery drain | Post-dev + on demand |
| ⚖️ **Judge** | Final GO/HOLD/SHIP decisions, conflict resolution | After pre-dev + before ship |

---

## ⚡ Quick Start

### 1. Install Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

### 2. Add to your project

**Option A — Start a new project:**
```bash
git clone https://github.com/DineshWayaman/Agentic-Mobile-Dev-Team.git
cd Agentic-Mobile-Dev-Team
claude
```

**Option B — Drop into an existing Flutter project:**
```bash
cp -r mobile-dev-agents/.claude   your-flutter-project/
cp mobile-dev-agents/CLAUDE.md    your-flutter-project/
cp -r mobile-dev-agents/decisions your-flutter-project/

cd your-flutter-project
claude
```

### 3. Use it

```bash
# In the Claude Code terminal:
/feature Add offline sync to the orders screen
```

The agents will discuss it, the Judge will approve or hold, and only then will the Mobile Engineer start coding.

---

## 🔄 How It Works

Every feature passes through two mandatory gates:

```
┌─────────────────────────────────────────────────────┐
│  GATE 1 — PRE-DEVELOPMENT                           │
│                                                     │
│  PM → Architect → Security → UI/UX → QA → Judge    │
│                                                     │
│  🟢 GO   → Mobile Engineer starts                  │
│  🔴 HOLD → Blockers must be resolved first         │
└─────────────────────────────────────────────────────┘
                        ↓ (only on GO)
┌─────────────────────────────────────────────────────┐
│  DEVELOPMENT                                        │
│  Mobile Engineer implements                         │
│  Performance Analyzer watches for early issues     │
└─────────────────────────────────────────────────────┘
                        ↓
┌─────────────────────────────────────────────────────┐
│  GATE 2 — POST-DEVELOPMENT                          │
│                                                     │
│  QA + Security + UI/UX + Performance + Architect   │
│                      ↓                             │
│                    Judge                           │
│                                                     │
│  🚀 SHIP  → Cleared for release                    │
│  ⏸️ HOLD  → Fixes needed — returns to Engineer     │
│  🚨 BLOCK → Critical issue — hard stop             │
└─────────────────────────────────────────────────────┘
```

---

## 💬 Slash Commands

| Command | What happens | When to use |
|---------|-------------|-------------|
| `/feature [description]` | Full 8-agent pre-dev discussion | Every new feature |
| `/review` | Post-dev team audit | After implementation |
| `/audit [area]` | Deep security + performance scan | Periodic or pre-release |
| `/design-review` | UI/UX + Architect pass on a screen | UI-only changes |
| `/ship [version]` | Final release check | Before publishing to store |

---

## 📁 File Structure

```
your-project/
├── CLAUDE.md                          # Orchestrator — team rules & workflow
├── decisions/
│   └── DECISIONS.md                   # All team decisions logged here
└── .claude/
    ├── agents/
    │   ├── project-manager.md
    │   ├── architect.md
    │   ├── mobile-engineer.md
    │   ├── qa-engineer.md
    │   ├── security-expert.md
    │   ├── ui-ux-expert.md
    │   ├── performance-analyzer.md
    │   └── judge.md
    └── commands/
        ├── feature.md                 # /feature
        ├── review.md                  # /review
        ├── audit.md                   # /audit
        ├── design-review.md           # /design-review
        └── ship.md                    # /ship
```

---

## 💰 Minimizing Token Usage

Running all 8 agents costs more than a single session. Here's how to keep costs low without sacrificing quality:

### Use the right command for the task

| Task | What to use | Agents used |
|------|-------------|-------------|
| New feature | `/feature` | All 8 |
| Bug fix | Talk to `mobile-engineer` directly | 1 |
| UI-only change | `/design-review` | 3 |
| Security concern | `security-expert` directly | 1 |
| Pre-release check | `/ship` | 4 |

### Use the Judge's fast-track rule

If all agents report no issues, the Judge responds in one line:
`🚀 SHIP — all agents clear.`

Full verdicts only when there are actual conflicts or blockers.

---

## ✏️ Customizing Agents

Every agent is a plain Markdown file. Edit to match your project:

**Change state management** — open `mobile-engineer.md`, update BLoC → Riverpod/Provider

**Change coverage targets** — edit the percentage in `qa-engineer.md`

**Add project conventions** — add a "Project Conventions" section to any agent file

**Add a new agent** — create a `.md` file in `.claude/agents/` with a frontmatter `name:` and `description:`, then reference it in `CLAUDE.md`

**Skip an agent** — remove it from the relevant command in `.claude/commands/`

**Per-agent model selection** — add `model: claude-opus-4-6` to the frontmatter of any agent to use a more powerful model for high-stakes reasoning (e.g. the Judge)

---

## 📋 Decision Log

Every major team decision is logged automatically to `decisions/DECISIONS.md`:

```markdown
### 2026-05-31 Biometric Login — Architecture Decision
**Decision:** Use local_auth + flutter_secure_storage
**Rationale:** Handles both Android Keystore and iOS Keychain natively
**Alternatives rejected:** Custom implementation — too large a security surface
**Decided by:** Architect, confirmed by Judge
```

This gives you a full audit trail of *why* things were built the way they were.

---

## 🤝 Contributing

Pull requests welcome. Ideas for new agents:

- 🚀 **DevOps agent** — GitHub Actions, Fastlane, app store submission
- 🌍 **Localization agent** — i18n coverage, translation quality
- ♿ **Accessibility specialist** — deeper WCAG audit beyond UI/UX scope
- 📊 **Analytics agent** — event tracking coverage, privacy compliance

**To contribute:**
1. Fork the repo
2. Improve an agent prompt, add a new agent, or improve the workflow
3. Open a PR with a clear description of what changed and why

---

## 📄 License

MIT — use freely in personal and commercial projects.

---

<div align="center">

Built with [Claude Code](https://docs.anthropic.com/en/docs/claude-code/overview) subagent architecture.
Made for the Flutter & mobile dev community. 🇱🇰

</div>
