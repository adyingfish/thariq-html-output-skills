# Thariq-following HTML interaction for agents

**English** | [简体中文](README.zh.md)

A Claude skill that grew out of [Thariq Shihipar's *The Unreasonable
Effectiveness of HTML*](https://thariqs.github.io/html-effectiveness/) and tries
to carry the part of it that's easiest to lose: the **judgment** — when HTML
helps, and when to leave it alone.

Thariq worried, in the post itself, that someone would turn it into a mechanical
"/html skill." That worry is the design brief. A skill that reflexively
converted every prompt into HTML would throw away the thing he actually cared
about. So this one is built around recognition and restraint, not around a
rulebook.

Three commitments follow from that:

- **Recognition, not keyword matching.** The whole post turns on one question —
  *would the reader skim a markdown version but actually read an HTML one?* The
  skill triggers on that perception of *shape*, and it is just as clear about
  when **not** to reach for HTML.
- **Lenses, not buckets.** The nine categories aren't slots you file a request
  into; they're lenses you look through, and they compose. A single artifact can
  be built through several at once — Thariq's own *implementation plan* demo is
  Exploration + Diagrams + Design + Code Review in one file. Keeping the nine
  distinct (rather than collapsing them) is itself a judgment: different shapes
  deserve different ways of looking.
- **Light touch.** "You don't need to do much to get Claude to do this." So the
  skill stays the minimum scaffolding — framing and examples, then it gets out
  of the way and trusts the model. Each reference leans on Thariq's own sharp
  observations not as relics to preserve, but as the fastest way to recognize a
  shape while building.

## Design philosophy

Four principles, each read back out of the original article — and out of the one
worry it ends on:

1. **Triggering is a perception, not a keyword match.** The whole post turns on
   one question — *"would the reader skim a markdown version but actually read an
   HTML one?"* The `description` in `SKILL.md` describes that perception of
   *shape* and offers the nine categories as vocabulary for naming the shape you
   saw, not as a routing table you match one row of. It is equally explicit
   about the carve-out: where markdown is the better medium, stay there.

2. **Categories are lenses that compose.** `SKILL.md` instructs the model to
   *name every lens that applies* and read each named reference, letting the
   dominant lens set the skeleton and the others contribute patterns inside it.
   The references are written to stack, and several point at each other
   (the module map borrows from Illustrations; the post-mortem borrows from
   Research & Learning).

3. **Trust the model.** The deepest reading of the post is to *not* turn it into
   a rulebook. So the references favor a few load-bearing points and Thariq's
   own sentences over exhaustive do/don't lists. The skill gives framing and
   examples, then gets out of the way and lets the model see what each artifact
   wants to be.

4. **The artifact must earn the read.** Every artifact holds to a small set of
   universal qualities — self-contained, works offline, real layout, readable in
   five seconds, editors export back to text — because those are what separate
   "a document you'd skim" from "one you'd actually read."

## Structure

```
thariq-html-output-skills/
├── SKILL.md                                    # recognition test, 9 lenses, composition, universal qualities
└── references/
    ├── exploration-and-planning.md
    ├── code-review-and-understanding.md
    ├── design.md
    ├── prototyping.md
    ├── illustrations-and-diagrams.md
    ├── decks.md
    ├── research-and-learning.md
    ├── reports.md
    └── custom-editing-interfaces.md
```

`SKILL.md` is always in context once the skill triggers. References are pulled
in by the lenses a request looks through — usually one, sometimes several.

## Running on a smaller model / subagent

The references are self-sufficient. To route generation to a cheaper model or a
subagent, hand it three things: (a) the user's original request, (b) the three
obligations from the "What every artifact owes the reader" section of `SKILL.md`,
and (c) the full text of every named reference. That package is everything needed
to build the artifact with no further context — see "Where the file goes" in
`SKILL.md`.

## Credits & license

Grew out of Thariq Shihipar's *The Unreasonable Effectiveness of HTML* and its
[companion site](https://thariqs.github.io/html-effectiveness/). The nine
categories and the framing are his; the recognition test, the composition model,
and the universal qualities are the extensions — an attempt to carry his
judgment, not just his examples.

MIT
