# Contributing

## Issues

Issues welcome — bug reports, install problems, behavior questions, and feature suggestions. Open one freely; minimal template needed (what you tried, what happened, what you expected).

## Pull requests

Reviewed case-by-case. Small fixes (typos, doc clarifications, broken-link corrections, obvious bugs in skill instructions) are welcome and likely to merge fast. Larger changes — substantive skill rewrites, new skills, structural changes — please open an issue first to align on scope before opening the PR.

## Cross-plugin references

This plugin is designed to be standalone. A user who installs only this plugin gets a fully functional plugin — no skill operationally depends on a skill from another plugin.

When contributing a new skill or modifying an existing one, do not introduce operational references in skill content (`SKILL.md` body, `references/`, `examples/`) that point at skills in another plugin. Operational references include "use X instead", "see X for Y", redirect rules in skill bodies, or required cross-skill workflows.

User-facing discovery aids (README "See also" sections, CHANGELOG migration notes) are exempt — these don't create operational dependencies.

If you find yourself wanting an operational reference to a sibling-plugin skill, the right action is one of: inline the relevant content, drop the reference, or propose merging the two plugins. Do not add the cross-reference.

## Out of scope

This repo is a curated subset of a larger personal collection of Claude Code skills, many of which are still in-progress experiments. Only skills polished and validated for public use are published here. Requests to publish other skills are welcome as feature requests but treated as low-priority — the curation gap is intentional, not an oversight.

Solo (non-team) skills belong in the companion [`claude-code-skills`](https://github.com/jpsweeney97/claude-code-skills) plugin, not here. Feature requests for solo skills should be opened in that repo.

## Maintenance

This public repo is canonical for shipped fixes — bug reports get fixed here. Backports to private dev-staging are at maintainer discretion. Versioning is SHA-driven (no `version` field in `plugin.json`); every commit is a new release for plugin marketplace consumers, so install updates pull the latest published state automatically.
