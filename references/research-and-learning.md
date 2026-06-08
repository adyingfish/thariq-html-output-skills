# Research & Learning

> "An explainer with collapsible sections, tabbed code samples and a glossary in
> the margin reads very differently from the same words dumped linearly. The
> agent can build the scaffolding that makes a new topic navigable." — Thariq

The lens for *teaching* — turning a topic into something the reader can navigate
non-linearly instead of reading front to back.

## Thariq's two demos

- **How a feature works** — "'Explain rate limiting in this repo' — TL;DR box,
  collapsible request-path steps, tabbed config snippets, and an FAQ."
- **Concept explainer** — "Consistent hashing taught with a live ring you can
  add/remove nodes from, a comparison table, and a hover-linked glossary."

## Building a feature explainer (code in a repo)

- A **TL;DR box** at the top: what it does, where it lives, key files.
- **Collapsible sections** for each phase of the lifecycle — deep stuff
  default-collapsed, the overview default-open. Code explainers are dense; let
  the reader expand only what they need.
- **Tabbed code snippets** — the same logic in TypeScript, Python, the test, the
  config — to save vertical space. Annotate the interesting lines.
- An **FAQ** at the bottom; it's where the reader's actual questions live. Plus
  "where to look next" links into the codebase.

## Building a concept explainer (a new topic)

- Title, subtitle, and a **one-paragraph TL;DR before any technical content** —
  the reader should know what they're about to learn in 15 seconds. Don't bury
  the punchline; the TL;DR gives away the answer.
- The core insight as a single sentence, most important word emphasized.
- A **live interactive demo** if the concept is spatial or stateful (hashing,
  sharding, scheduling, queuing). A five-second interaction beats five
  paragraphs. Don't skip it because "the reader can imagine it" — they can't,
  that's why they're here. (This reaches into Prototyping / Illustrations — read
  those for the interactive and SVG craft.)
- A comparison to the naive approach **with numbers, not adjectives** — "moves
  1/N keys instead of (N−1)/N," not "better."
- A **glossary in the margin** with hover-link cross-refs from the body. Bottom
  glossaries are never read; marginal ones get scanned.

## Sketch — concept explainer with live demo

```html
<main class="explainer">
  <header>
    <h1>Consistent hashing, on a ring</h1>
    <p class="tldr">Put nodes and keys on the same circle; a key belongs to the
       next node clockwise. Add or drop a node and only its arc reshuffles —
       about K/N keys move, not all of them.</p>
  </header>
  <section>
    <h2>The trick: a circle, not a line</h2>
    <figure class="demo">
      <svg id="ring" viewBox="0 0 320 320"><!-- nodes + keys on the circle --></svg>
      <div class="controls">
        <label>nodes <input type="range" id="n" min="2" max="10" value="5"></label>
        <button data-act="drop">Drop a node</button>
        <button data-act="add">Add a node</button>
      </div>
      <output id="moved">last change moved — keys</output>
    </figure>
  </section>
  <table class="vs"><caption>vs. hash mod N</caption>…</table>
  <aside class="glossary"><dl><dt>arc</dt><dd>the span of ring a node owns.</dd></dl></aside>
</main>
```
