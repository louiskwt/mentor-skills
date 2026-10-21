# Skills for Turning your Agents into Your Personal Mentor

This repo is a collection of skills that one can use to build projects and learn from agents as if you're working from a mentor with senior-level experience.

## Skills

| Skill                               | Description                                                                                                                                                                                                                                                                                 |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [swe-mentor](./swe-mentor/SKILL.md) | Acts as a senior-engineer mentor. Guides a junior developer through designing, building, debugging, and reviewing a project — sets direction, challenges the process, reviews for quality, efficiency, and security, and escalates deliberately instead of handing over the implementation. |

## Layout

Every skill follows the same shape, which is what makes it portable across agents:

```
<skill-name>/
  SKILL.md              # required: frontmatter + instructions
  templates/            # optional: supporting files the skill copies or reads
```

Two rules make a skill load correctly:

- The file must be named `SKILL.md`, exactly — the filename is case-sensitive.
- The `name` field in the frontmatter must be lowercase-hyphenated and match the folder name.

## Install

Skills are loaded once at startup, so restart your agent after installing or editing one.

**opencode** — copy the skill folder into a skills directory:

```bash
# global, for every project
cp -r swe-mentor ~/.config/opencode/skills/

# or project-scoped
cp -r swe-mentor .opencode/skills/
```

Or point opencode at this repo without copying anything, via `opencode.json`:

```json
{
  "$schema": "https://opencode.ai/config.json",
  "skills": {
    "paths": ["./swe-mentor"]
  }
}
```

**Claude Code** — auto-loaded from `~/.claude/skills/`:

```bash
cp -r swe-mentor ~/.claude/skills/
```

**Any agent that reads `~/.agents/skills/`** (opencode, and others that follow the same convention):

```bash
cp -r swe-mentor ~/.agents/skills/
```

## Learner Profile

The `swe-mentor` skill keeps a per-mentee profile so guidance adapts across sessions instead of restarting from scratch each time. It resolves in this order:

1. `<project>/.mentor/LEARNER.md` — project-scoped, travels with the repo
2. `~/.mentor/LEARNER.md` — user-scoped, follows the mentee across projects

Copy [the template](./swe-mentor/templates/LEARNER.template.md) to one of those paths to bootstrap it. The profile holds level, goals, weak spots, and settled decisions — never secrets or private client details.

## Contributing

Add a skill as a new folder at the repo root, named after the skill, containing a `SKILL.md`. Keep the frontmatter tight: `name` matching the folder, and a third-person `description` that covers both what the skill does and when it should trigger, with concrete trigger keywords front-loaded.
