# claude-code-agent-teams

Agent-team-powered [Claude Code](https://code.claude.com) skills for grounded documentation, deep architecture review, and tech-debt audit. Each skill orchestrates a parallel team of subagents that explore a codebase, design, or debt surface from multiple perspectives, then synthesizes findings into a single grounded artifact.

This is the experimental-flag tier — every skill in this plugin requires Claude Code v2.1.32+ and `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1`. For solo (non-team) skills that work without the experimental flag, see the companion plugin [`claude-code-skills`](https://github.com/jpsweeney97/claude-code-skills).

## Namespacing

After install, every skill in this plugin is invocable under the `claude-code-agent-teams` namespace:

```
/claude-code-agent-teams:claude-md
/claude-code-agent-teams:design-review-team
/claude-code-agent-teams:explore-repo
```

This guarantees that names from this plugin can never collide with skills from other plugins or your own personal skills. Manual invocation always wins over auto-routing — if you ever want a specific skill, name it explicitly.

## Requirements

- **Claude Code v2.1.32 or higher.** Check with `claude --version`. The agent-teams primitive used by every skill in this plugin landed in this version. See the [agent teams documentation](https://code.claude.com/docs/en/agent-teams) for background.
- **`CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1`** in your `settings.json` `env` block (or as a shell environment variable). Required for all 6 skills — they hard-stop without the flag.

  > **Note:** The agent-teams feature is experimental. If Anthropic renames the flag or stabilizes the feature in a future release, expect a follow-up release of this plugin. Bug reports against rename/deprecation are welcome.

## What's in here

6 skills, all agent-team-powered:

| Skill | Purpose |
|---|---|
| [`claude-md`](skills/claude-md/SKILL.md) | Create, audit, and update CLAUDE.md files with codebase-grounded accuracy via a parallel exploration team. |
| [`design-review-team`](skills/design-review-team/SKILL.md) | Thorough architecture review using 6 specialized reviewers covering structural+cognitive, behavioral, data, reliability+operational, change, and trust&safety lenses. |
| [`explore-repo`](skills/explore-repo/SKILL.md) | Deeply explore any GitHub repo or local codebase using a 6-teammate exploration team (Cartographer, Architect, Interface Mapper, Toolchain Scout, Domain Analyst, Historian). |
| [`handbook`](skills/handbook/SKILL.md) | Create, audit, and update operational handbooks with a 5-perspective parallel exploration team. |
| [`readme`](skills/readme/SKILL.md) | Create, audit, and improve READMEs grounded in actual project state via a parallel exploration team. |
| [`tech-debt-audit`](skills/tech-debt-audit/SKILL.md) | Thorough tech debt audit using 6 specialized auditors (Code Health, Architecture Drift, Dependency & Supply Chain, Test Debt, Operational & Observability, Knowledge & Documentation), synthesized into a prioritized cleanup backlog with severity × leverage × effort scoring. |

Each skill's `SKILL.md` is the canonical specification — frontmatter declares when Claude should trigger it, and the body is the procedure Claude follows.

## Install

### Try it (clone + dev flag)

For a session-scoped trial without committing to install:

```
git clone https://github.com/jpsweeney97/claude-code-agent-teams
claude --plugin-dir <path-to-clone>
```

The clone is permanent on your filesystem, but Claude only loads the plugin for the session you launched with `--plugin-dir`. Drop the flag next time and the skills disappear from that session.

### Install permanently (marketplace)

For ongoing access across all your sessions:

```
/plugin marketplace add jpsweeney97/claude-code-agent-teams
/plugin install claude-code-agent-teams@jpsweeney97-agent-teams
```

Run those inside a Claude Code session. The first command points Claude at this repo's marketplace manifest; the second installs the plugin from it. After install, every skill is invokable as `/claude-code-agent-teams:<name>`.

## Use a skill

Manual invocation always works:

```
/claude-code-agent-teams:design-review-team
```

Or just describe what you want — the skill's frontmatter trigger phrases will route Claude to the right skill automatically. For example, "thoroughly review this architecture" or "deeply explore this repo" will trigger the matching skill if it's loaded.

## Contributing

Issues are welcome — bug reports, install problems, behavior questions, and feature suggestions. PRs are reviewed case-by-case; small fixes (typos, doc corrections, broken links, obvious bugs) merge fast. For larger changes, please open an issue first.

This public repo is canonical: bug fixes land here, not in any private dev-staging copy. See [CONTRIBUTING.md](CONTRIBUTING.md) for the full policy, including the standalone-plugin design principle (no operational cross-references between this plugin and the companion `claude-code-skills`).

## See also

- [`claude-code-skills`](https://github.com/jpsweeney97/claude-code-skills) — solo skills companion plugin (rigorous review, decisions, and craft). No experimental flag required. This plugin is self-contained — installing the companion plugin is optional, not required.

## License

[MIT](LICENSE).

## Author

[JP Sweeney](https://github.com/jpsweeney97).
