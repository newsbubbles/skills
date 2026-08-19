# skills

Agent skills by [newsbubbles](https://github.com/newsbubbles). Each skill lives under `skills/<name>/` — a `SKILL.md` (frontmatter: `name` + triggering `description`) plus optional `references/`, `scripts/`, and `evals/`. Follows the [Agent Skills spec](https://agentskills.io/specification).

## Skills

- **[ui-taste](skills/ui-taste/SKILL.md)** — Picks the stack and visual direction for any web UI. Infers one of nine taste maps from intent, asks at most one small question batch up front, then locks a **Taste Contract** — a structured artifact written before any code and compiled into design tokens — so the result looks deliberately designed instead of AI-default. Ships a ban list of generated-look tells.

## Install

As a plugin (Claude Code):

```
/plugin marketplace add newsbubbles/skills
/plugin install ui-taste@newsbubbles-skills
```

Or manually — clone and copy (or junction/symlink) a skill into `~/.claude/skills/` for all projects, or `<project>/.claude/skills/` for one:

```powershell
New-Item -ItemType Junction -Path "$env:USERPROFILE\.claude\skills\ui-taste" -Target "<repo>\skills\ui-taste"
```

```bash
ln -s "$(pwd)/skills/ui-taste" ~/.claude/skills/ui-taste
```

## Adding a skill

1. `skills/<name>/SKILL.md` — the dir name must equal the frontmatter `name` (lowercase, hyphens). The `description` is the trigger: what it does AND when to use it; pushy beats subtle; end with what it's *not* for.
2. Keep `SKILL.md` under ~500 lines; push bulk into `references/*.md` with pointers on when to read each.
3. Structural beats prose: if a step must happen, make the skill demand an artifact (a contract, a checklist output, a script run), not just describe intent.
4. Put 2–3 realistic test prompts in `evals/evals.json`, and test discriminatively: the case that matters is the one where the model's default *differs* from what the skill demands. Baseline-without-skill first.
5. Add the skill to the README list and to `.claude-plugin/marketplace.json`.

Eval workspaces (`*-workspace/`) are gitignored scratch output from test runs.

## License

MIT
