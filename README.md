# skills

A repository of Claude Code skills. Each top-level directory is one skill: a `SKILL.md` with frontmatter (name + triggering description) and body, plus optional `references/`, `scripts/`, and `evals/`.

## Skills

| Skill | What it does |
|---|---|
| [ui-taste](ui-taste/SKILL.md) | Picks the stack and visual direction for any web UI. Infers a taste map from intent, asks at most one small question batch up front, locks a Taste Contract before code, and bans the AI-default look. |

## Installing a skill

Skills load from `~/.claude/skills/` (personal, all projects) or `<project>/.claude/skills/` (that project only). Keep this repo canonical and junction into place — junctions don't need admin on Windows:

```powershell
New-Item -ItemType Junction -Path "$env:USERPROFILE\.claude\skills\ui-taste" -Target "D:\skills\ui-taste"
```

Edits in the repo are live immediately; skills are read fresh each session.

## Adding a skill

1. `mkdir <skill-name>` with a `SKILL.md` — frontmatter `name` and `description` (the description is the trigger: say what it does AND when to use it, pushy beats subtle).
2. Keep `SKILL.md` under ~500 lines; push bulk into `references/*.md` with clear pointers on when to read each.
3. Structural beats prose: if a step must happen, make the skill demand an artifact (a contract, a checklist output, a script run), not just describe intent.
4. Put 2–3 realistic test prompts in `evals/evals.json`.
5. Add a row to the table above.

Eval workspaces (`*-workspace/`) are gitignored — they're scratch output from test runs.
