# {project_name}
{one_line_goal}

## Rules
- Read `.ai/index.md` first; open only the file you need.
- Follow `.ai/context/conventions.md` before writing anything.
- Update `.ai/memory/state.json` at the end of each session.
- Log decisions in `.ai/memory/decisions.jsonl` (append only).
- Never read `data/raw/` or `docs/` in full; search or query instead.
- Answer concisely; conclusion first.
- Start of chat: read `.ai/plan/handoff.md` and `.ai/memory/state.json`, open only the active milestone.
- When a milestone is done: update roadmap + handoff, then tell the user to start a NEW chat for the next milestone.
