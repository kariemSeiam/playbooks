# The onboarding prompt — a recipe, or a note to someone who can cook

A recipe says: 180°C, middle rack, 22 minutes. A note to someone who can
cook says: bake until the edges pull away from the tin. The second is
shorter, and it survives an oven that runs hot. It also fails
differently — not when the oven is wrong, but when the cook has never
seen edges pull away and guesses.

An install script is a recipe. A pasted onboarding prompt is the note,
and the difference is worth being deliberate about, because the cook is
standing in a kitchen you have never seen.

## What becomes an outcome, and what stays a step

The useful split is by **who can see what**:

- **The environment — write outcomes.** Which harness is running, where
  its config lives, whether `git` or `curl` is the thing available here:
  all knowable to the agent, none of it knowable to you. Every line you
  spend pinning these down is a line that breaks somewhere you didn't
  test. Say what you want to be true and stop.
- **The consequences — write steps.** Which file in that directory took
  someone a year to build, which one is safe to append to: the agent
  cannot see this, and it cannot ask you, only the user. So anything
  irreversible gets named, explicitly, in the imperative.

Get the split backwards and both halves go wrong at once — a prompt that
dictates paths and waves at consequences is simultaneously brittle and
dangerous, which is the common shape in the wild.

## The five places the boundary lands

Once you've split it that way, these fall out rather than needing to be
remembered:

1. **Detect, don't assume.** A prompt that hardcodes one harness's config
   path doesn't fail loudly elsewhere — it quietly sets up the wrong
   thing. ([mechanism.md](skills/mechanism.md) has the per-harness paths.)
2. **Land somewhere durable.** A clone into a temp directory evaporates.
   One into the current directory pollutes whatever project the user
   happened to be standing in. Name a default; let it be confirmed.
3. **Append, never overwrite.** The only irreversible step in a typical
   setup. An agent told "add this to their config," with nothing further,
   will sometimes write the file whole.
4. **Read back, then show the diff.** Not "done" — the paths touched and
   the lines added, re-read from disk. Unverified success is how a
   paste-install half-works for a week before anyone notices.
5. **Say what's still manual.** Usually a session restart. A prompt that
   ends on "installed" leaves someone believing it's live, and when it
   isn't, their conclusion is that the project doesn't work.

## The worked example, read against that split

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

Step 2 is the outcome half: *work out which harness you are* hands the
question to the only party who can answer it, and the two paths in
brackets are examples to pattern-match from, not a list to match against.
Steps 1, 3 and the closing line are the consequence half — the only
prescriptive sentences in the block. Steps 4 and 5 are there because an
agent left to decide what "finished" means will pick a looser definition
than the user would have.

Worth noticing what isn't in it: no `<YOUR_PATH>` placeholder (each one
turns a paste into an edit, and an edit into an abandoned install), and
no description of the project — the README already did that, and
repeating it costs the one thing the block cannot afford, which is
length.

## Where it breaks

Four honest limits on the block above, none of them solved:

- **It assumes `git` and a writable `~`.** Nearly always true, nowhere
  stated. An agent without network access finds out halfway through,
  after the reader has already spent attention.
- **The two named paths will age.** Harness conventions move. The block
  is a snapshot of two of them, and belongs in the same re-verification
  pass as any other README claim
  ([discoverability-checklist.md](../github/discoverability-checklist.md)).
- **Step 4 checks that the file changed, not that it changed correctly.**
  A pointer written with a wrong path reads back perfectly. Testing that
  the pointer resolves would catch it, and costs more length than the
  failure currently costs — a trade worth re-making as the block grows.
- **It cannot confirm what it promises.** Whether the agent then actually
  consults the vault depends on it re-reading its global instructions,
  which nothing inside the session that wrote them can force.

## One structural thing about this format

Everything else a project ships is read before it runs. This is run
before it's read — most people paste first and inspect afterward, if at
all. That inverts who carries the risk, and it's the reason the
consequence half of the split is worth more care than the rest of the
README combined.

## Related

- [mechanism.md](skills/mechanism.md) — the per-harness config paths any onboarding
  prompt has to route between.
- [readme-craft.md](../language/markdown/readme-craft.md) — where in a README this
  block earns its place, and the structure around it.
- [discoverability-checklist.md](../github/discoverability-checklist.md) — the pass that should
  re-verify it still points somewhere real.
