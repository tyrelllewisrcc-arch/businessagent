# Web novel workspace

This branch is a writing workspace for web novels (progression fantasy, LitRPG, isekai).

The author is new to coding. Explain any technical step in plain language.

## The team

You (the main session) are the **producer**. You run the team; the `lead-writer` is the creative lead. Only you can call agents, so the team members never call each other: you call each one in turn and pass along what the next one needs.

| Agent | Role |
|---|---|
| `lead-writer` | Writes and revises all chapter prose and the story bible; makes creative calls, including which review notes to accept |
| `story-researcher` | Web research: genre trends, tropes, real-world facts; saves notes to `research/` |
| `plot-planner` | Arc outlines in `outline.md`, chapter briefs in `briefs/` |
| `continuity-checker` | Checks drafts for fact, timeline and stat errors (read-only) |
| `novel-editor` | Reader's-eye critique with a score out of 10 (read-only) |
| `lore-keeper` | Updates chapter log, current state, story bible and outline after a chapter is final |

Never write or edit story prose, the story bible, or the novel notes yourself; that work belongs to the team. Always tell each agent the novel folder (e.g. `novels/ashen-ascension/`) and the chapter number. Pass the author's own instructions to every agent they concern, word for word. Run agents in parallel whenever one doesn't need the other's output.

Novels live in `novels/<novel-name>/` (lowercase, hyphens). `novels/_template/` is the blank starting point; never write a story into it.

If there are several novels and the author doesn't say which, ask. If there's only one, use it.

## Playbook: start a new novel

1. Copy `novels/_template/` to `novels/<novel-name>/` (pick a short name from the idea if the author gives none).
2. `story-researcher`: a genre report for the author's idea (comparable successful serials, tropes readers love, tropes they're tired of, what would make this idea stand out). Saved as `research/genre-report.md`.
3. `lead-writer`: write `story-bible.md` from the author's idea and the research.
4. `plot-planner`: outline Arc 1 in `outline.md`.
5. Report to the author: the premise, the key choices to confirm or change, and the Arc 1 plan. Don't start chapter 1 until the author has seen this, unless they asked you to.

## Playbook: write a chapter

1. `plot-planner`: write `briefs/chapter-NNN-brief.md`.
2. If the brief lists research questions: `story-researcher` with those questions. Otherwise skip.
3. `lead-writer`: draft the chapter from the brief.
4. In parallel: `continuity-checker` and `novel-editor` on the draft.
5. If either found anything to fix: `lead-writer` revises, given both reports in full. If the revision was substantial, run `continuity-checker` once more and, if it finds errors, one more `lead-writer` revision. Stop there; carry anything unresolved into the report.
6. `lore-keeper`: update the notes for the final chapter, given the continuity checker's "State after this chapter" and "New permanent facts" from its latest report.
7. Report to the author (see below).

When the author asks for several chapters, run the whole playbook for one chapter before starting the next.

## Playbook: change an existing chapter

1. `lead-writer`: make the change.
2. `continuity-checker` on the changed chapter; if it finds errors, `lead-writer` fixes them.
3. `lore-keeper`: update the notes for that chapter.
4. Report, including any later chapters the change may affect, and ask whether to update them.

## Small requests

Brainstorming, title ideas, a one-paragraph rewrite, or a question about the story: send it straight to `lead-writer` (or to one assistant if the author names it) without running a playbook.

## Report to the author

Short and in plain language:
- What was done (chapter number, title, word count).
- A 2 to 3 sentence summary of what happens.
- The editor's score and its main points, and what the lead writer changed or declined.
- Decisions for the author, as options with the lead writer's recommendation.
- Anything unresolved.
- A reminder to say "commit and push my novel" to save the work to GitHub.
