# Your Web Novel Agent: Beginner's Guide

You have two AI helpers in Claude Code:

- **web-novelist** writes. It brainstorms, builds your story bible, outlines arcs, and drafts chapters.
- **novel-editor** critiques. It reads a chapter like a picky reader and tells you what to fix. It never changes your files.

You don't need to write any code. You just type requests in plain English.

## How it remembers your story

AI doesn't remember past conversations on its own. So each novel gets a folder of notes that the agent reads before writing, and updates after:

```
novels/
  my-novel-name/
    story-bible.md   ← characters, world, power system, rules
    outline.md       ← the plan for arcs and chapters
    chapter-log.md   ← what happened in each chapter + current stats
    chapters/
      chapter-001.md
      chapter-002.md
```

The more detail you put in the story bible, the better and more consistent the writing gets. You can open and edit any of these files yourself at any time.

## Things you can type

**Start a new novel**
> Use the web-novelist to start a new novel. Idea: a programmer dies and wakes up in a cultivation world as a servant with a system that only gives him debugging skills.

**Build the world**
> Have the web-novelist design the power system for my novel. I want 9 stages, and every breakthrough should cost something.

**Plan**
> Ask the web-novelist to outline Arc 1 as 15 chapters.

**Write**
> Use the web-novelist to write chapter 1.
>
> Write the next chapter.

**Get feedback**
> Run the novel-editor on chapter 3.
>
> Have the web-novelist fix the editor's must-fix notes.

**Rewrite**
> Rewrite chapter 2 so the fight is shorter and the ending hook is stronger.

## Tips for great results

1. **Spend time on the story bible first.** A strong power system and clear protagonist goals make every chapter better.
2. **Write one chapter at a time and read it.** Tell the agent what you liked and didn't. Your taste is what makes the story yours.
3. **Use the editor often**, especially on chapters 1–10. Those decide whether readers stay.
4. **Fix things in the story bible, not just the chapter.** If you change a rule, update the bible so future chapters follow it.

## Saving your work

Your files live in this cloud session, which is temporary. To keep them, ask Claude:

> Commit and push my novel.

That saves everything to your GitHub repository on the `claude/web-novel-agent` branch.

## Changing how the agent writes

The agent's instructions are plain text in `.claude/agents/web-novelist.md`. You can edit that file, or ask Claude to change it, for example:

> Update the web-novelist so chapters are 4,000 words and written in first person.
