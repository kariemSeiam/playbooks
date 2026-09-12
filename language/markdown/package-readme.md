# Package-registry rendering — npm, PyPI, and the GitHub-chrome trap

A package's README renders in at least two places that matter: the GitHub
repo page, and the registry page (npmjs.com, pypi.org) a user actually
lands on from `npm install <pkg>`. These two renderers are not the same
<!-- markdownlint-disable-next-line MD044 -->
software, and [github-flavor.md](github-flavor.md)'s entire toolkit is, by definition,
GitHub-exclusive — nothing in it is guaranteed to survive the trip to a
registry page. This matters directly for any package of your own that's
published to npm — it is real, checkable behavior, not a hypothetical,
whether its README still reads correctly there.

## What npm actually renders

npmjs.com renders README content through `marked`, a CommonMark/GFM
*parser* — not GitHub's rendering pipeline. `marked` implements the GFM
**specification** (tables, task lists, strikethrough, autolinks) at high
fidelity. It does not implement GitHub's own proprietary UI additions on
top of that spec, because those aren't part of the GFM spec at all —
they're GitHub's own post-processing:

| Feature | npm (via `marked`) | Why |
|---|---|---|
| Tables, task lists, strikethrough, autolinks | Renders correctly | Part of the GFM spec `marked` implements |
| Fenced code blocks with language | Renders correctly, syntax-highlighted | Standard CommonMark |
| `> [!NOTE]`-style alerts | **Does not render** — shows as a plain blockquote with the literal `[!NOTE]` text | GitHub-proprietary, not GFM-spec |
| ` ```mermaid ` diagrams | **Does not render** — shows as a plain code block | GitHub's own JS widget, not part of any markdown spec |
| `<details>`/`<summary>` | Usually survives (standard HTML5, commonly allow-listed by the sanitizer) | Verify on the actual published page rather than assume |
| `<div align="center">`, `<picture>` | Commonly survives, but registry sanitizers vary and change over time | Same — check the live page |

<!-- markdownlint-disable-next-line MD044 -->
The practical rule: **anything from [github-flavor.md](github-flavor.md)'s alert or
diagram sections will silently degrade to plain, sometimes-ugly text on
a registry page.** This isn't a corner case — a README that opens with a
GFM alert box or leads with a Mermaid architecture diagram will look
broken to the first-time visitor most likely to actually be looking,
someone who just ran `npm install` and clicked through.

## Relative links and images

GitHub resolves a repo-relative image path (`![logo](./assets/logo.png)`)
against the repo's own file tree. A registry page is not the repo — it's
rendering the README's text as fetched from the published tarball or the
registry's own mirror, and a relative path frequently resolves to nothing
there. Use an absolute URL (the GitHub raw content URL, or a CDN-hosted
asset) for any image in a README that will be published to a registry —
verify by viewing the actual published package page, not by trusting
that "it worked on GitHub."

## What this means in practice

For a package meant to be read on both surfaces: keep the registry-unsafe
chrome (alerts, Mermaid) out of the parts of the README a
registry-page-only reader needs — the install command, the one-line
pitch, the first code example — and reserve them for sections deeper in
the file, or push them into a separate doc (`ARCHITECTURE.md`,
<!-- markdownlint-disable-next-line MD044 -->
`docs/*.md`) that's only ever read on github.com in the first place.
Doing this correctly looks like a Mermaid-free, alert-free [README.md](README.md)
that carries the install/quick-start path, while `ARCHITECTURE.md` holds
the GitHub-only diagrams. Verify a change to either by opening the actual
npmjs.com page after publish, not by assuming from the GitHub preview.
