# Discoverability checklist — run before making any repo public

[preflight-checklist.md](preflight-checklist.md) covers the safety of the action itself
(commit hygiene, secrets, push confirmation); this is the separate
checklist for whether the repo will actually be *found* once it's out —
run it once, right before flipping a repo public or right after, never
skipped as an afterthought weeks later when it's harder to fix without
losing history.

## 1. Description — structured, not a tagline

What / who / differentiator, in one line, checked against a real
character count — target under ~150 characters, not "as long as it takes
to say everything." A description that reads like a README's opening
paragraph is too long; a description that's just the repo name restated
says nothing. [developer-platform-discoverability.md](../seo/developer-platform-discoverability.md) has the full
reasoning.

## 2. Topics — researched, not guessed

1. Draft a candidate list from what the repo actually is: tech stack,
   domain, purpose — not vague adjacent buzzwords.
2. Check each candidate's real usage before trusting it — a topic that
   sounds perfectly descriptive can have near-zero traffic while a more
   generic one has real search volume. Verify, don't assume.
3. Check topics used by the closest 2-3 comparable real repos in the same
   space — this surfaces the actual canonical terms a category has
   converged on, which intuition alone won't reliably reconstruct.
4. Land on 5-10 topics covering multiple categories (language/stack,
   domain, purpose) — GitHub allows up to 20, but a pile of near-duplicate
   or irrelevant topics dilutes rather than helps; precision beats
   maximum count.

## 3. README — the on-page layer

Everything in [readme-craft.md](../language/markdown/readme-craft.md) and, if the repo
will ever be published to a package registry,
[package-readme.md](../language/markdown/package-readme.md). Leads with the case for why
this exists, not installation instructions — a reader deciding whether to
keep reading needs the "why" before the "how."

## 4. Social preview

Confirm a social preview image is set (repo Settings → Social preview) —
not a ranking factor, but the first thing anyone sees when the link is
shared anywhere outside GitHub itself (Slack, X, Discord, iMessage). A
missing or default preview is a real, avoidable drop in click-through on
every share.

## 5. AI-crawler layer, if the repo is genuinely knowledge-heavy

A `llms.txt` ([llms-txt.md](../language/markdown/llms-txt.md)) and explicit
`robots.txt` allowances for AI crawler user-agents, if the content is
meant to be found and cited by AI assistants, not just human search —
[generative-engine-optimization.md](../seo/generative-engine-optimization.md) has the reasoning for when
this is worth the setup versus premature ceremony for a repo with no
real audience yet.

## 6. License

A real `LICENSE` file, chosen deliberately (not defaulted). It also makes
the one never-decorative badge honest: a license badge answers a real
question the moment there's a file behind it,
per [readme-craft.md](../language/markdown/readme-craft.md)'s badge rule.

## What this checklist is not

Not a mandate to maximize every signal on day one. A repo with no real
content yet doesn't need an `llms.txt`; a repo nobody will ever publish to
a package registry doesn't need [package-readme.md](../language/markdown/package-readme.md)'s rendering
discipline. Run the checklist, apply what the repo's actual maturity
justifies — the same platform-maturity-ladder judgment [platform.md](platform.md)
already argues for GitHub's own features applies here too.

## Related

- [preflight-checklist.md](preflight-checklist.md) — the safety checklist this one is a
  sibling to, not a replacement for.
- **`../seo/`** — the full reasoning behind every item above.
