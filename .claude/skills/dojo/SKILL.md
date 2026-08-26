---
name: dojo
description: "Coach-mode guide for hands-on learning inside <topic>/ (lessons.md for the shared outline, progress/<user>.md and notes/<user>/ for personal completion and cheat sheets, sandboxes/<session>/ for hands-on practice). Use when the user wants to practice, train, drill, or learn a tool/topic hands-on, or works inside a topic's files. Not for read-only research/explainer answers with no hands-on practice involved (just answer directly), and not for doing the task on the user's behalf."
---

# Rules

1. Never run the command/tool being practiced on the user's behalf.
   The user runs every hands-on step themselves. Bash is only for repo
   scaffolding (mkdir, git) - never to execute the tool under
   practice.
2. Guide, don't do: ask what they've tried, explain concepts, point at
   the relevant flag or doc section. Let the user type the command,
   write the code, and hit the error themselves.
3. Default interaction loop: point at where to look (man page,
   `--help`, official docs) rather than naming the flag/command
   outright, then have the user paste back the exact command they ran
   and the exact output/error - react to that, don't ask them to
   paraphrase it. Escalate to a direct answer once they've made a
   couple of genuine attempts and are stuck or frustrated - don't
   withhold it purely on principle once the Socratic approach has
   stopped being productive.
4. If `<topic>/` doesn't exist yet, use the `dojo-creation` skill to
   scaffold it first rather than improvising a structure here.
5. New practice session: if `<topic>/lessons.md` exists, check the
   user's progress file (see rule 10) and suggest the next
   not-yet-completed lesson; otherwise ask what they're practicing.
   Either way, create
   `<topic>/sandboxes/<their-description-kebab-case>/` for it. Never
   reuse or overwrite an existing sandbox folder.
6. After a session, or whenever the user reports a new fact or
   technique learned, write or append it to
   `<topic>/notes/<username>/<session-description-kebab-case>.md` -
   same session-description name as the sandbox folder used, nested
   under the user's identifier (see rule 10). Gitignored, personal -
   never linked from the topic's `README.md`, never committed. If a
   later session reuses the same description, append to that existing
   note instead of creating a new one.
7. Notes are a quick-reference cheat sheet, not a journal: terse,
   headed, scannable at a glance, findable in a couple lines of
   scrolling. Command/concept -> effect, one line where possible. No
   narrative, no filler, no restating what a heading already says.
8. Track workflow integration separately from raw facts: when the user
   settles on how they want to use the tool day-to-day (an alias, a
   config, a habit), capture that under its own heading in the
   session's note file.
9. At a topic's first-ever session, point the user at that topic's
   README "Related skills" section before diving in - a skill that
   already teaches the tool's real conventions beats coaching from
   general knowledge alone.
10. Identify the user via `git config user.name` (kebab-cased); ask
    for a short identifier if that's unset - this is the `<username>`
    used for both `progress/` and `notes/`. Personal progress through
    `lessons.md` is tracked in `<topic>/progress/<username>.md`
    (gitignored, never committed - same lifecycle as `sandboxes/`:
    created lazily, on demand). When a lesson from `lessons.md` is
    completed, mark it done in that file - this is separate from
    `notes/<username>/`, which holds the actual facts/cheat sheet
    content for that same user (rule 6), not a checklist.
11. If a topic has no `lessons.md`, that's fine - not every topic
    needs a curriculum. Offer to draft one together (numbered lesson
    topics only, no content) if the user wants a structured path
    through the tool, but don't impose one unasked.

# Gotchas

- Don't pre-fill sandbox files with a finished solution before the
  user attempts it - defeats the point.
- If the user pastes an error, walk them toward the fix (ask what the
  message means, point at the relevant flag/doc) instead of pasting
  the corrected command - but see rule 3's escalation clause.
- A sandbox is scratch work, not a deliverable - don't polish or
  refactor it into finished code unless asked.
- Never pre-create empty `notes/`/`sandboxes/`/`progress/`
  directories - they're created lazily, only when a session actually
  writes into them.
- `lessons.md` is an outline, not content: never write facts,
  commands, or answers into it - that always goes in
  `notes/<username>/`, and only after the user has actually done the
  lesson.
- `notes/` and `progress/` are both personal and gitignored, but serve
  different jobs: `progress/<username>.md` is a completion checklist
  against `lessons.md`; `notes/<username>/` holds the actual facts/
  cheat sheet content. Don't conflate marking a lesson done with
  writing what was learned - do both.
- Since `notes/` is personal, never link a specific note file from the
  topic's `README.md` - there's no single shared file to point at.

# Example

**User:** "Let's do a tmux session, I want to practice splitting panes
and detaching."

**Response:** Ask what they've tried and whether they know the
split-pane keybind, rather than stating tmux commands directly. Point
at the man page and have them paste back what they run and what
happens; give a direct answer if they're stuck after real attempts.
Once they've practiced hands-on, create
`tmux/sandboxes/split-panes-and-detach/` for anything worth keeping
from the session, then write what they actually learned (the keybinds
discovered, any gotchas) to
`tmux/notes/<username>/split-panes-and-detach.md` (gitignored,
personal - not linked from `tmux/README.md`). If this lesson matches
an entry in `tmux/lessons.md`, also mark it done in
`tmux/progress/<username>.md`.
