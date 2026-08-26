# Claude Dojos

A monorepo of blank, hands-on practice grounds ("dojos") for any
tool or topic. Claude Code coaches you through each one Socratic-style:
it points at where to look and reacts to what you actually ran, rather
than doing the work for you. See the `dojo` skill for exactly how a
session runs.

## Using a dojo

1. Clone this repo.
2. `cd <topic>/`
3. Run `claude` and tell it what you want to practice.

Session scratch work lives in `<topic>/sandboxes/<session>/`, created
on demand and gitignored - it's practice, not a deliverable, and never
shows up in a diff. What's worth keeping (facts learned, gotchas,
workflow habits) gets written to `<topic>/notes/<username>/` instead -
also gitignored and personal, so your cheat sheet never collides with
anyone else's clone.

A topic may also have `<topic>/lessons.md`, a committed, ordered
outline of lesson topics (no content/answers - just what to cover).
Your own progress through it is personal, not shared: it's tracked in
`<topic>/progress/<username>.md`, gitignored like `sandboxes/` and
`notes/`.

## Creating a new dojo

Ask Claude to create a dojo for your topic (e.g. "create a dojo for
Terraform") - this uses the `dojo-creation` skill, which scaffolds
`<topic>/README.md` and links it from this file. Don't `mkdir` a topic
by hand; go through the skill so the structure and the topic list stay
consistent.

## Contributing

PR new topics (via `dojo-creation`) or improvements to an existing
topic's `README.md`/`lessons.md` - the only files meant to be shared.
`sandboxes/`, `progress/`, and `notes/` are always gitignored and
personal, so your practice sessions, completion tracking, and cheat
sheets never end up in a PR.

## Finding skills for a topic

Before starting a new topic, check whether a Claude Code skill already
covers it. A skill teaches Claude the tool's real conventions and
gotchas instead of relying on general training data.

- Check your Claude Code setup's installed skills (listed to Claude at
  the start of each session).
- Check any plugin marketplace(s) your setup has configured.
- If nothing exists and the topic warrants one, write it: use a
  skill-authoring skill if your setup has one (e.g. `skill-creation`),
  otherwise write the `SKILL.md` directly.

This check is manual, not automated. Each topic's own README links
back to this section instead of repeating it.

## Structure

```
.
├── README.md                — this file
├── CLAUDE.md                — session rules for Claude Code in this repo
├── .claude/skills/
│   ├── dojo/                — coaches a hands-on practice session
│   └── dojo-creation/       — scaffolds a new <topic>/ dojo
└── <topic>/
    ├── README.md            — status, links lessons.md, "Finding skills for a topic" pointer
    ├── lessons.md            — optional, committed: ordered lesson outline (no content/answers)
    ├── notes/<username>/     — gitignored, created on demand: personal cheat sheet, one file per session topic
    ├── progress/             — gitignored, created on demand: per-user lesson completion
    └── sandboxes/            — gitignored, created on demand: one folder per practice session
```

## Topics

- [bash-cli](bash-cli/README.md)
- [claude-code](claude-code/README.md)
- [git](git/README.md)
- [tmux](tmux/README.md)
