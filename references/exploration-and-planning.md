# Exploration & Planning

> "When you're not sure what you want yet. Ask the agent to fan out across
> several directions and lay them next to each other so you can point at one —
> instead of reading three sequential walls of text and trying to hold them all
> in your head. And once you've picked, turn the pick into a plan the
> implementer can actually read." — Thariq

Two moments live in this lens: *before* the decision (fan out, compare) and
*after* it (a plan you hand off). Both are about making a shape visible — the
shape of a choice, or the shape of a change.

## Direct entry — closest original examples

| Example | When to use it | Dominant form | Key reader action |
|---|---|---|---|
| [Three code approaches](original-examples/01-exploration-code-approaches.html) · [live](https://thariqs.github.io/html-effectiveness/01-exploration-code-approaches.html) | Comparing 2–4 concrete solutions side by side | Three columns, identical internal structure, hard metrics | Compare — eye scans horizontally across columns |
| [Implementation plan](original-examples/16-implementation-plan.html) · [live](https://thariqs.github.io/html-effectiveness/16-implementation-plan.html) | Handing off a decision that needs a timeline, diagram, and risk table | Milestones strip + data-flow SVG + risk table + annotated snippet | Follow — reader steps through phases in order |
| [Visual design directions](original-examples/02-exploration-visual-designs.html) · [live](https://thariqs.github.io/html-effectiveness/02-exploration-visual-designs.html) | Rendering 3–4 design options so preferences can be pointed at | Live rendered options side by side, no description-only | Compare + Try — react to the rendered thing, not imagine it |

Inspect the spatial relationships and information hierarchy of the closest example; design around your current material rather than copying its shell.

## Thariq's three demos

- **Three code approaches** — "Side-by-side comparison of three ways to solve
  the same problem, with trade-offs called out inline."
- **Visual design directions** — "A handful of layout and palette options
  rendered live so you can react to them, not imagine them."
- **Implementation plan** — "Milestones on a timeline, a data-flow diagram,
  inline mockups, the risky code, and a risk table — the plan you hand off."

## Building a side-by-side comparison

The single biggest win HTML has here. Three approaches in markdown is three
sequential sections the reader holds in their head at once; in HTML it's three
columns they scan across.

- One column per option (a responsive card grid past ~4 options).
- **Identical internal structure** in every column — same headings, same
  sub-sections — so the eye compares horizontally. A metric present in one
  column and missing in another reads as a weakness, even if you just forgot it.
- Inside each: a framing sentence, the real artifact (code / mockup / sketch), a
  pro/con **table** (a table reads as a comparison; bullets read as a sequence),
  and a row of hard metrics that force the recommendation to be defensible.
- End by **actually picking one** and saying why. "Show me three ways" means the
  reader wants help choosing.

## Building the implementation plan

Note this is the canonical composite — it reaches into Illustrations (the
data-flow diagram), Design (inline mockups), and Code Review (the annotated
risky snippet). Read those references too if the plan needs them.

- A one-paragraph problem statement, then a **milestones strip** as a real
  visual timeline — not a numbered list.
- A **data-flow diagram** (inline SVG) if the system has more than two parts.
  The reader can't hold the topology from prose alone; don't make them.
- The 2–3 load-bearing snippets, annotated on the tricky lines.
- A **risk table** (risk / likelihood / mitigation) — risks in a table get
  addressed; risks in paragraphs disappear.
- A short **"what we're explicitly not doing"** section. It stops scope creep
  before it starts.

## Sketch — three approaches

```html
<main>
  <header>
    <h1>Three ways to paginate /items</h1>
    <p>The prompt that produced this · the one I'd ship</p>
  </header>
  <section class="grid grid-cols-3">
    <article>
      <h2>01 · Offset / limit</h2>
      <p>Page by counting rows.</p>
      <pre><code>…query…</code></pre>
      <table class="pros-cons"><tr><th>Pro</th><th>Con</th></tr>
        <tr><td>Trivial to write</td><td>Drifts as rows shift</td></tr></table>
      <dl class="metrics"><dt>Deep-page cost</dt><dd>O(n)</dd><dt>Stable?</dt><dd>no</dd></dl>
    </article>
    <article>…02 · Cursor…</article>
    <article>…03 · Keyset…</article>
  </section>
  <footer><h2>Recommendation</h2><p>Go with 03 (keyset) — here's why…</p></footer>
</main>
```
