# Claude Dojos

A monorepo of hands-on practice dojos for various tools/topics. Read
`README.md` at the start of every session for what this repo is and
how it's organized.

## Skills

- `dojo` - coaches a hands-on practice session inside `<topic>/`.
- `dojo-creation` - scaffolds a new `<topic>/` dojo.

## Conventions

- `<topic>/sandboxes/` is gitignored scratch work, created on demand
  by the `dojo` skill - never pre-create it, never commit it.
- `<topic>/notes/<username>/` is gitignored, personal cheat-sheet
  output of a session - never commit it.
- A new topic always goes through `dojo-creation`, never a manual
  `mkdir` - it keeps the root README's topic list in sync.
