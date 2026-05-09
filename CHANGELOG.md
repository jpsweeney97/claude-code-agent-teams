# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project follows [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.1.0] - 2026-05-08

### Added

- **Agent-team-powered skills** (5 skills): `claude-md`, `design-review-team`, `explore-repo`, `handbook`, `readme`.
- Marketplace catalog at `.claude-plugin/marketplace.json` for one-line install.
- README with namespacing, Requirements, and install/use sections; CONTRIBUTING.md with maintenance flow and standalone-plugin design principle; MIT license.

### Notes

- This plugin originated from the `claude-code-skills` v0.2.0 split. The 5 skills here were extracted from that repo (which trimmed to its solo skills) — see the [`claude-code-skills` CHANGELOG](https://github.com/jpsweeney97/claude-code-skills/blob/main/CHANGELOG.md) for context.
- All skills require Claude Code v2.1.32+ and `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1`. See README Requirements section.
- Versioning is SHA-driven (no `version` field in `plugin.json`); every commit is a new release for plugin marketplace consumers, so install updates pull the latest published state automatically.
