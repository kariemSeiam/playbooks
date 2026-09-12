# Preflight checklist — run this before any git/GitHub action with real effect

The other three files in this playbook are the reasoning; this file is
the thing to actually execute, every time, before `add`/`commit`/`push`/
`branch`/`tag`/`remote`, or any GitHub action that creates or modifies
something. Skipping straight to the action because "this one's simple" is
exactly how the recurring real-world failure mode in
[concurrency-and-branching.md](concurrency-and-branching.md) happens — it's rarely one obviously-bad
step, it's two individually-reasonable steps combining into permanent
mislabeled history.

## 0. Is there a project-specific override?

Check for a project's own stated git convention (a `CONTRIBUTING.md`, a
note in its `CLAUDE.md`/`AGENTS.md`/README, or an explicit standing
instruction already given for this specific repo) before assuming this
playbook's defaults apply. A project's own convention always wins over a
general default — this checklist is the fallback for when nothing more
specific has been said.

## 1. `git status` before anything else

Always, even for "just a quick commit." Read the actual output, don't
assume it matches expectation. Specifically look for:

- Files modified/untracked that you didn't cause — a sign that some other
  work (another process, an earlier half-finished task) is sitting in this
  tree. Don't touch it, don't assume it's safe to sweep in.
- Whether the number of changed files roughly matches what was actually
  done — if two files were intentionally changed and `status` shows
  fifteen, stop and find out why before staging anything.

## 2. Is more than one task/process touching this repo right now?

If yes, or about to be (e.g. about to dispatch parallel work) — set up a
`git worktree` per task first ([concurrency-and-branching.md](concurrency-and-branching.md)). Don't
proceed with a shared working tree "just this once" — that's the exact
reasoning that produces the failure mode this playbook exists to prevent.

## 3. Stage exact files, never broad

`git add <exact path> <exact path> ...` — always. Never `git add -A`,
never `git add .`, even when `status` looks clean. The discipline has to
be unconditional to be reliable; making it conditional on "looks fine
today" is how it eventually fails on the one day it doesn't look fine and
nobody double-checked.

After staging: run `git diff --cached --stat` and actually read it. Does
it show exactly the files intended, and roughly the expected size of
change? If anything unexpected is staged, `git restore --staged <file>`
it out before proceeding.

## 4. Scan for secrets before committing

Check the staged diff itself — not just the filenames — for anything
that looks like a credential, API key, token, or `.env`-style content,
even in a file whose name looks innocuous. If found, unstage it and stop;
never commit it "to remove later" — history remembers even a fast
follow-up removal. Confirm `.env*`/`*.key`/`*.pem`-style files are
actually gitignored rather than assuming they are.

## 5. Write the commit message per [commits.md](commits.md)

Header (type + imperative subject), body (why, not what), footer only if
there's a real trailer to add. If the header needs an "and" to describe
it, the commit likely isn't atomic yet — reconsider before committing,
not after.

## 6. After committing: verify, don't assume

`git status` again — confirm the working tree now shows only what should
still be uncommitted (any other process's untouched work should look
exactly as it did before). `git show --stat <new-commit>` — confirm the
file list matches intent exactly, not approximately.

## 7. Before pushing

Pushing to a remote is generally an action that needs the owner's
explicit go-ahead, even when the broader task was clearly authorized —
unless the request that started this work already explicitly named the
push itself. After pushing, report exactly what landed (which commits)
and, just as importantly, what did NOT — uncommitted working-tree state
never travels with a push, and letting that go unsaid risks the owner
assuming everything is synced when it isn't.

## 8. Before any GitHub action that creates something (repo/issue/PR/release)

Check [platform.md](platform.md) for whether the construct actually earns its place at
the project's current size and maturity — most GitHub ceremony (branch
protection, PRs, CI) is correctly unused below a certain size and a real
liability if adopted without the conditions that justify it. Before
creating a repository specifically: confirm intended visibility (private
by default absent a stated reason otherwise) and check whether one
already exists at the target name before creating a duplicate.
