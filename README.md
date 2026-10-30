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

## Install as a plugin

The repository is also a plugin for coding agents. Each plugin install adds the five skills plus the HoneyHive docs MCP server (`https://docs.honeyhive.ai/mcp`).

| Agent | Command or action |
|---|---|
| Claude Code | `/plugin install honeyhive --marketplace honeyhiveai/skills` (or `claude plugin marketplace add honeyhiveai/skills` then `claude plugin install honeyhive@honeyhive`) |
| Codex / ChatGPT desktop | `codex plugin marketplace add honeyhiveai/skills`, then install `honeyhive` from the plugin list |
| GitHub Copilot CLI | `copilot plugin install honeyhive@awesome-copilot` (after the listing is approved) |
| Cursor | Install `honeyhive` from the Cursor Marketplace (after the listing is approved) |
| Antigravity CLI | `agy plugin install https://github.com/honeyhiveai/skills` |
| Gemini CLI | `gemini extensions install https://github.com/honeyhiveai/skills` |
| Kiro | Powers panel, Add Custom Power, Import power from GitHub, paste `https://github.com/honeyhiveai/skills` |
| Any agent (skills only) | `npx skills add honeyhiveai/skills --skill '*'` |

## What the plugin runs and sends

- **Docs MCP server:** connects to `https://docs.honeyhive.ai/mcp` (no sign-in). Tools: `search_honey_hive_ai_docs` and `query_docs_filesystem_honey_hive_ai_docs` (read-only), and `submit_feedback`, which sends documentation feedback to the HoneyHive docs site (hosted by Mintlify).
- **Installs:** the skills may install the `honeyhive` CLI (Homebrew tap `honeyhiveai/tap` or the release install script in `honeyhiveai/honeyhive-cli`, which verifies a SHA256) and HoneyHive SDK and OpenTelemetry instrumentation packages from PyPI or npm into your project.
- **Data:** the skills send trace, session, experiment and project data only to the HoneyHive API you set in `HH_API_URL` or `HH_DATA_PLANE_URL`, authenticated with your `HH_API_KEY`. The plugin has no hooks and runs nothing in the background.

## Support and privacy

- Support: [GitHub issues](https://github.com/honeyhiveai/skills/issues) or support@honeyhive.ai
- Privacy policy: https://www.honeyhive.ai/legal/privacy-policy
- Terms of service: https://www.honeyhive.ai/legal/terms-of-service

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
