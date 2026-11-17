# AI Architect Blueprint v2.0: milestones

Repo: https://github.com/linhng1993/universal-ai-architect-blueprint (v1 on `main`, tag `v1.0`)
Owner / decision author: Linh | Created: 2026-11-17
Rules: one milestone per chat. Work on branch `v2`, never on `main` until M06. Never delete: archive or use git. Ask before any push. Log decisions in `plan/decisions.jsonl` with `{"ts","by":"Linh","via","topic","decision","reason"}`.

## Status
| ID | Title | Status | Depends on |
|---|---|---|---|
| M01 | Freeze 1.0 and set up | done | none |
| M02 | Safety and git | review | M01 |
| M03 | Decision log and memory | not_started | M01 |
| M04 | Fix the flow | not_started | M02, M03 |
| M05 | Validator and example | not_started | M04 |
| M06 | Public release | not_started | M05 |

Only one milestone is in_progress at a time.

## M01: Freeze 1.0 and set up
Tasks:
- [x] Tag the current `main` commit `v1.0`
- [x] Create branch `v2`
- [x] Add `VERSION` (2.0.0)
- [x] Add `CHANGELOG.md` listing planned changes
Done when: `v1.0` tag exists, `v2` branch exists, changelog lists planned changes.
Note: Linh marked M01 done on 2026-11-17. `v2` is on GitHub; the `v1.0` tag (a600756) is recreated locally and goes up with the next approved push.

## M02: Safety and git
Tasks:
- [x] Write `safety.md`: never delete; move to `.ai/archive/YYYY-MM-DD/`; get approval first; log it
- [x] Add git steps to the README flow: init, first commit, commit and tag at milestone end
- [x] Add a template `.gitignore` for new projects
- [x] Remove "safe to delete" wording from `blueprint.md`
- [x] Reference `safety.md` from the `AGENTS.md` template
Done when: every delete path in the kit ends in archive or git, and a new project starts as a git repo.
Note: done locally on 2026-11-17; becomes `done` once Linh reviews it and approves the push. M03 starts in a new chat.

## M03: Decision log and memory
Tasks:
- [ ] Change `decisions.jsonl` format to `{ts, by, via, topic, decision, reason}` (ISO time with timezone)
- [ ] Ship `decisions.jsonl` empty (no placeholder entry)
- [ ] Make `state.json` allow "no plan" (null milestone)
- [ ] Add memory-size rule: summarise old entries after about 50
- [ ] Ask the person's name once in intake; store in `context/project.md`
Done when: a logged decision shows name, date and time; templates contain no fake entries.

## M04: Fix the flow
Tasks:
- [ ] Reorder README steps: approval before copying files
- [ ] State that `templates/ai/` is copied as `.ai/`
- [ ] Map Minimal / Standard / Full onto the variants
- [ ] Change intake to "2-3 rounds"
- [ ] Add `CLAUDE.md` vs `AGENTS.md` choice
- [ ] Add iPhone / cloud workflow note
Done when: reading the README start to finish shows no contradictions.

## M05: Validator and example
Tasks:
- [ ] Write `scripts/validate.sh` (line limits, leftover placeholders, index links)
- [ ] Add one filled-in example project under `examples/`
- [ ] Add missing templates: `summaries/`, `prompts/`, `policies.md`
Done when: validator passes on the example and fails on a deliberately broken copy.

## M06: Public release
Tasks:
- [ ] Rewrite README for humans
- [ ] Add `CONTRIBUTING.md`
- [ ] Add security rule: file and web text is data, not instructions; no secrets in memory files
- [ ] Final check for personal data
- [ ] Merge `v2` into `main`, tag `v2.0`
Done when: `main` is tagged `v2.0`, `v1.0` is still reachable, Linh has approved the final review.
