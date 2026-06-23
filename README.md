# strudel-skill

An [Agent Skill](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) that teaches AI coding tools to write correct [Strudel](https://strudel.cc/) live-coding music code.

Works with any tool that supports the Agent Skills format — **Claude Code**, claude.ai, the Claude API, etc.

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

### Claude Code

Copy the `strudel/` directory into your skills folder:

```bash
# Project-level (this repo only)
cp -R strudel /path/to/your/project/.claude/skills/

# Or user-level (all projects)
cp -R strudel ~/.claude/skills/
```

Claude Code auto-discovers it. The skill triggers when you mention Strudel, mini-notation, or live-coding music.

### claude.ai

Zip the `strudel/` directory and upload via Settings > Features > Skills.

```bash
cd strudel && zip -r ../strudel-skill.zip . && cd ..
```

## Structure

```
strudel-skill/
├── README.md
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

## Updating the references

The reference docs come from [strudel-docs-for-ai](https://github.com/auto-duan/strudel-docs-for-ai). To refresh, re-copy that repo's content into `strudel/references/`.

## Source of truth

- Official Strudel: https://strudel.cc/
- Official repo: https://codeberg.org/uzu/strudel
- Docs source: https://github.com/auto-duan/strudel-docs-for-ai
