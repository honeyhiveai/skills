# HoneyHive Agent Skills

HoneyHive's official [Agent Skills](https://agentskills.io) — portable, version-controlled procedural knowledge for AI coding agents.

This repo is the public distribution point. The source-of-truth lives in HoneyHive's internal monorepo and syncs here automatically on release.

## Installation

```sh
gh skill install honeyhiveai/skills <skill-name>
```

Requires `gh` ≥ 2.91.0. Installs into the per-host directory for your agent (Claude Code, Copilot, Cursor, Codex, Gemini CLI, etc.) — see `gh skill install --help` for `--agent` and `--scope` options.

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
