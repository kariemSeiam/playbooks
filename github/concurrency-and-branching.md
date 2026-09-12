# Branching models and concurrent-work isolation

## Choosing a branching model — a decision, not a default

There is no single correct branching model; there is a correct model for
a given team size, release cadence, and risk tolerance. Picking one
without checking which conditions actually hold is the most common
branching mistake — not picking "the wrong one" in the abstract, but
importing a model built for a different situation.

- **Trunk-based (direct or near-direct commits to `main`, no long-lived
  branches)** — correct when the team is small (often one contributor,
  human or AI-paired), releases continuously or doesn't version releases
  at all, and there's no need to stabilize a release line while new work
  continues in parallel. Minimizes merge friction and keeps `main` always
  close to what's actually running. Wrong the moment more than a handful
  of people need to avoid interfering with each other's in-flight work,
  or a released version needs patches while development moves ahead of it.
- **GitHub Flow (short-lived feature branches, PR, merge to `main`,
  deploy from `main`)** — correct for small-to-medium teams shipping
  continuously, where a PR's value is genuine review from a second person,
  not process for its own sake. The branch's only job is to exist long
  enough for review; it should not accumulate weeks of drift from `main`.
- **Git Flow (`develop`, release branches, hotfix branches, tagged
  releases)** — correct when a project ships discrete, versioned releases
  that need to be stabilized independently of ongoing development, and/or
  needs to patch an old release without pulling in newer unreleased work.
  Heavyweight for anything that doesn't actually have this need — the
  ceremony (multiple long-lived branches, merge-back discipline) is a cost
  paid to buy release stability, and is waste when nothing is being
  stabilized.
- **Trunk-based with release branches cut only at ship time** — a middle
  path: develop on `main`, cut a release branch (`release/1.2`) only when
  actually releasing, patch that branch for hotfixes, merge patches back.
  Correct for projects that release periodically but don't need Git Flow's
  full ceremony for the much larger fraction of time spent between
  releases.

**The test to apply, concretely**: how many independent contributors need
to avoid stepping on each other, and does a released version need to
survive independently of ongoing development? Low/low → trunk-based.
Higher contributor count, still no independent release stability need →
GitHub Flow. Real need to stabilize/patch a shipped version independently
→ Git Flow or trunk-with-release-branches. Re-evaluate when either answer
changes — the model that was right at project start is not guaranteed to
still be right once a team or release cadence changes.

## The concurrency problem that classic branching advice doesn't cover

Git's branching literature was written assuming the unit of concurrent
work is a human, working at human speed, in their own checkout. It says
almost nothing about a newer and increasingly common situation: **multiple
autonomous processes — parallel AI agents, automated tooling, background
jobs — operating on the same repository at overlapping times**, often
faster than a human would notice the collision happening at all.

This matters because the usual safety nets for human concurrency (a PR
sitting open long enough for a human to notice a conflict, a Slack message
saying "I'm working on X") don't exist for concurrent automated work
unless someone builds them in deliberately. The actual failure mode: two
agents each reasonably assume their file sets are disjoint (by spec, by
task boundary), work in the *same shared working tree* at the same time,
and one of them stages more broadly than its own task — sweeping the
other's already-made-but-uncommitted changes into its own commit. Nothing
is lost or corrupted (the content is all real), but the resulting commit
message now describes only a fraction of what the commit actually
contains, and that mislabeling becomes permanent, uncorrectable history
the moment it's part of a shared branch that anyone else might build on
top of (rewriting shared history to fix it is usually a worse trade than
living with a mislabeled commit).

This is not a hypothetical concern to file away for later — it is the
predictable outcome of running more than one agent against one working
tree without isolation, and it has been observed in practice. Treat it as
a known, recurring failure mode, not an edge case.

## The standing fix: isolate before you parallelize

**The moment more than one task or process might touch a repo in
overlapping time, give each its own `git worktree` before starting** —
don't share one working tree and rely on careful staging to keep them from
colliding. A worktree is a second checkout of the same repository on its
own branch, in its own directory (`git worktree add ../<name> <branch>`);
commits made inside one worktree are invisible to file operations in
another until deliberately merged. This is structural isolation — it
doesn't depend on any individual step remembering to be careful, which is
exactly the property that "just stage carefully" doesn't have.

Concretely: before dispatching more than one piece of work against the
same repo with any chance of overlapping execution, create one worktree
per task, let each stage/commit entirely inside its own tree, then
integrate afterward from a single point. This is more setup than working
directly in one shared tree — that tradeoff is worth it precisely because
the failure mode it prevents produces permanent, uncorrectable history
rather than a recoverable mistake caught in review.

**When a worktree is not warranted**: a single task, single active
process, no other work expected to land in the same window. The trigger
is "more than one thing touching this repo around the same time" — not
every commit, and not a standing requirement for solo sequential work.

## The fallback, when isolation wasn't set up in time

If concurrent work is discovered mid-task in a shared tree that wasn't
pre-isolated: never `git add -A` or `git add .`. Stage the exact files the
current task actually touched, verify with `git diff --cached --stat`
that the staged set matches intent exactly before committing, and confirm
with `git status` afterward that nothing else was swept in. This is a
discipline, not a structural guarantee — it has to be actively applied
every single time to work, which is precisely why it's the fallback and
not the primary defense.

## Interleaved-hunk recovery

If a single file ends up with one task's intended change interleaved,
in the same region, with another process's unrelated uncommitted edit
(discovered after the fact, no interactive terminal available for `git
add -p`): reconstruct the file's intended isolated content (HEAD plus
only the current task's change), write that to disk, stage it, verify
with `git diff --cached` that only the intended hunk is staged, then
restore the working file to its full real state (the task's change plus
the other process's untouched work) so nothing is lost. Confirm with
`git diff` (unstaged) that only the other process's untouched hunk remains
before committing. Mechanical and reliable — slower than staging cleanly
in the first place, which is the actual argument for isolating before
parallelizing rather than depending on recovering afterward.
