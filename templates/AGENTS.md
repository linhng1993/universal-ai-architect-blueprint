# {project_name}
{one_line_goal}

## Rules
- Never delete anything. To remove a file, follow `.ai/safety.md`: ask first, move it to `.ai/archive/YYYY-MM-DD/`, log it. Ask before any `git push`.
- Read `.ai/index.md` first; open only the file you need.
- Follow `.ai/context/conventions.md` before writing anything.
- Update `.ai/memory/state.json` at the end of each session.
- Log decisions in `.ai/memory/decisions.jsonl`: append one JSON line per decision, never edit old lines:
  `{"ts":"2026-01-31T14:05+01:00","by":"<who decided>","via":"<tool>","topic":"<one word>","decision":"<what>","reason":"<why>"}`
  - `ts`: read the clock, never guess (`date +%Y-%m-%dT%H:%M%:z`; PowerShell `Get-Date -Format yyyy-MM-ddTHH:mmzzz`). No clock: ask.
  - `by`: the person who decided (Owner in `.ai/context/project.md` unless someone else did). `via`: e.g. claude-code, claude-app, claude-cloud.
- Memory size: when `decisions.jsonl` or `learned.md` passes about 50 entries, ask first, then write a 10-20 line summary to
  `.ai/memory/summaries/<file>-to-YYYY-MM-DD.md`, archive the full file (`.ai/safety.md`), keep the newest ~10 entries, log it (topic `archive`).
- Never read `data/raw/` or `docs/` in full; search or query instead.
- Answer concisely; conclusion first.
- Start of chat: read `.ai/plan/handoff.md` (if any) and `.ai/memory/state.json`. `active_milestone: null` means no plan; otherwise open only that milestone.
- When a milestone is done: update roadmap + handoff, commit, tag `M0X-done`, then tell the user to start a NEW chat for the next milestone.
