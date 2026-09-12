# When a playbook note becomes a Skill, and how this vault writes one

## The promotion rule

Not every folder here needs a Skill wrapper — most declarative field
notes (`finance/`, `marketing/`, etc.) are fine as manually-consulted
reference, read when a task obviously calls for that domain. Promotion
earns its keep specifically when both are true:

1. **The law is meant to fire before the agent would think to check it**
   — the exact failure `github/preflight-checklist.md` exists to prevent
   ("skipping straight to the action because this one's simple") is
   precisely what a Skill's automatic trigger closes, and a note sitting
   in a folder nobody remembered to open doesn't.
2. **The trigger condition is nameable in one or two sentences** — if the
   "when to use this" can't compress into a description that fires
   reliably without also firing on unrelated work, it isn't ready to be a
   Skill's cover yet, no matter how good the underlying note already is.

`github/` and `language/markdown/` both clear this bar today: every git/
GitHub action and every `.md` edit are exactly the kind of before-not-
after law a forgettable folder check keeps failing at.

## Authoring convention, when building one from this vault's own content

- **Frontmatter stays name + description only.** The description states
  the trigger condition in the third person — the way `find-skills`' own
  does ("Helps users discover... when they ask...") — not a summary of
  what the skill contains.
- **Body stays lean and decision-first.** The condensed rule, not the
  full reasoning — the reasoning already lives in the matching playbook
  file, and restating it in the Skill body would violate the same
  no-duplication discipline `preflight-checklist.md` already states for
  notes linking to notes.
- **Point back at the playbook file instead of copying it into a bundled
  `references/` folder.** Hermes bundles its references inside each skill
  because its skills are meant to be portable, installed independently,
  outside any one person's own knowledge base. These skills aren't —
  `playbooks/` is already the canonical source, sitting on the same
  machine, so the Skill's job is to be the trigger, not a second copy of
  the law.
- **Carry a safety tier where the underlying action has one.** `github/`
  already has real stakes — reuse this operator's own existing standing
  rules for what's forbidden without confirmation (a force-push to main,
  a hard reset on a shared branch, skipping hooks, touching a secret)
  rather than inventing a parallel list. Don't duplicate what's already
  the authority on it.

## Related

- [mechanism.md](mechanism.md) — the frontmatter/body split this convention builds
  on top of.
- [preflight-checklist.md](../../github/preflight-checklist.md) — the first real candidate for
  conversion under the promotion rule above.
