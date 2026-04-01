# Contributing to claude-power-skills

Thanks for your interest. Here's how to contribute.

## Adding a new skill

1. Create a directory under `skills/` with your skill name (kebab-case)
2. Add a `SKILL.md` file following this structure:

```yaml
---
name: your-skill-name
description: When this skill activates — include trigger phrases and contexts
metadata:
  version: 1.0.0
---

# Skill Title

[Your structured protocol here]
```

3. The skill should define:
   - **When it activates** — clear trigger conditions in the description
   - **What steps it follows** — numbered protocol, not vague advice
   - **What output it produces** — structured format, not free-form prose
   - **Rules** — guardrails that keep the skill focused

4. Test your skill by invoking it with a realistic scenario
5. Submit a PR with the skill and a changelog entry

## Improving existing skills

- Found an edge case a skill doesn't handle? Fix it.
- Know a better protocol for an existing workflow? Propose it.
- Keep changes focused — one skill per PR.

## Style guide

- Skills are protocols, not essays. Use structured formats (checklists, tables, code blocks).
- Be specific. "Validate input" is useless. "Check for null, empty string, negative numbers, and type coercion" is actionable.
- Every skill should work standalone — no cross-skill dependencies required.
- No filler. If a section doesn't add value, cut it.

## What not to submit

- Skills that are just prompt templates with no structure
- Skills that duplicate existing ones without meaningful improvement
- Overly abstract "meta-skills" that don't produce concrete output
