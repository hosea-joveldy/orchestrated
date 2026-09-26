# opencode-orches

A 5-agent [opencode](https://opencode.ai) config: orchestrator, planner, designer, coder, QA — each with its own model and locked-down permissions, so only `@coder` touches code/git and only `@qa` can call something done.

```
@orchestrator (delegates only)
   ├── @planner    — scopes work, writes tasks
   ├── @designer   — design tokens + Stitch specs
   ├── @coder      — implements, tests, commits
   └── @qa         — PASS/FAIL, no fixes
```

Uses Memoir for persistent cross-session memory, TypeUI + Stitch for design tokens/mockups, and Playwright for QA screenshots.

## Setup

1. Install [opencode](https://opencode.ai).
2. Copy `opencode.jsonc` and `prompts/` into `~/.config/opencode`.
3. Put the omniroute API key at `~/.secrets/omniroute-key`.
4. Point the `9router/combo-*` model names at whatever your router exposes.
5. Run `opencode`.

## Customizing

Prompts live in `prompts/*.txt`, one per agent. Permissions (`allow`/`ask`/`deny`) are set per agent per tool in `opencode.jsonc`.

## Problems

- I haven't setup the memoir
- TypeUI might be redundant here
- Some agents prompt are too long
