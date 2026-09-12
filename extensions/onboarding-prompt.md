# The onboarding prompt — a README block that makes the reader's agent the installer

A new distribution surface, specific to this era: instead of
`npm install x` and a page of manual setup steps, a public repo can ship
**one fenced block a human copies into whatever agent they already run**,
and that agent does the setup — detecting its own environment, choosing
the right paths, merging rather than clobbering, and reporting what it
changed. The install instructions stop being a script the human executes
and become a goal the agent executes.

This note is the standing law for writing one, because the failure modes
are specific and the good version isn't obvious.

## What the prompt is actually for

Not "explain the project" — the README already does that, and a prompt
that re-explains is wasted paste. The prompt's only job is **to get from
"a human is interested" to "their agent is actually set up," without the
human reading setup docs at all.** Everything that isn't in service of
that is padding, and padding is what makes a block too long to paste.

## The flow it has to control, end to end

The moment the human pastes, the publisher loses direct control and the
prompt is the only steering left. It has to specify all five of these, or
the agent improvises — and improvisation is where the damage happens:

1. **Detect, don't assume.** Which harness is running, and therefore
   which config paths are real, is something the agent can determine and
   the publisher cannot ([mechanism.md](skills/mechanism.md) has the per-harness paths).
   A prompt hardcoding one harness's path breaks silently for everyone
   else.
2. **Land somewhere durable and predictable.** A clone into a temp
   directory, or into whatever the current working directory happens to
   be, is a setup that evaporates or pollutes. State a sensible default
   and let the agent confirm it.
3. **Merge, never clobber.** This is the one that does real damage: a
   user's global agent-instructions file is *theirs*, often carefully
   built. The prompt must say append-or-update-in-place explicitly. An
   agent told "add this to their config" without that constraint will
   sometimes write the file wholesale.
4. **Verify, then report what changed.** Not "done" — the actual paths
   touched and the actual lines added, read back from disk. An agent that
   reports success without reading back is the single most common way a
   paste-install silently half-works.
5. **Say what's still manual.** Almost always at least one thing: a
   session restart before new instructions load, for instance. A prompt
   that ends without naming it leaves the human thinking it's live when
   it isn't.

## Craft rules

- **Goal plus constraints, not a rigid script.** A numbered list of exact
  shell commands breaks on the first environment that differs. State the
  outcome and the boundaries, and let the agent pick the commands — that
  is the entire reason this pattern beats a manual install section.
- **No placeholders the human has to fill in.** Every `<YOUR_PATH_HERE>`
  is a step where a paste becomes an edit, and an edit becomes an
  abandoned install. If something genuinely varies, have the agent ask,
  not the human pre-fill.
- **Short enough to look pasteable.** The block is scanned before it's
  read; a screen-and-a-half of text reads as "this will be complicated"
  and loses people who would have pasted ten lines. Cut anything the
  agent could reasonably infer.
- **Harness-agnostic phrasing.** "your agent," not "Claude" — the same
  block should work pasted into any harness, which is the whole premise
  of [the repo's own cross-harness claim](../README.md). Naming one
  vendor makes it read as not-for-me to everyone else.
- **Make the destructive branch ask.** Anywhere the agent might overwrite
  or delete, the prompt says to confirm first. This is cheap to write and
  the only thing standing between a bad inference and someone's config.

## Watch-outs

- **A prompt that assumes network or tooling that may not be there** (a
  specific package manager, a specific clone method) fails at the worst
  moment — after the human has already committed attention. Prefer
  phrasing that lets the agent choose the mechanism it actually has.
- **Instructing an agent to modify files outside the project it's in** is
  a real permission boundary in most harnesses — the prompt should expect
  the agent to need approval for that, and should not be written as
  though it will happen silently.
- **Stale prompt, moved repo.** The block hardcodes at least a URL. It
  belongs in the same review pass as any other README claim
  ([discoverability-checklist.md](../github/discoverability-checklist.md)), not written once and
  forgotten.

## Related

- [mechanism.md](skills/mechanism.md) — the per-harness config paths any onboarding
  prompt has to route between.
- [readme-craft.md](../language/markdown/readme-craft.md) — where in a README this
  block earns its place, and the surrounding structure it sits in.
- [discoverability-checklist.md](../github/discoverability-checklist.md) — the pass that should
  re-verify the block still points somewhere real.
