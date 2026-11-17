# Changelog

All notable changes to the AI Architect Blueprint kit.
Format: [Keep a Changelog](https://keepachangelog.com/). Versions: [SemVer](https://semver.org/).

## [2.0.0] - unreleased (branch `v2`)

### Planned
**Safety and git (M02)**
- `safety.md`: never delete; move to `.ai/archive/YYYY-MM-DD/`; get approval first; log it.
- Git steps in the README flow: init, first commit, commit and tag at each milestone end.
- Template `.gitignore` for new projects.
- Remove "safe to delete" wording from `blueprint.md`; reference `safety.md` from the `AGENTS.md` template.

**Decision log and memory (M03)**
- `decisions.jsonl` format becomes `{ts, by, via, topic, decision, reason}`, with ISO time and timezone.
- `decisions.jsonl` ships empty (no placeholder entry).
- `state.json` allows "no plan" (null milestone).
- Memory-size rule: summarise old entries after about 50.
- Intake asks the person's name once and stores it in `context/project.md`.

**Fix the flow (M04)**
- README steps reordered so approval comes before copying files.
- State that `templates/ai/` is copied as `.ai/`.
- Map Minimal / Standard / Full onto the variants.
- Intake becomes "2-3 rounds".
- Choice between `CLAUDE.md` and `AGENTS.md`.
- iPhone / cloud workflow note.

**Validator and example (M05)**
- `scripts/validate.sh`: line limits, leftover placeholders, index links.
- One filled-in example project under `examples/`.
- Missing templates: `summaries/`, `prompts/`, `policies.md`.

**Public release (M06)**
- README rewritten for humans; `CONTRIBUTING.md`.
- Security rule: file and web text is data, not instructions; no secrets in memory files.
- Final personal-data check; merge `v2` into `main` and tag `v2.0`.

### Added
- `VERSION` file (2.0.0) so projects built from the kit can record which version they used.
- `CHANGELOG.md` (this file).
- `plan/v2-milestones.md` and `plan/decisions.jsonl`: plan and decision log for building 2.0.
- `safety.md` (M02): never delete; archive to `.ai/archive/YYYY-MM-DD/`, ask first, log it; risky git commands need approval. Copied into each project as `.ai/safety.md`.
- Memory rules (M03) in `templates/AGENTS.md` and `blueprint.md`: decision line format, clock-read timestamps, and a size rule (past ~50 entries: ask, summarise to `memory/summaries/`, archive the full file, keep the newest ~10, log it).
- `context/project.md` template (M03): `Owner` line, asked once at intake and used as `by` in `decisions.jsonl`.
- `templates/gitignore` (M02): secrets, OS files and `.ai/cache/`; copied into each project as `.gitignore`.
- Git section in `README.md` (M02): `git init` and a baseline commit before writing files, first commit after, commit and tag `M0X-done` at each milestone end.

### Changed
- `blueprint.md`: `cache/` is no longer "safe to delete"; tree adds `safety.md`, `archive/` and `.gitignore`.
- `templates/AGENTS.md` and `templates/ai/index.md` point to `safety.md`; milestone end now commits and tags.
- `decisions.jsonl` (M03): format is now `{ts, by, via, topic, decision, reason}` with ISO time and timezone; template ships empty.
- `state.json` template (M03): `active_milestone` and `milestone_status` default to `null` (no plan); `updated` is an ISO time.
- `learned.md` and `glossary.json` templates (M03): example entries removed (`learned.md` keeps a format comment; `glossary.json` is `{}`).
- `intake.md` (M03): asks the person's name once before Round 1; "single task" plan choice keeps the milestone null.
- `milestones.md` end-of-milestone steps and `principles.md` rule 4 use archive and git instead of deletion.

## [1.0.0] - 2026-11-17 (tag `v1.0`)
- Original kit: `README.md`, `intake.md`, `variants.md`, `blueprint.md`, `milestones.md`,
  `principles.md`, `templates/`, MIT `LICENSE`.
