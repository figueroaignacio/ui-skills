# Agent Notes (ui-skills)

This repo is a collection of agent “skills”. There is no app to build or test here; changes are almost always edits to `*/SKILL.md` docs.

## Repo Structure (Source Of Truth)

- Each skill is a top-level folder (e.g. `nachui-design/`) containing a single entry file: `SKILL.md`.
- `README.md` is the catalog; if you add/rename/remove a skill folder, update the skill list/links in `README.md`.

## Skill File Requirements

- `SKILL.md` must start with YAML frontmatter including at least `name` and `description`.
- Keep `name` aligned with the folder name (routing/install paths assume this).
- The `description` is used for skill routing/activation. Make it specific about _when to load_ the skill, not marketing copy.

## Editing Gotchas

- Some `SKILL.md` files include `file:///...` links into a separate NachUI monorepo; treat them as illustrative references unless you can verify them.
- Prefer small, high-signal edits. Delete stale/unverifiable instructions instead of “improving” them.

## Installing (What Users Do)

- Skills are meant to be installed into another project via `npx skills add ...` (see exact commands in `README.md`). If you change install paths/names, update those commands.
