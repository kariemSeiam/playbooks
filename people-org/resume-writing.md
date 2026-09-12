---
domain: people-org
concept: Resume & CV Writing — content strategy and ATS mechanics
source: research — 2026 recruiter eye-tracking and ATS-parsing guidance, plus this operator's own applied build-and-revise process, 2026
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
  metrics are available to use.
- A resume has been producing no callbacks despite genuinely strong
  underlying experience — the content is very often the gap, not the
  qualifications.
- A resume reads fine but feels generic — usually a content problem
  (adjectives instead of numbers), not the design problem it's often
  mistaken for.

## How it works

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

**One page is the default under roughly three years of experience.** A
resume that runs long at that stage almost always has padding
somewhere, not signal. Beyond that, a second page has to earn its place
by containing something real that genuinely doesn't compress further —
and if a real second page exists, make the break itself a deliberate
structural choice (one page-per-life-stage, or current-role vs.
history), not an accident of where the content happened to run out of
room.

**Cut every claim that isn't checkable.** "Strong communicator,"
"detail-oriented" are true of nearly every resume that uses them and
verify nothing. The test: would a different piece of evidence make this
sentence false? If not, it's decoration — replace it with the concrete
thing that is checkable, or remove it.

**What actually breaks ATS parsing, mechanically.** Tables, multi-column
layouts, and text boxes scramble or drop content — a parser reading
across two columns as one stream turns a resume into word salad. Single-
column flow, top to bottom, is the only fully safe layout. Less obvious,
found by actually building and unzipping the result rather than assumed:
a Word document's native bulleted-list numbering renders through the
Symbol dingbat font by default — invisible on screen, a real and
completely avoidable parsing risk. A plain Unicode bullet character
embedded as literal text carries the same content with zero risk.
Equally invisible until checked: the document's own author metadata
defaults to whatever tool generated the file — worth setting explicitly
to the actual person's name before anyone opens File → Properties.

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
actually is. Once content is settled, verify the mechanical layer
directly rather than trust a template: unzip the actual `.docx` and grep
for `Symbol` in the document XML, confirm the author metadata is real,
and count pages with the file's real content, not an estimate.

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
- **Assuming a template's native bullet/heading styles are ATS-safe
  without checking.** The Symbol-font bullet issue above is invisible on
  screen in every common editor — it only shows up by inspecting the
  file's actual XML.

## Related

- [generative-engine-optimization.md](../seo/generative-engine-optimization.md) — the same
  front-load-the-checkable-claim discipline, applied to a different
  reader (an AI system synthesizing an answer instead of a recruiter
  scanning a page).
- [readme-craft.md](../language/markdown/readme-craft.md) — the same "who's actually
  reading this, in what order" thinking, applied to a different
  document type.
