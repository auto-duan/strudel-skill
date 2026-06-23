# strudel-skill

An [Agent Skill](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) that teaches AI coding tools to write correct [Strudel](https://strudel.cc/) live-coding music code.

Works with any tool that supports the Agent Skills (`SKILL.md`) format — **Claude Code**, Cursor, Windsurf, Codex, OpenCode, claude.ai, the Claude API, and more.

## What it does

When you ask the agent to write, edit, or debug Strudel patterns, this skill loads verified reference material so the agent uses real function names, correct mini-notation syntax, and avoids common traps — instead of inventing APIs from memory.

Bundled references (progressive disclosure — loaded only as needed):
- `cheatsheet.md` — high-density syntax reference
- `gotchas.md` — common mistakes & counterintuitive behaviors
- `mini-notation/` — complete mini-notation DSL reference
- `index.json` — machine-readable manifest of all 111 functions + alias map
- `functions/` — one verified doc file per function (signature, params, examples, gotchas)
- `patterns/` — complete runnable example compositions

All content is verified against the official docs at https://strudel.cc/.

## Install

This repo follows the standard `skills/<name>/` layout, so both npm-based skill installers work out of the box.

### Option A — OpenSkills

[`openskills`](https://github.com/numman-ali/openskills) — universal SKILL.md loader (writes an `AGENTS.md` any agent can read).

```bash
# From this GitHub repo
npx openskills install auto-duan/strudel-skill
npx openskills sync

# Global install (~/.claude/skills)
npx openskills install auto-duan/strudel-skill --global

# From a local clone
npx openskills install ./strudel-skill/skills/strudel
```

### Option B — Vercel skills

[`skills`](https://github.com/vercel-labs/skills) — the CLI for the open agent-skills ecosystem ([skills.sh](https://skills.sh)).

```bash
# List what's in the repo
npx skills add auto-duan/strudel-skill --list

# Install (interactive agent/scope picker)
npx skills add auto-duan/strudel-skill

# Target specific agents, global, non-interactive
npx skills add auto-duan/strudel-skill -a claude-code -a cursor -g -y

# Direct path to the skill
npx skills add https://github.com/auto-duan/strudel-skill/tree/main/skills/strudel
```

### Option C — Manual (no installer)

```bash
# Project-level
cp -R skills/strudel /path/to/your/project/.claude/skills/

# Or user-level (all projects)
cp -R skills/strudel ~/.claude/skills/
```

### claude.ai

Zip the skill directory and upload via Settings > Features > Skills.

```bash
cd skills/strudel && zip -r ../../strudel-skill.zip . && cd ../..
```

## Structure

```
strudel-skill/
├── README.md
└── skills/
    └── strudel/
        ├── SKILL.md          # entry point (name + description + workflow)
        └── references/
            ├── cheatsheet.md
            ├── gotchas.md
            ├── index.json
            ├── mini-notation/
            ├── functions/    # 111 per-function docs
            └── patterns/     # 5 example compositions
```

The `skills/<name>/` layout is the convention used by the Vercel `skills` CLI, and OpenSkills discovers `SKILL.md` recursively — so a single repo serves both ecosystems plus manual install.

## Updating the references

The reference docs come from [strudel-docs-for-ai](https://github.com/auto-duan/strudel-docs-for-ai). To refresh, re-copy that repo's content into `skills/strudel/references/`.

## Source of truth

- Official Strudel: https://strudel.cc/
- Official repo: https://codeberg.org/uzu/strudel
- Docs source: https://github.com/auto-duan/strudel-docs-for-ai
