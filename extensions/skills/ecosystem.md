# The open Skills ecosystem

Three different things, not one — check the right one for what's actually
being searched for, and don't treat a thin result on one as a thin result
on all of them:

- **[skills.sh](https://skills.sh)** (`vercel-labs/skills`, MIT, open
  source) — a registry and CLI (`npx skills find|add|list|update`), not a
  runtime of its own. Its own `find-skills` skill is installed globally
  here (`~/.claude/skills/find-skills`) and is the right tool to search
  this registry before building something from scratch.
- **[ClawHub](https://clawhub.ai)** — OpenClaw's marketplace, skills and
  plugins together, published and installed through its own CLI with an
  explicit "install → scan → publish → verify" security posture. A
  different ecosystem than skills.sh, not interchangeable with it — check
  both if a search on one comes up thin.
- **[Hermes (`mturac/hermes-supercode-skills`)](https://github.com/mturac/hermes-supercode-skills)**
  — not a registry, a single well-built set of 13 skills, worth studying
  for its shape rather than installing: every skill runs
  Recon → Plan → Execute → Verify, marks each action 🔴 never / 🟡
  confirm first / 🟢 safe, and keeps its `SKILL.md` lean with heavy detail
  pushed to a `references/` folder loaded only on demand.

## Before writing a new one: check the registry, but don't defer to it blindly

`find-skills`' own stated bar — prefer 1K+ installs, be suspicious under
100, trust official sources (`vercel-labs`, `anthropics`) over unknown
ones — is a real filter. Searching it for git/GitHub discipline and for
skill-authoring itself both came back with nothing past a few hundred
installs and no official source. When a search comes up thin against
what's already sitting in this vault, that's the signal to build here
rather than import — not a failure of the search.

## Related

- [mechanism.md](mechanism.md) — what a Skill actually is and where it lives, before
  deciding whether to import one or build one.
- [promotion-and-authoring.md](promotion-and-authoring.md) — the convention to follow once the
  answer is "build one."
