# The onboarding prompt — writing install instructions for an intelligence

Every install format before this one assumed a deterministic executor. A
shell script, a `package.json`, a Dockerfile — you write exact steps
because the thing running them cannot think, and anything you failed to
anticipate becomes a bug report. The onboarding prompt inverts that: a
single block a reader pastes into whatever agent they already run, which
then figures out its own environment and does the setup. The executor can
think now. That changes what good instructions are, and most prompts in
the wild are still written as if it didn't.

## The dial, which is the whole craft

The only real decision is **how much judgment to delegate**, and it's a
dial, not a switch:

- **Turn it too far toward determinism** and you've written a shell
  script in English — exact paths, exact commands, exact order. It breaks
  on the first environment that differs from the one you tested, which is
  most of them, and you've given up the single capability that made this
  format worth using.
- **Turn it too far toward delegation** — "set up the playbooks for me" —
  and the agent fills every gap you left with a guess. Most guesses are
  fine. The one that isn't overwrites a config file someone spent a year
  building.

The resolution isn't a midpoint, it's a split: **delegate everything
about the environment, constrain everything about consequences.** The
agent knows its own harness, paths, and available tooling far better than
you ever will — say nothing about those and let it work. It does *not*
know which files in that environment are precious, and it cannot ask you,
only the user. So every irreversible step gets an explicit boundary.

Once you've split it that way, the rest of the prompt writes itself, and
the five things below are just where the boundaries land.

## The five boundaries

1. **Detect, don't assume.** Which harness is running — and therefore
   which config paths are real — is knowable to the agent and unknowable
   to you ([mechanism.md](skills/mechanism.md) has the per-harness paths). A prompt that
   hardcodes one harness's path doesn't fail loudly for everyone else; it
   quietly sets up the wrong thing.
2. **Land somewhere durable and predictable.** A clone into a temp
   directory evaporates; one into the current working directory pollutes
   whatever project the user happened to be standing in. Name a default,
   let the agent confirm it.
3. **Merge, never clobber.** The one that does real damage. A global
   agent-instructions file is the user's own accumulated work. An agent
   told "add this to their config," with no further constraint, will
   sometimes write the file whole. Say append-or-update-in-place in as
   many words — this is the single highest-value sentence in any
   onboarding prompt.
4. **Read back, then report the diff.** Not "done." The paths actually
   touched and the lines actually added, re-read from disk. An agent
   reporting success it didn't verify is the most common way a
   paste-install half-works and nobody notices for a week.
5. **Name what's still manual.** There's almost always something — a
   session restart before new instructions load, most often. A prompt
   that ends on "installed!" leaves someone believing it's live when it
   isn't, and the next thing they conclude is that it doesn't work.

## The worked example — this repo's own block, line by line

```text
Set me up with the Playbooks standing-law vault:
https://github.com/kariemSeiam/playbooks

1. Clone it to ~/.playbooks — ask me first if you'd put it somewhere else.
2. Work out which agent harness you are and where your *global*
   instructions file lives (Claude Code: ~/.claude/CLAUDE.md, OpenCode:
   ~/.config/opencode/AGENTS.md, otherwise whichever one you actually read).
3. Append to it — never overwrite it, and update in place if a Playbooks
   pointer is already there — a short block telling yourself to check
   ~/.playbooks/README.md for a governing note before any non-trivial git,
   markdown, agent-extension, SEO, or business-domain decision, and to
   defer to the current project's own stated conventions wherever they
   differ from it.
4. Read the file back and show me exactly what changed.
5. Tell me whether I need to restart my session before it takes effect.

Ask before overwriting anything you did not create.
```

Reading it against the dial: step 2 delegates completely — "work out
which harness you are" hands the environment question to the only party
who can answer it, and the two paths in parentheses are examples to
pattern-match from, not an exhaustive switch statement. Steps 1, 3 and
the closing line are all consequence boundaries, and they're the only
places the prompt is prescriptive at all. Steps 4 and 5 exist because an
agent left to decide what "finished" means will pick a weaker definition
than the user would.

Note what isn't there: no `<YOUR_PATH>` placeholder (every one of those
converts a paste into an edit, and an edit into an abandoned install), no
explanation of what the project is (the README said that already —
re-explaining is wasted paste), no vendor name in the instructions to the
agent itself, only in the examples.

## What's worth questioning about it, not just copying

- **It assumes `git` and a writable `~`.** Both nearly always true,
  neither stated. An agent without network access will discover this
  halfway through, after the user has already spent attention.
- **The two named paths will age.** Harness config conventions move; this
  block hardcodes a snapshot of two of them. It belongs in the same
  re-verification pass as any other README claim
  ([discoverability-checklist.md](../github/discoverability-checklist.md)), not written once and trusted.
- **Step 4 verifies the file changed, not that it changed *correctly*.**
  A pointer block appended with a wrong path reads back perfectly. A
  stronger version would have the agent test the pointer resolves — the
  reason it doesn't is that the check costs more prompt length than the
  failure costs, which is a judgment call worth re-making as the block
  grows.
- **It cannot confirm the end state it promises.** "Your agent will now
  consult the playbooks" is true only if that agent actually re-reads its
  global instructions, which no prompt can force from inside the session
  that wrote them.

## Why this is a trust artifact, not just an installer

A pasted prompt is the first time a stranger's agent acts on their
machine on your behalf. Everything else a project ships is read before
it's run; this is run before it's read. A block that clobbers a config,
or claims success it didn't verify, isn't a bad install experience — it's
a demonstration that the project's author didn't think carefully about
consequences in someone else's environment, which is exactly the question
a reader is trying to answer about whether to adopt anything of yours at
all.

## Related

- [mechanism.md](skills/mechanism.md) — the per-harness config paths any onboarding
  prompt has to route between.
- [readme-craft.md](../language/markdown/readme-craft.md) — where in a README this
  block earns its place, and the structure around it.
- [discoverability-checklist.md](../github/discoverability-checklist.md) — the pass that should
  re-verify the block still points somewhere real.
