# Milestones and curriculum system

Use for any project that runs longer than one chat. Work is split into milestones (project)
or modules (curriculum). Each milestone gets a FRESH chat, so context stays small and cheap.

## Folder (inside .ai/)
```
plan/
├── roadmap.json          [JSON] all milestones: id, title, status, depends_on, goal, done_when
│     AI: reads this to see the whole plan in ~1 screen; never loads milestone files it doesn't need
├── handoff.md            [markdown, <40 lines] the baton passed between chats
│     AI: reads FIRST in every new chat after AGENTS.md; rewrites it at milestone end
└── milestones/
    └── M01-<slug>.md     [markdown, <60 lines] scope, tasks checklist, acceptance criteria, notes
          AI: opens only the ACTIVE milestone file
```
Curriculum variant: same files; milestone = module; add `learn_goal`, `exercises`, `check_questions`
to each milestone file, and `mastery` (not_started / learning / practiced / mastered) to roadmap.json.

## Status values (roadmap.json and state.json)
not_started -> in_progress -> blocked | review -> done   (curriculum may add: skipped)
Only ONE milestone is in_progress at a time.
No plan (single-task project): `state.json` has `"active_milestone": null` and `"milestone_status": null`.

## Session protocol
START of every chat:
1. Read AGENTS.md, then plan/handoff.md, then memory/state.json.
2. Open only the active milestone file. Do not load other milestones.
3. Confirm in one line: "Active: M0X, next step: ...". Then work.

DURING: tick tasks in the milestone file; update state.json (status, next_step) after each meaningful step.

END of milestone (all done_when criteria met, or user says done):
1. Set milestone status = done in roadmap.json; set the next milestone to in_progress (or not_started if user wants a break).
2. Append key decisions to memory/decisions.jsonl; new lessons to memory/learned.md.
3. Rewrite plan/handoff.md using templates/ai/plan/handoff.md (what's done, what's next, files touched, open questions, first action for next chat).
4. Commit everything and tag it: `git tag -a M0X-done -m "M0X: <title>"`. Ask before pushing.
5. TELL THE USER to start a new chat:
   "Milestone M0X is complete and the handoff is saved. I suggest starting a new chat for M0Y to keep context small and cheap. Paste this as your first message: 'Continue the project. Read AGENTS.md and .ai/plan/handoff.md, then start M0Y.'"

## When to suggest a new chat (also mid-milestone)
- A milestone just finished (always).
- The chat has grown long (many files read, many turns) or answers start drifting: save handoff, suggest new chat.
- The topic switches to a different milestone or module.
Never start the next milestone in the same chat unless the user insists.

## Sizing rule
A milestone should fit in one chat: 1 clear outcome, 3-8 tasks, verifiable "done when". Split larger ones.
