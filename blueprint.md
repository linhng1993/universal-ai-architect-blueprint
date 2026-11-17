# Blueprint: universal layout

Core idea: entry file -> index -> one file. Cost grows only with need.

```
project/
├── AGENTS.md                  [markdown, <100 lines]
│     For: always-loaded entry point (rules + pointer to the index)
│     AI: reads first every session; nothing else loaded by default
│     (name it CLAUDE.md for Claude Code, AGENTS.md for other tools)
├── .ai/
│   ├── index.md               [markdown, ~50 lines]
│   │     For: map of "what lives where", one line each
│   │     AI: decides which single file to open next
│   ├── safety.md              [markdown, <40 lines] never delete: archive, ask, log
│   │     AI: follows it before removing, moving or overwriting anything
│   ├── context/               (stable knowledge, rarely changes)
│   │   ├── project.md         [markdown] goal, users, scope, non-goals
│   │   │                      AI: loaded once for the "why"
│   │   ├── architecture.md    [markdown + mermaid] components, data flow
│   │   │                      AI: loaded only for structural/design tasks
│   │   ├── conventions.md     [markdown bullets] naming, style, do/don't
│   │   │                      AI: loaded before writing code or text
│   │   └── glossary.json      [JSON {term: definition}]
│   │                          AI: looked up by key, never read whole
│   ├── memory/                (what changes over time)
│   │   ├── state.json         [JSON] current task, status, next step (milestone null = no plan)
│   │   │                      AI: resumes work without re-explaining
│   │   ├── decisions.jsonl    [JSON Lines, append-only, ships empty] ts, by, via, topic, decision, reason
│   │   │                      AI: greps by topic
│   │   ├── learned.md         [markdown bullets] mistakes and fixes
│   │   │                      AI: reads to avoid repeating errors
│   │   └── summaries/         [markdown, 10-20 lines each] compressed history
│   │                          AI: loads a summary, not the full chat
│   ├── plan/                  (milestones or curriculum; see milestones.md)
│   │   ├── roadmap.json       [JSON] all milestones + status
│   │   │                      AI: whole plan at a glance, cheap to read
│   │   ├── handoff.md         [markdown, <40 lines] baton between chats
│   │   │                      AI: read right after AGENTS.md in every new chat
│   │   └── milestones/M01-*.md [markdown] one file per milestone
│   │                          AI: opens only the active one
│   ├── skills/<name>/
│   │   ├── SKILL.md           [markdown + YAML header] when to use + steps
│   │   │                      AI: only the 1-line description is always visible
│   │   └── scripts/           [py/sh] deterministic work AI runs, not reasons through
│   ├── prompts/*.md           [markdown templates with {variables}]
│   │                          AI: fills variables instead of retyping long prompts
│   ├── schemas/*.schema.json  [JSON Schema] shape of inputs/outputs
│   │                          AI: returns strict JSON, no rambling or retries
│   ├── tools/registry.json    [JSON] tool name, one-line purpose, parameters
│   │                          AI: picks the right tool without trial and error
│   ├── cache/                 (generated, rebuild in place; clearing follows safety.md)
│   │   ├── embeddings/        [vector DB / .npy] semantic search; top 3-5 chunks
│   │   ├── file-summaries.json [JSON {path: 2-line summary}] skim before opening
│   │   └── results/           [JSON/parquet] reuse costly computations
│   ├── logs/runs.jsonl        [JSON Lines] what was done, cost, outcome
│   │                          AI: rarely read; used to audit token cost
│   └── archive/YYYY-MM-DD/    [any] files moved away instead of deleted (kept in git)
│                              AI: never reads, except to restore a file
├── .gitignore                 [text] secrets, OS files, .ai/cache/ (from templates/gitignore)
├── docs/                      [markdown] human docs; AI searches on demand
├── src/                       [code] the work product; AI opens by path, partial reads
└── data/
    ├── raw/                   [csv/pdf/etc.] untouched originals; AI never reads directly
    └── processed/             [parquet/jsonl] compact versions; AI queries with code
```

## Memory rules
Templates ship with no example entries; the AI writes only real ones.
- `decisions.jsonl`, one line per decision (time read from the clock, with timezone):
  `{"ts":"2026-11-17T22:05+01:00","by":"Alex","via":"claude-code","topic":"git","decision":"Tag milestones M0X-done","reason":"Easy to find in history"}`
- `by` is the Owner from `context/project.md` (asked once at intake) unless someone else decided.
- Size: past about 50 entries in `decisions.jsonl` or `learned.md`, ask, then summarise the old
  entries into `memory/summaries/`, archive the full file (`safety.md`), keep the newest ~10, log it.

## Tailoring rule
Keep the entry file, index, safety.md, context/, memory/ and .gitignore in every project.
Every project is a git repo from the first session (see README).
Everything else is optional: add it only when the project has a real need.
