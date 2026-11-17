# AI Architect Blueprint

A reusable kit for designing a token-efficient project structure ("small map, load on demand").
The AI reads a tiny index first and opens only the one file it needs.

## When the user says "create an AI architecture for a new project"
Follow these steps in order. Do NOT load every file in this kit.

1. Read `intake.md`. Ask its multiple-choice questions with AskUserQuestion (2 rounds).
2. Read `variants.md`. Pick the variant that fits (coding / research / assistant / content / data).
3. Read `blueprint.md` for the full layout, then drop or add folders per the variant.
3b. For any project longer than one chat, read `milestones.md` and include `plan/` (milestones, or curriculum modules).
4. Copy files from `templates/` into the new project. Fill every `{placeholder}`.
   Always include `safety.md` (copy as `.ai/safety.md`) and `templates/gitignore` (copy as `.gitignore`).
   Never overwrite a file that already exists; follow `safety.md`.
5. Check the result against `principles.md`.
6. Show the user the final tree (with data type, purpose, how the AI uses each item) and a 5-line summary. Create files only after they approve.
7. Git (see below): set up the repo before the first file is written; commit when the files are in place.

## Git (every project is a git repo)
- Before writing any file: if the folder is not a git repo, run `git init`. If it already holds files,
  commit them first: `git add -A && git commit -m "Before AI architecture"`.
- First commit after the files are created: `git add -A && git commit -m "Add AI architecture (blueprint <VERSION>)"`.
- End of each milestone: commit, then tag: `git tag -a M0X-done -m "M0X: <title>"`.
- Ask before any `git push`. If git is not installed, tell the user and log it in `decisions.jsonl`; do not skip silently.
- Never delete files: archive them (`safety.md`).

## Files in this kit
| File | Load when |
|---|---|
| intake.md | always, step 1 |
| variants.md | always, step 2 |
| blueprint.md | step 3 |
| milestones.md | step 3b (multi-chat projects, curricula) |
| principles.md | step 5 |
| safety.md | step 4 (copied into every project), and before removing anything |
| templates/* | step 4, only the files the chosen variant needs |
