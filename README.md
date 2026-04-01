# ⚡ claude-power-skills

**20 power-user skills for Claude Code that turn your AI assistant into a senior engineering partner.**

Born from reverse-engineering how top-tier AI coding agents actually work internally — session management, multi-agent orchestration, adversarial testing, decision archaeology, calibrated estimation — then packaging those patterns as drop-in skills anyone can use.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/Skills-20-green.svg)](#skills)
[![Claude Code](https://img.shields.io/badge/Claude_Code-Compatible-blueviolet.svg)](https://docs.anthropic.com/en/docs/claude-code)

---

## Why this exists

Claude Code ships with solid defaults. But if you've pushed it on real projects — multi-repo monoliths, production incident debugging, sprint planning — you've hit the ceiling. The agent forgets context between sessions. It estimates effort like someone who's never shipped software. It doesn't know when it's stuck. It can't coordinate parallel workstreams.

These skills fix that. Each one encodes a specific workflow pattern that experienced engineers use intuitively, structured so the agent can execute it consistently.

No wrappers. No frameworks. No dependencies. Just SKILL.md files that plug directly into Claude Code's skill system.

---

## Quick Start

**Option 1: Plugin install**
```bash
claude plugins add irfad7/claude-power-skills
```

**Option 2: Clone and use**
```bash
git clone https://github.com/irfad7/claude-power-skills.git ~/.claude/skills/power-skills
# Skills auto-discover from the skills/ directory
```

**Option 3: Cherry-pick individual skills**
```bash
# Copy just the skills you want into your project's skills/ directory
cp -r claude-power-skills/skills/bughunter your-project/skills/
```

Then invoke any skill by name:
```
/bughunter        → adversarial security analysis
/ultraplan        → deep planning with creative exploration
/effort-estimate  → calibrated estimation with velocity tracking
/codebase-insight → persistent architecture analysis
```

---

## Skills

### 🧠 Session & Memory

| Skill | What It Does |
|-------|-------------|
| [**kairos-session**](skills/kairos-session/SKILL.md) | Session lifecycle management — structured boot sequence with context loading, state diffing, and memory consolidation on shutdown. Daemon mode for persistent background operation. |
| [**autodream**](skills/autodream/SKILL.md) | Memory synthesis across sessions — scans memory files, detects contradictions and duplicates, merges observations, promotes recurring patterns to reflexes. Outputs a health score. |
| [**session-review**](skills/session-review/SKILL.md) | End-of-session analysis — replays the session transcript, extracts decisions and patterns, computes knowledge deltas, generates handoff notes for the next session. |
| [**context-compression**](skills/context-compression/SKILL.md) | 3-layer compression pipeline for long conversations. Layer 1: MicroCompact (~30-40% reduction, zero info loss). Layer 2: AutoCompact (~60-70%). Layer 3: Full Compact (~85-90%). |

### 📐 Planning & Estimation

| Skill | What It Does |
|-------|-------------|
| [**ultraplan**](skills/ultraplan/SKILL.md) | Creative exploration before execution. 5-act structure: understand the problem, explore multiple approaches, validate technically, design incrementally, produce phased execution plan. Includes problem reframing, devil's advocate challenges, and YAGNI audits. |
| [**effort-estimate**](skills/effort-estimate/SKILL.md) | Calibrated estimation engine. Decomposes tasks into atoms, scores complexity on 3 axes, applies velocity calibration from past estimates. Maintains a `.velocity-profile.json` that makes estimates more accurate over time. Cold-start aware. |
| [**thinkback**](skills/thinkback/SKILL.md) | Decision archaeology — reconstruct why past decisions were made from git history, code patterns, and documentation. Three modes: dig (single decision), audit (batch review), replay (reasoning trace). |

### 🔍 Code Quality

| Skill | What It Does |
|-------|-------------|
| [**code-review**](skills/code-review/SKILL.md) | 6-pass deep code review: correctness, security, logic/design, performance, maintainability, integration. Structured output with severity levels, fix suggestions, and explicit acknowledgment of what's well-written. |
| [**bughunter**](skills/bughunter/SKILL.md) | Red team adversarial analysis. Maps attack surfaces, runs 5 systematic attack categories (input, state, logic, integration, data integrity), logs structured exploits, chains bugs into kill chains. Three modes: quick (15min), standard, deep (parallel subagents). |
| [**codebase-insight**](skills/codebase-insight/SKILL.md) | Deep codebase analysis that persists to `.codebase-insight.md`. Maps architecture, patterns, dependencies, critical paths, quirks, and health scores. Delta mode updates only what changed. Future sessions load the file instantly instead of re-analyzing. |
| [**pr-autofix**](skills/pr-autofix/SKILL.md) | Reads PR review comments and CI failures, triages by priority, applies fixes (one commit per comment), drafts reviewer responses, and pushes. Compresses the review→fix→push cycle from hours to minutes. |

### 🔄 Workflow & Orchestration

| Skill | What It Does |
|-------|-------------|
| [**coordinator-mode**](skills/coordinator-mode/SKILL.md) | Multi-agent orchestration. Decomposes complex tasks, plans execution waves with dependency ordering, dispatches parallel subagents, merges results with conflict detection, runs quality gates. |
| [**batch-mode**](skills/batch-mode/SKILL.md) | Apply one operation across many targets consistently. Mandatory dry-run phase, progress tracking, exception handling with skip/retry/abort, structured report on completion. |
| [**prompt-speculation**](skills/prompt-speculation/SKILL.md) | Proactive next-step engine. After completing work, generates 4 candidate follow-ups (immediate, quality, strategic, preventive), scores them by leverage = (Impact × Urgency) / Effort, and presents the top 3. |

### 🛡️ Security & Recovery

| Skill | What It Does |
|-------|-------------|
| [**security-review**](skills/security-review/SKILL.md) | 7-phase security audit covering secrets scanning, auth/authz review, input validation, data protection, dependency analysis, infrastructure config, and business logic flaws. Produces a structured report with severity ratings and remediation code. |
| [**stuck-recovery**](skills/stuck-recovery/SKILL.md) | Detects when the agent is looping on the same approach. Forces a structured reset: stop → restate the problem → audit assumptions → gather fresh evidence → reframe using 5 Whys / inversion / simplification → new approach → checkpoint. |
| [**frustration-aware**](skills/frustration-aware/SKILL.md) | 3-tier frustration detection (explicit, implicit, preemptive). Fundamentally changes approach on detection — not just tone, but strategy. Escalation rules prevent repeated corrections. |

### 🔒 Protection & Documentation

| Skill | What It Does |
|-------|-------------|
| [**undercover-mode**](skills/undercover-mode/SKILL.md) | Stealth contribution mode. Strips AI attribution from commits, PRs, code comments. Matches repo conventions for commit style, comment density, PR templates. Pre-commit checklist ensures nothing leaks. |
| [**anti-distillation**](skills/anti-distillation/SKILL.md) | Context protection. Prevents sensitive project context from leaking across boundaries — into public outputs, other projects, or training data capture. 5-layer defense system. |
| [**magic-docs**](skills/magic-docs/SKILL.md) | Documentation generator that reads the actual codebase. Every claim traces to a file path. Supports README, API reference, architecture guide, onboarding guide, and changelog. Monorepo-aware. |

---

## How skills work

Each skill is a single `SKILL.md` file with YAML frontmatter and structured instructions:

```yaml
---
name: skill-name
description: When to activate this skill (trigger phrases, contexts)
metadata:
  version: 1.0.0
---

# Skill Title

[Structured protocol the agent follows]
```

Skills activate automatically based on conversation context, or you invoke them directly with `/skill-name`. No configuration required.

---

## What makes these different

**They're protocols, not prompts.** Each skill defines a multi-step process with decision points, structured outputs, and quality gates. The agent follows the protocol — it doesn't freestyle.

**They compound.** `kairos-session` boots context → `autodream` consolidates memory → `session-review` extracts lessons → next session starts smarter. `bughunter` finds vulnerabilities → `code-review` catches design issues → `pr-autofix` resolves feedback → `undercover-mode` ships it clean.

**They're calibrated.** `effort-estimate` tracks actual completion times and adjusts future estimates. `frustration-aware` escalates based on signal density, not single events. `context-compression` picks the right layer based on conversation length.

**They're battle-tested.** Built from patterns used across production codebases — SaaS platforms, multi-tenant systems, real-time pipelines. Not theoretical prompts. Workflows that survived contact with real projects.

---

## Skill deep dives

<details>
<summary><strong>bughunter — adversarial analysis in action</strong></summary>

Given a simple API endpoint:
```javascript
app.get('/api/users/:id', async (req, res) => {
  const user = await db.query(`SELECT * FROM users WHERE id = ${req.params.id}`);
  res.json({ password: user.password, email: user.email });
});
```

BugHunter produces structured exploit reports (BUG-001 format), chains them into kill chains, and suggests specific fixes. Not "consider input validation" — the actual parameterized query you need to write.

</details>

<details>
<summary><strong>effort-estimate — calibrated estimation</strong></summary>

Instead of "this should take 2-3 hours" (which always means 2-3 days), effort-estimate:

1. Decomposes into atomic tasks (including hidden work: migrations, tests, config)
2. Scores each on 3 axes: code complexity, uncertainty, integration risk
3. Applies your personal velocity multiplier from past estimates
4. Adds probability-weighted risk buffers
5. Delivers best/expected/worst with confidence level

First estimate is rough. After 5 tracked tasks, it knows your pace.

</details>

<details>
<summary><strong>codebase-insight — persistent architecture memory</strong></summary>

Analyzes your entire codebase and saves the result to `.codebase-insight.md`. Next session, instead of re-reading 200 files, the agent loads the insight file and knows:

- Architecture pattern and organization style
- All code patterns (error handling, auth, validation, data fetching)
- Component dependency map
- Critical user paths traced end-to-end
- Quirks and gotchas that waste debugging time
- Health score across 7 dimensions

Delta mode updates only what changed since last analysis.

</details>

<details>
<summary><strong>ultraplan — planning that starts with thinking</strong></summary>

Most planning tools skip the most important part: figuring out what to build.

```
Regular:    Idea → Plan → Build → "Wait, this isn't what we needed"
UltraPlan:  Idea → Explore → Challenge → Validate → Plan → Build → Ship
```

Forces problem reframing, generates 2-3 approaches with honest trade-offs, runs devil's advocate against its own recommendation, then validates technically before producing a phased execution plan.

</details>

---

## Project structure

```
claude-power-skills/
├── skills/
│   ├── anti-distillation/SKILL.md
│   ├── autodream/SKILL.md
│   ├── batch-mode/SKILL.md
│   ├── bughunter/SKILL.md
│   ├── code-review/SKILL.md
│   ├── codebase-insight/SKILL.md
│   ├── context-compression/SKILL.md
│   ├── coordinator-mode/SKILL.md
│   ├── effort-estimate/SKILL.md
│   ├── frustration-aware/SKILL.md
│   ├── kairos-session/SKILL.md
│   ├── magic-docs/SKILL.md
│   ├── pr-autofix/SKILL.md
│   ├── prompt-speculation/SKILL.md
│   ├── security-review/SKILL.md
│   ├── session-review/SKILL.md
│   ├── stuck-recovery/SKILL.md
│   ├── thinkback/SKILL.md
│   ├── ultraplan/SKILL.md
│   └── undercover-mode/SKILL.md
├── LICENSE
├── README.md
├── changelog.md
└── package.json
```

---

## Contributing

Found a bug in a skill? Want to add a new one? PRs welcome.

Skills should follow the existing format: YAML frontmatter with `name`, `description`, and `metadata`, followed by a structured protocol. Every skill should define when it activates, what steps it follows, and what output it produces.

---

## License

MIT — use these however you want.

---

Built by [Irfad Imtiaz](https://github.com/irfad7)
