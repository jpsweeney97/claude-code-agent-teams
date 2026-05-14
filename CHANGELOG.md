# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project follows [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

- **New skill: `tech-debt-audit`** — 6-auditor parallel team (Code Health, Architecture Drift, Dependency & Supply Chain, Test Debt, Operational & Observability, Knowledge & Documentation) producing a prioritized cleanup backlog with severity × leverage × effort scoring, bucketed into quick-wins / high-leverage / strategic / watch.

### Changed

- `tech-debt-audit` lifecycle hardening: explicit Phase 3 preflight for stale workspace and existing-team detection (executable: filesystem inspection of `~/.claude/teams/tech-debt-audit/` plus `TeamCreate`-conflict fallback, since `allowed-tools` has no team-listing tool); mandatory durable report at `docs/audits/YYYY-MM-DD-<target-slug>-debt.md` before any workspace deletion; workspace-preservation invariant overrides cleanup defaults when the durable report is missing or `TeamDelete` reports degraded state; task IDs and `TaskUpdate` obligations now wired into auditor spawn prompts (status normalized to snake_case `in_progress` with full payload spec in `references/agent-teams.md`) so `TaskGet` is a meaningful completion signal.
- `tech-debt-audit` severity rubric tightened: P0 for `bus-factor-1 + undocumented` now requires concrete handoff evidence (announced transition, named successor, near-term deadline, or active blocker) rather than the prior "even if everything else looks fine" wording.
- README now lists 6 skills (was 5); README lead, `plugin.json`, and `marketplace.json` descriptions updated to include tech-debt audit scope, with a `tech-debt` keyword added to `plugin.json`.

## [0.1.0] - 2026-05-08

### Added

- **Agent-team-powered skills** (5 skills): `claude-md`, `design-review-team`, `explore-repo`, `handbook`, `readme`.
- Marketplace catalog at `.claude-plugin/marketplace.json` for one-line install.
- README with namespacing, Requirements, and install/use sections; CONTRIBUTING.md with maintenance flow and standalone-plugin design principle; MIT license.

### Notes

- This plugin originated from the `claude-code-skills` v0.2.0 split. The 5 skills here were extracted from that repo (which trimmed to its solo skills) — see the [`claude-code-skills` CHANGELOG](https://github.com/jpsweeney97/claude-code-skills/blob/main/CHANGELOG.md) for context.
- All skills require Claude Code v2.1.32+ and `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1`. See README Requirements section.
- Versioning is SHA-driven (no `version` field in `plugin.json`); every commit is a new release for plugin marketplace consumers, so install updates pull the latest published state automatically.
