---
name: setup-english-artifacts
description: Creates `docs/agents/artifact-language.md` and adds an artifact language entry to CLAUDE.md/AGENTS.md so the `english-artifacts` policy is active on every new conversation automatically. Run once per repo before using `english-artifacts`, or to update the conversation language.
---

# Setup English Artifacts

Bootstrap the per-repo language configuration that the `english-artifacts` skill reads.

Two writes, one question: `docs/agents/artifact-language.md` stores the language config; `CLAUDE.md` (or `AGENTS.md`) makes the policy load automatically on every conversation.

## Process

### 1. Explore

Check the current repo state before asking anything:

- Does `docs/agents/artifact-language.md` already exist? If yes, read and show its current content.
- Does `CLAUDE.md` exist at the repo root?
- Does `AGENTS.md` exist at the repo root?
- Does either file already have an `## Agent skills` section? If yes, read and show it.
- Note whether `docs/agents/` exists (informs what you'll create).

### 2. Ask

Ask the user one question:

> "Which language should I use for our conversation? Artifacts (CLAUDE.md, specs, code, commits, PRs) will stay in English. Just tell me the conversation language — e.g. Portuguese (pt-BR), Spanish, French."

If `artifact-language.md` already exists, warn the user that proceeding will overwrite the current config and confirm before continuing.

### 3. Confirm

Show the exact content that will be written:

1. `docs/agents/artifact-language.md` — use the bundled template at [artifact-language.md](./artifact-language.md) with `<conversation-language>` replaced by the user's answer.
2. The `## Agent skills` block to be added or updated in `CLAUDE.md` / `AGENTS.md` (see step 4 for which file).

Let the user review both before writing.

### 4. Write

**Write `docs/agents/artifact-language.md`:**

Create `docs/agents/` if it doesn't exist. Write the file with the confirmed content.

**Update `CLAUDE.md` or `AGENTS.md`:**

Pick the file using this priority:

- If `CLAUDE.md` exists → edit it.
- Else if `AGENTS.md` exists → edit it.
- If neither exists → ask the user which one to create. Do not pick for them.

Never create `AGENTS.md` when `CLAUDE.md` already exists (or vice versa).

If an `## Agent skills` section already exists in the chosen file, add or update the `### Artifact language` subsection in-place. Do not overwrite unrelated sections or append a duplicate block.

If no `## Agent skills` section exists, append one at the end of the file:

```markdown
## Agent skills

### Artifact language

Persistent artifacts stay in English; conversation stays in <conversation-language>. See `docs/agents/artifact-language.md`.
```

### 5. Done

Tell the user:

- `docs/agents/artifact-language.md` was created (or updated)
- `CLAUDE.md` / `AGENTS.md` was updated — the policy will now load automatically on every new conversation, no slash command needed
- They can edit `docs/agents/artifact-language.md` directly at any time; re-running this skill is only needed to start over
- If `english-artifacts` isn't installed yet in this agent, run: `npx skills@latest add joserobertomi/skills` and select it
