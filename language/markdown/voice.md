# Voice — the prose layer

Syntax ([syntax.md](syntax.md)) is what makes a document mechanically correct. Voice
is what makes it worth reading. The research converges on something worth
naming plainly: every major technical-writing style guide (Microsoft's,
Google's) arrives at almost exactly the pact a well-tuned AI agent's own
instructions already encode — this isn't new instruction, it's
confirmation that "answer first, no filler" is not a house quirk, it's
the actual professional standard, independently discovered by people with
no reason to agree with each other except that it's what works.

## Scannable first, readable second

Readers of technical documents don't read start to finish — they scan for
the part that answers their question, then read that part closely. Write
for that behavior instead of fighting it:

- **The answer or the point goes first in a section**, not at the end of
  a paragraph building up to it. A reader (or an agent) who stops after
  the first sentence should still have the substance.
- **One idea per paragraph, one topic per section.** A paragraph that
  drifts across two ideas is a paragraph a scanning reader will
  misjudge — they'll read the first idea, decide the paragraph isn't
  relevant, and skip the second idea that actually was.
- **Structure carries meaning before prose does.** A reader should be able
  to tell what a document contains from its headings alone, without
  reading a single sentence of body text — that's the actual test of
  whether the structure is doing its job.

## Active voice, concrete subject

"The button can be clicked to start the process" hides who does what to
whom; "click the button to start the process" doesn't. This isn't a
grammar preference — passive voice systematically hides the actor, and in
technical writing the actor (what does this, what causes that) is usually
the entire point. Default to active voice; the exception is when the
actor is genuinely unknown or irrelevant to the point being made, not when
active voice would just require more thought to phrase.

## Plain language over jargon, but not at the cost of precision

Short, ordinary words over long, impressive ones, when they mean the same
thing — "use" not "utilize," "help" not "facilitate." This is not about
dumbing content down; it's that unnecessary latinate vocabulary makes a
reader work to decode word choice instead of spending that effort on the
actual idea. The exception that matters: a genuine technical term (the
name of a specific mechanism, a specific error, a specific tool) is
precision, not jargon — don't paraphrase away the one word that lets a
future reader grep for this exact concept.

## No filler — the same discipline stated for prose specifically

- No throat-clearing before the point ("It's worth noting that...", "One
  thing to consider is...") — cut straight to the noted thing.
- No hedging that isn't load-bearing ("might potentially", "in some
  cases, possibly") — if a claim is uncertain, say what's actually
  uncertain about it in concrete terms, don't blur it with vague
  qualifiers that could apply to anything.
- No restating what a heading or a table already said, in prose, right
  below it. If the heading says what the section is about, the first
  sentence doesn't need to say it again before getting to content.
- No manufactured transitions ("Now that we've covered X, let's move on
  to Y") — the heading for Y already tells the reader that's what's next.

## The voice test

After writing anything non-trivial: strip the markdown formatting —
headers, bold, tables, lists — and read the remaining prose as plain
text. Does it still say something, in a voice that sounds like genuine
judgment, or does it collapse into vague, interchangeable filler the
moment the formatting stops doing the work of looking organized? A
document that only reads as authoritative *because* it's formatted like
one is a document that hasn't actually said anything yet.
