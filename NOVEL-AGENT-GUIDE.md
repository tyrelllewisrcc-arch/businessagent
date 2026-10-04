# Your Web Novel Writing Team: Beginner's Guide

You have a team of six AI agents in Claude Code. You talk to Claude normally. Claude acts as the **producer**: it follows a playbook and hands each step to the right team member. The **lead writer** writes every word of the story and makes the creative calls.

```
You (the author)
  └─ Claude, the producer ── runs the playbook, reports back to you
       ├─ Lead writer ──────── writes the chapters, decides which feedback to use
       ├─ Researcher ──────── looks things up on the web
       ├─ Plot planner ────── plans each chapter scene by scene
       ├─ Continuity checker ─ checks facts, timeline and stat math
       ├─ Editor ──────────── critiques the chapter like a picky reader
       └─ Lore keeper ─────── updates your notes after every chapter
```

(Why isn't the lead writer the boss of the others? In Claude Code cloud sessions, only the main Claude session is allowed to call agents. So Claude does the scheduling and the lead writer keeps the creative control.)

You don't need to write any code. You just type requests in plain English.

## What happens when you ask for a chapter

1. The **plot planner** writes a plan for the chapter (scenes, goals, ending hook).
2. If the chapter needs real-world facts, the **researcher** looks them up.
3. The **lead writer** writes the chapter.
4. The **continuity checker** and **editor** review it at the same time.
5. The **lead writer** fixes the problems they found.
6. The **lore keeper** updates your story notes (chapter log, stats, new characters).
7. Claude reports back: what happened, the editor's score, and any decisions for you.

Because six agents are working, a chapter takes several minutes and uses more of your Claude usage than a single agent would. For small jobs (rename a character, rewrite one paragraph, brainstorm titles), Claude skips the playbook and asks the lead writer directly.

## How it remembers your story

AI doesn't remember past conversations on its own. So each novel gets a folder of notes that the team reads before working and updates after:

```
novels/
  my-novel-name/
    story-bible.md    ← characters, world, power system, rules
    outline.md        ← the plan for arcs and chapters
    chapter-log.md    ← current stats + what happened in each chapter
    briefs/           ← the plot planner's chapter plans
    research/         ← the researcher's notes
    chapters/
      chapter-001.md
      chapter-002.md
```

The more detail in the story bible, the better and more consistent the writing gets. You can open and edit any of these files yourself at any time.

## Things you can type

**Start a new novel**
> Start a new novel. Idea: a programmer dies and wakes up in a cultivation world as a servant with a system that only gives him debugging skills.

The researcher studies what readers of that genre love, the lead writer builds the story bible, and the planner outlines Arc 1. Then you get a summary of the choices to approve or change.

**Write**
> Write chapter 1.
>
> Write the next chapter. I want the tournament to start and the rival to cheat.

**Change things**
> Rewrite chapter 2 so the fight is shorter and the ending hook is stronger.
>
> Change the power system so there are 9 stages instead of 7.

**Ask one assistant directly**
> Have the researcher look up how Damascus steel was made.
>
> Have the editor review chapter 5.

## Tips for great results

1. **Spend time on the story bible first.** A strong power system and clear protagonist goals make every chapter better.
2. **Read each chapter before asking for the next.** Tell the lead writer what you liked and didn't. Your taste is what makes the story yours.
3. **Answer the questions in each report.** When the lead writer gives you options for a big decision, pick one, or it will keep going with its recommendation.

## Saving your work

Your files live in this cloud session, which is temporary. To keep them, ask Claude:

> Commit and push my novel.

That saves everything to your GitHub repository on the `claude/web-novel-agent` branch.

## Changing how the team works

Each agent's instructions are plain text files in `.claude/agents/`:

The producer's playbook (the order the team works in) is in `CLAUDE.md`.

| File | Agent |
|---|---|
| `lead-writer.md` | Lead writer |
| `story-researcher.md` | Researcher |
| `plot-planner.md` | Plot planner |
| `continuity-checker.md` | Continuity checker |
| `novel-editor.md` | Editor |
| `lore-keeper.md` | Lore keeper |

You can edit them, or ask Claude to, for example:

> Update the lead writer so chapters are 4,000 words and written in first person.
>
> Add a new assistant that writes the author's notes at the end of each chapter.
