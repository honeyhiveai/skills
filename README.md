# HoneyHive Agent Skills

HoneyHive's official [Agent Skills](https://agentskills.io) — portable, version-controlled procedural knowledge for AI coding agents.

This repo is the public distribution point. The source-of-truth lives in HoneyHive's internal monorepo and syncs here automatically on release.

## Requirements

- [`gh`](https://cli.github.com/) ≥ 2.91.0 with the [`gh skill`](https://agentskills.io) extension — used to install skills.
- [`honeyhiveai/honeyhive-cli`](https://github.com/honeyhiveai/honeyhive-cli) — skill scripts (preflight check, trace check) shell out to `honeyhive` for credential validation and trace inspection.

## Install

```sh
# 1. gh skill extension (see https://agentskills.io for the canonical command)
gh extension install github.com/agentskills/gh-skill

# 2. honeyhive-cli
go install github.com/honeyhiveai/honeyhive-cli@latest

# 3. set credentials in your env
export HH_API_KEY="<your-project-api-key>"
export HH_API_URL="https://api.dp1.us.honeyhive.ai"   # multi-tenant default; dedicated/self-host customers have their own

# 4. healthcheck — confirms HH_API_URL is reachable and HH_API_KEY is valid
honeyhive events search --filters '[]' --limit 1
```

Then install a skill:

```sh
gh skill install honeyhiveai/skills <skill-name>
```

Installs into the per-host directory for your agent (Claude Code, Copilot, Cursor, Codex, Gemini CLI, etc.) — see `gh skill install --help` for `--agent` and `--scope` options.

## Skills

| Skill | What it does |
|---|---|
| [`honeyhive-instrument`](skills/honeyhive-instrument/SKILL.md) | Wire HoneyHive tracing into an LLM / agent / RAG application. SDK install, OTEL-compatible instrumentation, manual session/event construction (TypeScript), framework instrumentor selection (Python). |

More skills (`honeyhive-evaluate`, `honeyhive-improve`) are in progress and will land here as their bodies are authored.

## Resources

- [HoneyHive documentation](https://docs.honeyhive.ai/v2/)
- [Agent Skills specification](https://agentskills.io/specification)

## License

[MIT](LICENSE)
