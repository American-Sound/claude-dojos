---
name: dojo-creation
description: "Scaffold a new dojo topic at the root of this repo: <topic>/README.md plus a link from the root README's topic list. Use when the user wants to create a dojo, start a new dojo for some tech/topic, add a topic to this repo, or scaffold a new practice ground. Not for running a practice session inside an existing topic (see the dojo skill) or for editing an existing topic's content."
---

# Rules

1. Kebab-case the topic name for the directory (`Terraform` ->
   `terraform`, `Azure Entra` -> `azure-entra`).
2. If `<topic>/` already exists, don't overwrite it - point the user
   at the existing `<topic>/README.md` instead.
3. Create `<topic>/README.md`, plus `<topic>/lessons.md` only if the
   user wants one (see rule 5). Never pre-create `notes/`,
   `sandboxes/`, or `progress/` - those are gitignored, personal, and
   created lazily by the `dojo` skill the first time a session
   actually needs them; an empty directory here would never even get
   committed (git doesn't track empty dirs).
4. Append a link to the new topic under the root README's "## Topics"
   list, alphabetically.
5. Ask the user for a one-line status/description of the topic if they
   didn't already give one, to seed the README's status line. Also ask
   whether they want a lesson outline drafted now - if yes, write
   `<topic>/lessons.md` together as a numbered, ordered list of lesson
   topics (one line each, no content/answers - see template). If no,
   skip the file entirely; the `dojo` skill can draft one later.

# Template for `<topic>/README.md`

```markdown
# <Topic Title>

Status: <one-line status, e.g. "not started">.

## Lessons

(add this section, linking `lessons.md`, only if that file exists)

[lessons.md](lessons.md) - outline. Personal progress is tracked in
gitignored `progress/`, per user - never committed.

## Notes

Personal cheat sheets are tracked in gitignored `notes/<username>/`,
per user - never committed.

## Related skills

Before your first session, check the root README's "Finding skills
for a topic" section for how to look for a skill that already covers
<Topic Title>.
```

# Template for `<topic>/lessons.md` (only if the user wants one)

```markdown
# <Topic Title> lessons

Ordered outline - a session works through the next lesson you haven't
completed. See "Related skills" in the README before your first one.
Personal progress lives in gitignored `progress/`, not here.

1. <lesson 1 topic>
2. <lesson 2 topic>
```

# Gotchas

- Don't invent a status/description if the user hasn't given one and
  didn't want to answer - "not started" is a safe default, but ask
  first rather than assuming what they're using it for.
- `lessons.md` is an outline (topic names only) - never write the
  actual facts/commands/answers into it. Learned content only ever
  goes in personal, gitignored `notes/<username>/`, and only after a
  real session (see `dojo` skill).
- This skill only creates the topic; it does not start a session -
  hand off to the `dojo` skill once the topic exists.

# Example

**User:** "Create a dojo for Terraform."

**Response:** Ask for a one-line status (or default to "not started")
and whether they want a lesson outline drafted now. Say they do, with
lessons on providers/state, resources, and modules. Create
`terraform/README.md`:

```markdown
# Terraform

Status: not started.

## Lessons

[lessons.md](lessons.md) - outline. Personal progress is tracked in
gitignored `progress/`, per user - never committed.

## Notes

Personal cheat sheets are tracked in gitignored `notes/<username>/`,
per user - never committed.

## Related skills

Before your first session, check the root README's "Finding skills
for a topic" section for how to look for a skill that already covers
Terraform.
```

And `terraform/lessons.md`:

```markdown
# Terraform lessons

Ordered outline - a session works through the next lesson you haven't
completed. See "Related skills" in the README before your first one.
Personal progress lives in gitignored `progress/`, not here.

1. Providers and state.
2. Resources.
3. Modules.
```

Add `- [terraform](terraform/README.md)` to the root README's Topics
list (alphabetically), then confirm it's ready and hand off: "Run
`cd terraform/` and start Claude Code there whenever you want to begin
- the `dojo` skill will pick it up."
