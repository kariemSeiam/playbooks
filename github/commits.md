# Commit anatomy, taxonomy, and quality bar

A commit is three parts: **header** (always), **body** (unless the change
is genuinely trivial — a typo fix, a one-line dependency bump), **footer**
(only when there is something machine-readable to say). This is the
Conventional Commits shape — an actual industry standard, not a house
invention — and every point below is true of it regardless of what
project or language it's applied to.

## Header — `<type>(<scope>): <subject>`

One line. Imperative mood — "add", not "added" or "adds" (the convention
comes from thinking of a commit as an instruction to the codebase: "apply
this commit" reads naturally as "add support for X", not "adds support for
X"). No trailing period. Keep it to roughly 72 characters or fewer —
`git log --oneline`, GitHub's PR/commit list views, and terminal-width
truncation all cut off past that point, so anything past it is invisible
in the views where a header is read most often.

`(scope)` is optional — a short noun for the area that changed (`(auth)`,
`(parser)`, `(ci)`). It earns its place once a project has enough
independent moving parts that "which area" isn't obvious from the subject
alone; a small or early-stage project can skip it and let the subject
carry that information.

### Type taxonomy — pick by what actually changed, not by vibe

| Type | Use when | NOT when |
|---|---|---|
| `feat` | a capability exists that didn't before | tweaking an existing one without adding new capability — that's a plain description or `fix`, not `feat` by default |
| `fix` | correcting behavior that was wrong | a change of mind about a design choice that was never actually broken — that's `feat` or `refactor` |
| `docs` | documentation/comment-only changes | any change that also touches executable code — split it into two commits |
| `chore` | tooling, config, ignore rules, dependency bumps — no product behavior change | anything a user or reader of the product would notice |
| `refactor` | internal restructuring, behavior unchanged | if behavior changes even slightly, say so honestly (`feat`/`fix`), don't call it `refactor` to make it sound safer than it is |
| `test` | test-only changes | — |
| `perf` | a *measured* performance improvement | a change you merely hope is faster — measure first, or call it `refactor`/`feat` until you have a number |
| `style` | formatting/whitespace, zero logic change | — |
| `build` / `ci` | build system or CI pipeline changes | — |
| `revert` | undoing a prior commit | — |

A project may add its own type beyond this list (e.g. `spec` for a design
document, `content` for adding real product content alongside code) — that's
legitimate the moment the standard list doesn't honestly describe what's
happening and the new type will recur. It's illegitimate the moment it's
invented once per commit as a way to avoid picking honestly from the list
above; a proliferating vocabulary of one-off types defeats the purpose of
having a taxonomy at all.

## Body — the *why*, never the *what*

Blank line after the header, then prose, wrapped to roughly 72 columns (a
convention old enough to predate modern terminals, still load-bearing
because `git log`'s default indent and most terminal-width defaults still
assume it). The diff already shows *what* changed — a body that just
narrates the diff in English is dead weight that will be skipped by every
future reader, including the one who wrote it. What only the author knows
and the diff cannot show:

- **Why this approach and not an alternative** — what was actually
  considered and rejected, and on what grounds.
- **What constraint forced this shape** — a measured limitation, a
  correctness requirement, a compatibility need.
- **What was verified, and how** — if the change fixes something, what
  concretely confirms it's fixed (a specific number, a specific
  reproduction, a specific check that now passes).

A body that reads "changed the timeout value" is worthless — the diff
already says that. A body that reads "the timeout was set to 30s based on
a guess; load testing showed p99 latency at 45s under realistic traffic,
so raised it to 60s with headroom, and added a metric to catch the next
time this assumption goes stale" is doing real work: it tells a future
reader the reasoning, the evidence, and what changed in the system's
observability as a result — none of which the diff itself contains.

## Footer — machine-readable trailers, only when there's a real one

Blank line after the body, then `Key: value` trailers:
- `Fixes #123` / `Closes #123` — auto-closes an issue tracker item on
  merge to the default branch (GitHub, GitLab, and most trackers honor
  this convention).
- `Refs #123` — links without closing, for a related-but-not-resolving
  reference.
- `BREAKING CHANGE: <description>` — the change alters a public
  interface/contract in an incompatible way. This is the trailer that
  drives major-version bumps under semantic versioning, and the one most
  worth never skipping once a project has any external consumers of its
  interfaces (including "future you," six months from now, having
  forgotten this contract existed).
- `Co-authored-by: Name <email>` — reserved for when a commit's content is
  genuinely the product of more than one distinct contributor whose
  authorship should be credited — not a boilerplate addition to every
  commit regardless of whether that's true.

Only use a footer trailer when the thing it points to actually exists
(an issue tracker, an external consumer, a second real author). A project
with none of those yet correctly has no footers — don't invent an issue
number or a co-author to make a commit look more complete than it is.

## Atomicity — one logical change per commit

A commit should do one thing describable in its header without an "and".
This isn't a style preference — it's what makes `git bisect` find a
regression in `log(n)` steps instead of forcing a manual read of a giant
diff, what makes `git revert` safely undo exactly one change instead of an
entangled bundle, and what makes code review (human or AI) actually
tractable per-commit instead of per-PR-as-one-blob.

The most common way atomicity silently breaks in practice, worth naming
because it's easy to miss in the moment: **staging more than the current
task actually touched.** A broad `git add -A`/`git add .` run in a working
tree that also contains someone else's (or some other process's) unrelated
uncommitted work will happily stage all of it together, producing a commit
whose message describes one thing while the diff contains several. The
content isn't wrong, but the history is now permanently mislabeled — a
commit's message is exactly as trustworthy as the discipline that staged
it, and that discipline is a single habit: stage exact paths, verify the
staged diff before committing, never assume a clean-looking `status` means
a broad add is safe.

## What NOT to do

- Don't write a header that could describe a dozen different diffs
  ("update files", "wip", "fix stuff"). If it can't name what changed
  specifically, the commit likely isn't atomic yet — split it.
- Don't narrate the diff line-by-line in the body. `git show` already does
  that; the body only earns its place by saying something the diff can't.
- Don't `git commit --amend` anything already pushed, and don't use it at
  all unless explicitly asked to — a failed pre-commit hook means the
  commit never happened, so `--amend` immediately after a hook failure
  silently rewrites the *previous*, unrelated commit instead.
- Don't skip the body because the diff "felt small." A ten-line change can
  carry a body worth reading if the reasoning behind it is non-obvious;
  size of diff and size of "why" are unrelated quantities.
