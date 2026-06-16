# joser-skills

My agent skills for daily engineering work.

## Install

### Claude Code

```bash
npx skills@latest add joserobertomi-itab/skills -a claude-code
```

### Codex

```bash
npx skills@latest add joserobertomi-itab/skills -a codex
```

### Cursor

```bash
npx skills@latest add joserobertomi-itab/skills -a cursor
```

### Interactive (choose agent during install)

```bash
npx skills@latest add joserobertomi-itab/skills
```

## Skills

### [`setup-english-artifacts`](./skills/engineering/setup-english-artifacts/SKILL.md)

Run once per repo. Creates `docs/agents/artifact-language.md` and updates `CLAUDE.md`/`AGENTS.md` so the `english-artifacts` policy loads automatically on every new conversation — artifacts in English, conversation in your language.

## Skills I use from other ecosystems

| Skill | Source |
|---|---|
| `english-artifacts` | `npx skills@latest add joserobertomi/skills` |
| `setup-matt-pocock-skills`, `grill-me`, `tdd`, `to-issues`, and others | `npx skills@latest add mattpocock/skills` |
