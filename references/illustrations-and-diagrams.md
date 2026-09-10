# Illustrations & Diagrams

> "Inline SVG gives the agent a real pen. Ask for the figures for a post or a
> flowchart of a process and get vector art you can tweak by hand or paste
> straight into the final document." — Thariq

Don't fall back to ASCII or "imagine a flowchart that…" prose. Draw it. The
output is vector art the user edits by hand and copies out.

## Direct entry — closest original examples

| Example | When to use it | Dominant form | Key reader action |
|---|---|---|---|
| [SVG figure sheet](original-examples/10-svg-illustrations.html) · [live](https://thariqs.github.io/html-effectiveness/10-svg-illustrations.html) | Producing a set of diagrams for a post or document | One `<figure>` per diagram, consistent visual language across the set, "copy SVG" per figure | Locate — find the figure you need, copy it out for the destination document |
| [Annotated flowchart](original-examples/13-flowchart-diagram.html) · [live](https://thariqs.github.io/html-effectiveness/13-flowchart-diagram.html) | Visualising a process where each step has detail worth expanding | Flowchart as inline SVG; click a node to open a side panel with what runs there, timing, failure paths | Locate + Track — navigate the chart to find a step, expand it to see the detail |

Inspect how the examples separate the chart (navigation) from the detail panel (content); design your own information layering from that structure rather than cram all detail onto the nodes.

## Thariq's two demos

- **SVG figure sheet** — "The diagrams for a blog post, drawn inline so they can
  be tweaked and copied out one by one."
- **Annotated flowchart** — "A deploy pipeline drawn as a real flowchart — click
  any step to see what runs, timings, and failure paths."

## Building a figure sheet

- One figure per section, each a `<figure>` with a caption and a **"copy SVG"**
  button — the point is pasting them into the real document one by one.
- A **consistent visual language** across the set: same line weight, arrowheads,
  palette, type. A scattered set reads as amateurish even if each figure is fine.
- Size for reuse — inline `<svg>` that works on light and dark, no hard-coded
  colors that break in the destination.

## Building an annotated flowchart

- The flowchart as inline SVG, drawn properly: labelled nodes, directional edges
  (arrows — without them it's just a graph), branches visually distinct from the
  main path.
- **Click a node to expand a side panel** with what runs there, expected
  duration, what failure looks like, source links. The chart is the navigation;
  the panel is the content. Don't cram everything onto the chart.
- Highlight the **happy path** in a distinct color, failure/retry paths muted.
- Use **shape *and* color** to distinguish states, so it survives colorblind
  viewing and grayscale print. Abstract rare branches into one "error handling"
  subgraph rather than drawing 40 nodes.

## SVG craftsmanship

- `viewBox`, not fixed `width`/`height`, so it scales.
- `currentColor` for ink, so it inherits text color and adapts to dark mode.
- Round numbers (`x="120"`, not `x="119.7843"`) so a human can tweak by hand.
- Group with `<g>` and label, so an editor finds things by structure.
- Text as real `<text>`, not paths — selectable, copyable, accessible.
- No raster fallbacks. If it can be drawn, draw it.

## Sketch — labeled flow

```html
<figure>
  <svg viewBox="0 0 640 160" role="img" aria-labelledby="t">
    <title id="t">Deploy pipeline</title>
    <defs><marker id="tip" viewBox="0 0 10 10" refX="8" refY="5"
      markerWidth="6" markerHeight="6" orient="auto">
      <path d="M0,0 L10,5 L0,10 z" fill="currentColor"/></marker></defs>
    <g class="node" data-step="build">
      <rect x="20" y="60" width="110" height="40" rx="6" fill="none" stroke="currentColor"/>
      <text x="75" y="85" text-anchor="middle">build</text>
    </g>
    <g class="node" data-step="test">
      <rect x="180" y="60" width="110" height="40" rx="6" fill="none" stroke="currentColor"/>
      <text x="235" y="85" text-anchor="middle">test</text>
    </g>
    <line x1="130" y1="80" x2="180" y2="80" stroke="currentColor" marker-end="url(#tip)"/>
  </svg>
  <figcaption>Happy path solid, the rollback branch dashed. Click a step for timings.</figcaption>
  <button onclick="copyFigure(this)">Copy SVG</button>
</figure>
```

---

## When to bring in the Unknowns gallery

If the work has unresolved preferences, assumptions, or knowledge gaps — pre-implementation options still open, a choice the user has not yet made, or a hypothesis that needs testing — consult [`unknowns.md`](unknowns.md) for an appropriate exploration, prototype, clarification, or understanding check before building the final artifact.