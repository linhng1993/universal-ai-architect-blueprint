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

## [1.0.0] - 2026-11-17 (tag `v1.0`)
- Original kit: `README.md`, `intake.md`, `variants.md`, `blueprint.md`, `milestones.md`,
  `principles.md`, `templates/`, MIT `LICENSE`.
