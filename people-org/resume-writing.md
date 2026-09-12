---
domain: people-org
concept: Resume & CV Writing — content strategy and ATS mechanics
source: research — 2026 recruiter eye-tracking and hiring-manager surveys, cross-platform ATS parsing studies (Workday/Greenhouse/Lever/iCIMS/Taleo), regional resume-photo/legal-norm studies, plus this operator's own applied build-and-revise process, 2026
tags: [resume, cv, career-coaching, ats, recruiting]
---

# Resume & CV writing: content strategy and ATS mechanics

A resume is read twice, by two different readers, in that order: a
machine that decides whether a human ever sees it, then a human who
decides in seconds whether to keep reading. Most resume advice optimizes
for one pass and quietly damages the other — keyword-stuffing that reads
as robotic to the human, or personality-led prose a parser can't extract
a fact from. Writing well for both at once is the actual skill, not a
design problem to solve after the words are settled.

## When to use

- Someone asks for help rewriting or reviewing a resume/CV, at any career
  stage — the framework doesn't change with seniority, only which
  metrics are available to use and how much history there is to compress.
- A resume has been producing no callbacks despite genuinely strong
  underlying experience — the content is very often the gap, not the
  qualifications.
- A resume reads fine but feels generic — usually a content problem
  (adjectives instead of numbers), not the design problem it's often
  mistaken for.
- A resume has a real employment gap, a career change, or 10+ years of
  history to compress — the three situations where the default advice
  ("just use reverse-chronological, one page") stops being sufficient on
  its own and needs a real judgment call.

## How it works

### Content

**Front-load the number.** Recruiter eye-tracking data puts the first
scan of a resume under seven seconds — the summary and the first bullet
under each role get read closely, everything else gets skimmed for
shape. The single strongest, most specific claim belongs in the first
sentence, not built up to three lines in.

**Quantify with the metric the reader's own field actually tracks.**
"Improved efficiency" is unverifiable; the number that makes a domain
expert nod is specific to that domain — a sales resume needs quota
attainment, a support resume needs resolution time, an engineering
resume needs a measured performance delta. Ask what insiders in that
function measure themselves on, not what sounds impressive from outside.

**A fast internal promotion is a headline, not a footnote.** Two titles
at one company close together in time reads as "someone else already
vetted this person" — stack both roles under one company header and
state the promotion explicitly in a bullet, rather than leaving a
reader to notice a date gap and infer it.

**Cut every claim that isn't checkable.** "Strong communicator,"
"detail-oriented" are true of nearly every resume that uses them and
verify nothing. The test: would a different piece of evidence make this
sentence false? If not, it's decoration — replace it with the concrete
thing that is checkable, or remove it. **"References available upon
request" is the same failure in a different shape** — it's assumed by
default, so it spends a line saying nothing, and its real function now
is dating the document. Drop it with no replacement; keep an actual
reference sheet ready, in the resume's own header/format, to hand over
only once it's asked for, typically after a second interview.

**Reverse-chronological is the default for a real reason, not just
convention.** Most recruiters and hiring managers name it their
preferred format, and it's the one every ATS parses reliably. A pure
functional or skills-first format that hides the timeline is read as a
gap-hiding or job-hopping signal now, not a neutral stylistic choice —
some ATS fail to parse it cleanly at all. The legitimate middle path for
a real career change or gap is a **hybrid**: a skills-forward summary up
top, then a full, honest reverse-chronological history underneath it —
gets the framing benefit without triggering the red flag a pure
functional resume does.

**Length scales with how much real signal there is, not a fixed number.**
Under roughly three years of experience, one page is the default — a
resume that runs long at that stage almost always has padding somewhere.
Past that, the rule inverts: a candidate with 10–15 years who compresses
to one page is very often losing real, relevant signal, and two pages is
standard at that stage, not a maximum. The structuring move that makes a
long history actually work: full detail on the most recent 10–15 years,
everything earlier condensed to a single line each under an "Earlier
Career" heading — length grows with the years worth detailing, not the
years worth mentioning. Executive, academic, and federal resumes can
run to three pages for the same reason. Whatever the length, a genuine
second (or third) page should read as a deliberate section — current
role vs. history, or recent vs. earlier career — never spacing stretched
to fill a target or content crammed to avoid one.

**A real employment gap gets a labeled line, not a disappearing act.**
Current hiring-manager sentiment has shifted decisively toward openness
on this — most report they're open to candidates with a break once it's
handled honestly. The concrete move: a dated line on the resume itself
("Career Break — [reason]," year-only if the gap is short) rather than
silence the reader has to notice and guess at. Anything productive
during the gap — a certification, freelance work, caregiving with a
real skill built from it — earns its own line with a number attached if
one exists; naming that activity is the single most effective thing a
gap line can do.

### Mechanics

**What actually breaks ATS parsing, structurally.** Tables, multi-column
layouts, and text boxes scramble or drop content — a parser reading
across two columns as one stream turns a resume into word salad. Single-
column flow, top to bottom, is the only fully safe layout.

**Font choice is a real, measurable risk, not superstition.** A parser
substitutes a fallback font for anything not installed on the system
reading it, and substitution is what actually drops or merges
characters — the font name itself doesn't matter, universal
availability does. Calibri, Arial, Helvetica, Verdana, Georgia, and
Cambria are all safe defaults for this reason. Treat anything not
bundled with every common OS — a downloaded Google Font, a display or
condensed face — as unverified risk until checked the way the bullet
glyph below was.

**Two more risks invisible on screen, found only by unzipping the
actual file and reading its XML, not by assuming a template is safe:** a
Word document's native bulleted-list numbering renders through the
Symbol dingbat font by default — a real, completely avoidable parsing
risk with a zero-cost fix (a plain Unicode bullet character embedded as
literal text carries identical content with none of the risk). And the
document's own author metadata defaults to whatever tool generated the
file, worth setting explicitly to the actual person's name before
anyone opens File → Properties.

**PDF vs. DOCX is a platform question, not a universal rule.** Older
Taleo deployments and some Workday configurations parse DOCX
measurably more reliably; Greenhouse, Lever, iCIMS, and Ashby parse a
clean text-layer PDF equally well, with no DOCX advantage. Document
*complexity* — the tables/columns/text-boxes rule above — matters more
than the format choice either way. Default to PDF; fall back to DOCX
specifically when an application flags an upload warning or is known to
run on a legacy Taleo/Workday portal.

**Keyword matching has gone hybrid, and the method that follows from
that is concrete.** Modern ATS combine exact-phrase matching with
semantic/contextual scoring — "program management" now scores partial
credit against "project management" — but an exact match still scores
higher wherever the real language allows it. The actual technique: pull
the literal phrase from the job posting and use it verbatim at least
once, inside a real sentence where it's true. This is targeted
phrase-matching, not keyword-stuffing a list at the bottom of the page
— a stuffed list reads as manipulation to the human pass even when it
helps the machine pass.

**A photo is a real, unresolved regional question — confirm the
specific country, don't default either way.** In the US, UK, Canada,
Australia, and Ireland it's a near-hard no, and the reasoning is legal
as much as stylistic: studies on photo-included resumes have found
measurable bias that helps attractive men and hurts women regardless of
attractiveness, which is part of why it reads as a liability to a
Western employer, not just a stylistic miss. Germany still commonly
expects a small headshot; the Netherlands has drifted toward no-photo
over the last decade but isn't settled; the UAE and much of the Middle
East, along with parts of Asia, still commonly expect one. Ask, or check
a real local norm, before assuming either convention applies.

## Example

Two resumes for people with materially similar underlying experience.
One opens: *"Motivated professional with strong problem-solving skills."*
The other: *"Reduced average resolution time 30% across a 40-person
team, while holding a 95%+ satisfaction score."* The second is checkable
and front-loaded — a reader forms a real opinion of this person's actual
work in one sentence. The first could describe almost anyone, including
someone who has never done the job.

## Applying it for a client

Ask what the target role's own function actually measures itself on
before touching layout at all — content problems dressed up in better
formatting are still content problems. If the person has a fast
promotion or a title change in their history, that's very often the
single highest-leverage rewrite available; most people undersell it by
treating it as a date change instead of the credibility signal it
actually is. Pull the actual job posting before finalizing anything and
work its literal key phrases into real sentences, not a keyword list.
Once content is settled, verify the mechanical layer directly rather
than trust a template: unzip the actual `.docx` and grep for `Symbol` in
the document XML, confirm the author metadata is real, confirm the font
is a universally-installed one, and count pages with the file's real
content, not an estimate.

## Watch-outs

- **Inventing a number that isn't real.** A fabricated metric is worse
  than a vague sentence — it's a specific, false, checkable claim,
  discoverable at the first real interview question about it.
- **Bolding every number with the same weight regardless of scale.** A
  small real number bolded identically to a large one creates a false
  equivalence a careful reader notices.
- **Treating a class project or volunteer role with the exact register
  of a paid job.** Language normal for full-time work reads as inflated
  applied to a few hours of volunteering — match the register to what
  the activity actually was.
- **Squeezing content to hit a page target by shrinking whitespace
  instead of cutting weak content.** A cramped, tiny-margin one-pager
  reads as trying too hard to fit — and often reads worse than a
  clean, well-spaced two-pager. Cut a redundant bullet before shrinking
  a font.
- **Assuming a template's native bullet/heading styles, or its font, are
  ATS-safe without checking.** Both risks above are invisible on screen
  in every common editor — they only show up by inspecting the file's
  actual XML or confirming the font is one every system already has.
- **Defaulting a functional format onto a real career-change or gap
  situation.** It reads as hiding the thing it's meant to soften — the
  hybrid structure above gets the same benefit without the same
  suspicion.
- **Assuming the photo convention from one country applies to another.**
  This is genuinely regional and not settled even within a region —
  confirm rather than default.

## Related

- [generative-engine-optimization.md](../seo/generative-engine-optimization.md) — the same
  front-load-the-checkable-claim discipline, applied to a different
  reader (an AI system synthesizing an answer instead of a recruiter
  scanning a page).
- [readme-craft.md](../language/markdown/readme-craft.md) — the same "who's actually
  reading this, in what order" thinking, applied to a different
  document type.
