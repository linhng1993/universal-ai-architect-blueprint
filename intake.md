# Intake (multiple choice)

## How to ask
Use the AskUserQuestion tool. Limits: max 4 questions per call, 2-4 options each.
"Other" (free text) is added automatically, so never add it as an option.
Run 2 rounds. Skip any question the user already answered. If the tool is unavailable, ask the same questions in plain text with lettered options (A/B/C/D + "or write your own").
First, ask the project's one-sentence goal in plain chat (free text) before Round 1.

## Round 1: shape of the project
1. header "Type" | "What kind of project is this?" | single-select
   - Coding / software
   - Research, thesis or writing
   - Company assistant / knowledge base
   - Data analysis
2. header "Users" | "Who will use it?" | single-select
   - Just me
   - Small team
   - Customers or the public
3. header "AI tool" | "Which AI tools will run it?" | multi-select
   - Claude Code (terminal / desktop)
   - Claude app (chat, projects)
   - Claude API / custom app
   - Other AI tools (ChatGPT, Gemini, local)
4. header "Size" | "How big is the content?" | single-select
   - Small (under 20 files)
   - Medium (20-200 files)
   - Large (200+ files or big datasets)

## Round 2: behaviour and limits
5. header "Memory" | "What must persist between sessions?" | multi-select
   - Task progress / next steps
   - Decisions and reasons
   - My preferences and style
   - Mistakes to avoid
6. header "Repeat" | "Do you repeat procedures often?" | single-select
   - Yes, several (make skills + scripts)
   - One or two (make a skill)
   - No (skip skills/)
7. header "Constraints" | "Any hard constraints?" | multi-select
   - Private / sensitive data
   - Must keep token cost very low
   - Specific output formats (docx, xlsx, JSON)
   - Non-English language
8. header "Variant" | "Which layout depth do you want?" | single-select
   - Minimal (entry file + index + memory)
   - Standard (recommended)
   - Full (adds cache, embeddings, logs)

## After the answers
Map answers to a variant in `variants.md`. "Other" answers: read them literally and adapt.
Sensitive data -> add a "never read / never send" rule to AGENTS.md.

## Round 3: plan style (ask if the project spans more than one chat)
9. header "Plan" | "How should the work be structured?" | single-select
   - Milestones (project phases with deliverables)
   - Curriculum (learning modules with exercises)
   - Single task, no plan needed
10. header "Pace" | "How big should each milestone be?" | single-select
   - Small (one short chat)
   - Medium (one focused chat, recommended)
   - Large (split further if it won't fit one chat)
Rule: each milestone gets its own chat. See `milestones.md`.
