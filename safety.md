# Safety: never lose work

Conclusion: the AI never deletes. It moves files to `.ai/archive/YYYY-MM-DD/`, asks first, and logs it.
Copy this file into every new project as `.ai/safety.md`. `AGENTS.md` points to it.

## Rules
1. Never delete a file or folder. This includes `rm`, emptying a file, `git rm`, `git clean`,
   and overwriting a file you have not read.
2. To remove something, move it to `.ai/archive/YYYY-MM-DD/<original path>` (today's date, same
   relative path, so it is easy to restore).
3. Ask first. Name every file and say why. Move nothing until the person says yes.
4. Log every archive move in `.ai/memory/decisions.jsonl` with topic `archive`
   (what moved, where to, why).
5. The archive is kept in git. Nobody reads it except to restore a file.

## Setting up a new project in an existing folder
- Never overwrite an existing file (for example an old `CLAUDE.md` or `README.md`).
  Merge into it, or archive it first under rule 2 and 3.
- Commit the folder as it is before writing anything, so the starting state is in git (see README).

## Git
- Commit before a large edit, so the old version is in history.
- Without approval, never run: `git reset --hard`, `git clean`, `git push --force`, `git branch -D`,
  `git rebase` on a pushed branch, `git checkout -- <file>` on uncommitted work.
- Always ask before any `git push`.
- Removing a file that is already committed: still archive it (rule 2). Use `git rm` only if the
  person explicitly asks for it, and log it.

## Generated files (`.ai/cache/`)
- Rebuild in place with the script that made them. Do not clear the cache yourself.
- To free space, ask; then archive under rule 2. If the archived files are large (over ~10 MB),
  ask whether to add that archive folder to `.gitignore`.
