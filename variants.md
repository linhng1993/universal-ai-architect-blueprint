# Variants (pick one after intake)

## Coding
Keep: AGENTS.md, .ai/index, context (project, architecture, conventions), memory, tools, src/, docs/.
Add: tests notes in conventions.md; scripts/ for build/test commands.
Drop: data/, embeddings (unless the repo is huge).

## Research / thesis / writing
Keep: context (project, glossary), memory (decisions, learned, summaries), skills (per workflow step), docs/.
Add: sources/ (one note per source, JSON metadata), cache/file-summaries.json, embeddings if >50 sources.
Drop: src/, tools/.

## Company assistant
Keep: context, memory, prompts, schemas, tools/registry.json, skills, logs.
Add: policies.md (what the AI must never do), embeddings over company docs.
Drop: src/ unless it ships code.

## Content / marketing
Keep: context (brand voice, audience), prompts, schemas, memory/learned.
Add: examples/ (approved samples), calendar.json.
Drop: embeddings, src/.

## Data analysis
Keep: data/raw + data/processed, cache/results, scripts, schemas, memory/decisions.
Add: data dictionary in glossary.json.
Rule: AI queries data with code and reports only results.
