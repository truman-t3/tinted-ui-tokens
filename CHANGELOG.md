# Changelog

All notable changes to this project are documented here. The format is based on
[Keep a Changelog](https://keepachangelog.com/), and this project adheres to
[Semantic Versioning](https://semver.org/).

## [1.1.0] - 2026-07-18

### Added
- `LICENSE` (MIT) — the repository now ships an explicit license file (README
  already declared MIT; the file was missing).
- `CHANGELOG.md` — release history.
- `CONTRIBUTING.md` — contribution guidelines.

### Changed
- `SKILL.md` `name:` synced from `tinted-ui-tokens` to `tinted-ui-tokens-skills`
  so it matches the repository slug.
- Cursor rule file renamed `tinted-ui-tokens.mdc` → `tinted-ui-tokens-skills.mdc`
  to match the slug; the Cursor README references were updated accordingly.

## [1.0.0] - 2026-07-11

### Added
- Initial release: brand-agnostic tinted design-token generator
  (`scripts/generate_tokens.py`).
- `SKILL.md` (WorkBuddy / Claude Code) plus `INSTRUCTIONS.md` (agent-neutral
  core instructions).
- Cross-agent wiring docs under `agents/` for Claude Code, Cursor,
  OpenAI Codex, Cline, Aider, WindSurf, GitHub Copilot, and Gemini CLI.
- `references/principles.md` distilling the essay 《你的UI廉价，错在颜色》.
- GitHub Actions CI (`validate.yml`) running frontmatter + smoke + semantic
  sanity checks.
- Bilingual README with a cross-agent compatibility table.
