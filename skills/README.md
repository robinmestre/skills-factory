# Skills Development Staging Area

This directory is a **development incubator** for skills in progress.

## Workflow

1. **Develop** — Create new skills here using category folders for organization
2. **Test** — Iterate on skill design and references
3. **Promote** — Move completed skills to `/.claude/skills/` when production-ready

## Structure

```
skills/
├── documentation/    # Doc generation skills
├── evaluation/       # Assessment/scoring skills
├── research/         # Research workflow skills
├── requirements/     # Requirements extraction skills
├── prompts/          # Prompt engineering skills
└── meta/             # Skills about skills
```

Each skill follows the standard structure:
```
skill-name/
├── SKILL.md          # Skill definition and workflow
├── references/       # Domain knowledge and patterns
└── templates/        # Ready-to-use templates
```

## Active Skills

Production-ready skills live in `/.claude/skills/` and are automatically loaded by Claude Code.
