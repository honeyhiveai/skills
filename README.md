# HoneyHive Agent Skills

HoneyHive's official [Agent Skills](https://agentskills.io) — portable, version-controlled procedural knowledge for AI coding agents.

## Requirements

- [Node.js](https://nodejs.org/) 18+ — used to run the [`skills`](https://github.com/vercel-labs/skills) CLI via `npx`.
- [`honeyhiveai/honeyhive-cli`](https://github.com/honeyhiveai/honeyhive-cli) — skill scripts shell out to `honeyhive` for credential validation, trace inspection, and resource operations.

## Install

```sh
# 1. honeyhive-cli — Homebrew (macOS, or Linux if you use Homebrew)
brew tap honeyhiveai/tap
brew install honeyhive

# …or Linux install script (downloads the release binary, verifies SHA256, installs to /usr/local/bin)
# See https://github.com/honeyhiveai/honeyhive-cli for the latest install command.

# 2. set credentials in your env
export HH_API_KEY="<your-project-api-key>"
export HH_API_URL="https://api.dp1.us.honeyhive.ai"   # multi-tenant default; dedicated/self-host customers have their own

# 3. healthcheck — confirms HH_API_URL is reachable and HH_API_KEY is valid
honeyhive events search --filters '[]' --limit 1

# 4. install HoneyHive skills
npx skills add honeyhiveai/skills --skill '*'
```

Installs into the per-agent skills directory (Cursor, Claude Code, Copilot, Codex, etc.) — see `npx skills add --help` for `--agent`, `-g`, and `--global` options.

## Skills

| Skill | What it does |
|---|---|
| [`honeyhive-cli`](skills/honeyhive-cli/SKILL.md) | Install, discover, and use the HoneyHive CLI. Shared reference for the other skills. |
| [`honeyhive-instrument`](skills/honeyhive-instrument/SKILL.md) | Wire HoneyHive tracing into an LLM / agent / RAG application. SDK install, OTEL instrumentation, framework instrumentor selection. |
| [`honeyhive-evaluate`](skills/honeyhive-evaluate/SKILL.md) | Set up and run HoneyHive experiments — datasets, evaluators, run comparison, and regression checks. |
| [`honeyhive-improve`](skills/honeyhive-improve/SKILL.md) | Debug failing agent workflows using HoneyHive trace data and ship minimal, evidence-backed fixes. |
| [`honeyhive-alert-root-cause`](skills/honeyhive-alert-root-cause/SKILL.md) | Investigate HoneyHive Discover alert URLs — decode filters, pull flagged sessions, classify true vs false positives, and recommend guardrails. |

## Resources

- [HoneyHive documentation](https://docs.honeyhive.ai/v2/)
- [Agent Skills specification](https://agentskills.io/specification)
- [`skills` CLI](https://github.com/vercel-labs/skills)

## License

[MIT](LICENSE)
