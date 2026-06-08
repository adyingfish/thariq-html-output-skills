---
name: thariq-html-output
description: >-
  Produce a single self-contained HTML artifact instead of a markdown document
  whenever the thing being asked for has a *shape* that linear text would flatten:
  a comparison to weigh, spatial information (diffs, call-graphs, module maps,
  flowcharts, timelines), motion or interaction that has to be felt, a design
  surface, a reference document navigated non-linearly, a slide deck, an
  explainer, a recurring report, or a one-off editor for a task that is awkward
  to describe in a text box. The test is Thariq Shihipar's: would the reader
  *skim* a markdown version but *actually read* an HTML one? Trigger on requests
  for plans, comparisons, code reviews, PR writeups, module walkthroughs, design
  systems, component sheets, prototypes, animations, diagrams, flowcharts, decks,
  slides, explainers, concept walkthroughs, status updates, post-mortems,
  incident timelines, or throwaway editors / tools — even when the user never
  says "HTML" or "artifact." Stay in markdown only for short conversational
  replies, code-only answers, terminal/command answers, and content that is
  genuinely just a few sentences.
---

# HTML output

> "Twenty self-contained `.html` files an agent produced instead of a wall of
> markdown. Each one trades a document you'd skim for one you'd actually read."
> — Thariq Shihipar, *The Unreasonable Effectiveness of HTML*

This skill is a faithful operationalization of Thariq's post. It keeps his nine
categories exactly as he framed them, in his words, and it keeps his light
touch. The post deliberately gives examples rather than rules, because — in his
own words — "you don't need to do much to get an agent to do this." This skill
tries to be the smallest scaffolding that preserves that, not a fortress of
do's and don'ts.

## The recognition test

Before anything else, ask the one question the whole post turns on:

> **Does the thing I'm about to write have a shape that linear text would
> flatten — and would the reader skim a markdown version but actually read an
> HTML one?**

If yes, make an HTML artifact. If the answer is genuinely no — it's a sentence,
a snippet, a command — stay in markdown. That carve-out is real and matters;
see "When to stay in markdown" below. A skill that turned *every* prompt into
HTML would be exactly the thing Thariq worried about.

## The nine lenses

These are Thariq's nine categories, unchanged. Treat them as **lenses, not
buckets.** A request is rarely "a diagram" or "a plan" in isolation — it has one
or more shapes, and each shape is a lens you look through while building.

| Lens | Look through it when the request is about… | Reference |
|---|---|---|
| Exploration & Planning | weighing options side by side, or turning a decision into a hand-off plan | `references/exploration-and-planning.md` |
| Code Review & Understanding | annotated diffs, PR writeups, module maps, "explain this package" | `references/code-review-and-understanding.md` |
| Design | design systems, tokens, component contact sheets | `references/design.md` |
| Prototyping | motion, transitions, click-through flows — things that must be felt | `references/prototyping.md` |
| Illustrations & Diagrams | inline-SVG figures, flowcharts, architecture drawings | `references/illustrations-and-diagrams.md` |
| Decks | a short presentation to arrow-key through in a meeting | `references/decks.md` |
| Research & Learning | explainers, concept walkthroughs, navigable scaffolding for a new topic | `references/research-and-learning.md` |
| Reports | status updates, post-mortems, incident timelines | `references/reports.md` |
| Custom Editing Interfaces | a throwaway editor for a task awkward to type into a text box | `references/custom-editing-interfaces.md` |

## Composition is the default, not the exception

This is the heart of the skill, and it is Thariq's own design. His
*implementation plan* demo is described as:

> "Milestones on a timeline, a data-flow diagram, inline mockups, the risky
> code, and a risk table — the plan you hand off."

That single artifact is **Exploration + Illustrations + Design + Code Review
at once.** The lenses compose. So:

1. **Name every lens that applies.** Don't force the request into one category.
   Most artifacts need one; the richest need three or four.
2. **Read each named reference.** They're short and they're written to stack.
3. **Let the dominant lens set the skeleton**, and let the others contribute
   their patterns inside it. The implementation plan above is Exploration's
   skeleton (problem → options resolved → hand-off) with a diagram from
   Illustrations, mockups from Design, and an annotated snippet from Code Review
   embedded in it.

When in doubt, look through more lenses, not fewer. Composition is how Thariq's
best examples got their density.

## What every artifact owes the reader

These hold no matter which lenses built the artifact. They aren't a style guide —
each is part of what makes the difference Thariq names, between a page you'd skim
and one you'd actually read. They come down to three obligations.

**It has to stand on its own.** One `.html` file that opens in a browser with no
build step and no install — style, script, and imagery (inline SVG or data URIs)
all in the one file — and that still works with the network unplugged. If a font
or library has to come from a CDN, pick a stable one and assume it may need
inlining later. On a phone it should keep its shape rather than collapse: ship
the viewport tag and a layout that survives a narrow column.

**It has to show its shape.** This is the whole reason you reached past markdown,
so spend the effort here. Lay a comparison out in columns; draw a timeline as a
timeline; render a diff as a diff. Transcribing a markdown heading-stack 1:1 into
`<h2>`s throws the point away. And it has to land in about five seconds — a
title, one orienting line, then the substance — so the reader knows what they're
holding before deciding to read it.

**It has to stay honest.** Restraint is the default: legible type, a comfortable
measure, room to breathe, and color used only where it means something. The
moment an artifact lets the reader change state — drag, toggle, tune — it owes
them a way back out: a copy-as-markdown / copy-as-JSON / download control that
turns the manipulated UI back into text. Without that exit the editor is a
dead end; with it, in Thariq's phrase, the loop gets tighter.

## When the answer is markdown

The recognition test cuts both ways. When the content has no shape to flatten,
HTML is just ceremony — and reaching for it anyway is precisely the mechanical
reflex Thariq warned against. Stay in markdown when the reply is the kind of
thing you'd say in conversation: a sentence or two of answer, a single snippet
someone will paste as-is, a short run of shell commands, a list glanced at once
and discarded. None of these gain anything from a column, a color, or a click.

One case is subtler — a document that lives in version control and gets reviewed
in pull requests across many revisions. HTML diffs are noisy where markdown diffs
cleanly, so the long-lived spec is friendlier as markdown, even when a one-off
HTML *view* of it would read better today.

## Where the file goes

Write the artifact as one `.html` with a name that says what it is
(`pagination-options.html`, `deploy-pipeline.html`), then point the user at the
path and offer to open it for them. When a request spawns a set that belongs
together — an exploration that becomes a plan, say — keep them in one folder so
they travel as a unit. Keep everything self-contained in the one file: inline the
styles and scripts, keep editor state in memory, and prefer a bare `text/html`
document over React, Mermaid, or a raw SVG unless the ask is specifically for one
of those.

**Handing off to a smaller model or a subagent.** The references are written to
stand alone, so a cheaper executor needs only three things to build the artifact
cold: the original request, the three obligations above, and the full text of
each named lens's reference. Nothing else has to come along.

## A note on restraint

An ugly artifact is worse than plain markdown, and ugliness here has a
predictable source: the house style of generated UI, where every surface is a
tinted card, every heading wears an emoji, and a spread of near-identical accent
colors does no work at all. The fix isn't more taste layered on top — it's less.
Start from quiet typography (a real reading face for documents, a neutral sans
for tools), give it space, and introduce a color only at the moment it has a job
to do: a status, a severity, an axis. If the project already has a design system
or a `frontend-design` skill, take its tokens instead of inventing your own. The
bar is Thariq's: his examples look like things a person sat and read, not things
a machine emitted. Aim there.

## A note on what this is not

Not "always answer in HTML." The point was never the format. The point is that
for many of the things people now ask agents to make — plans, comparisons,
reviews, explainers, editors — markdown's linear, color-less, static shape
*actively obscures the content*, and HTML lifts that. Where markdown is the
better medium, use markdown. The skill is the recognition, not the reflex.
