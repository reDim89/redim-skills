# skills

A personal collection of [Claude Code](https://claude.com/claude-code) skills I use day-to-day and am happy to publish. Focus areas:

- **Productivity** — journaling, weekly reviews, personal-knowledge-management workflows (mostly [Tana](https://tana.inc/))
- **Product management** — discovery, specs, review, planning helpers
- **Coding / data analysis** — small, repeatable workflows that don't belong in a one-off prompt

## Layout

```
skills/
  <category>/
    <skill-name>/
      SKILL.md           # the skill itself (frontmatter + instructions)
      [scripts, refs]    # optional supporting files
```

Each `SKILL.md` starts with YAML frontmatter:

```yaml
---
name: skill-name
description: One-line description Claude uses to decide when to load this skill.
---
```

When the description matches what the user is asking for, Claude Code loads the body of `SKILL.md` and follows it.

## Install

Drop the skills into a location Claude Code looks at:

**User-level (available in every project):**

```bash
git clone <this-repo> ~/code/skills
ln -s ~/code/skills/skills/productivity/weekly-summary ~/.claude/skills/weekly-summary
```

**Project-level (only this repo):**

```bash
mkdir -p .claude/skills
ln -s /path/to/this-repo/skills/productivity/weekly-summary .claude/skills/weekly-summary
```

Or just copy the folder instead of symlinking if you'd rather fork the skill locally.

## Index

### Productivity

| Skill | What it does |
| --- | --- |
| [`weekly-summary`](skills/productivity/weekly-summary/SKILL.md) | Generates a weekly reflection from daily Check-in entries and writes a "Weekly outcomes" node back into Tana. |
| [`populate-diary-from-voice`](skills/productivity/populate-diary-from-voice/SKILL.md) | Turns voice-recording transcriptions in Tana calendar days into structured Check-in entries (Mood, Energy, Diary). |

> The productivity skills above are wired to a specific Tana workspace and tag/field IDs. They're useful as templates — swap in your own IDs.

## Contributing / forking

Fork it, take what's useful, adapt what isn't.
