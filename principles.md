# Token-saving principles

| Principle | How to apply |
|---|---|
| Progressive disclosure | Entry file -> index -> one file |
| Structured over prose | JSON, JSONL, bullets use ~30-50% fewer tokens than paragraphs |
| Retrieve, don't stuff | Embeddings/summaries return 3-5 chunks, not whole documents |
| Code does the work | Scripts/queries compute over big data and return only the result |
| Stable prefix first | Keep AGENTS.md and context identical between calls so prompt caching is cheap |
| Append-only memory | Log decisions once, search them later |
| Strict schemas | Fixed output formats avoid rambling and retries |

## Rules
1. AGENTS.md and index.md stay under ~100 lines each (paid on every call).
2. One topic per file, descriptive file name (AI can choose from the name alone).
3. Conclusion first in every file, so the AI can stop reading early.
4. Summarize and archive old sessions regularly.
5. Anything generated goes in cache/ (rebuildable, no maintenance).
6. Never preload docs/, data/ or src/. Reach them through the index.
7. One milestone per chat. Finished milestone -> write handoff.md -> suggest a new chat. Long chats cost more and drift.
