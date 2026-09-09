# Code Review & Understanding

> "Diffs and call-graphs are spatial information; markdown flattens them. Let
> the agent render the change as an annotated diff, draw the module as boxes and
> arrows, or write the PR description your reviewers actually want — so the shape
> of the code is visible at a glance." — Thariq

Render the code the way it wants to be read, not as a wall of `<pre>` with
prose between every chunk.

## Direct entry — closest original examples

| Example | When to use it | Dominant form | Key reader action |
|---|---|---|---|
| [Annotated pull request](original-examples/03-code-review-pr.html) · [live](https://thariqs.github.io/html-effectiveness/03-code-review-pr.html) | Reviewing a diff where specific lines need commentary | Styled diff with margin notes, severity tags, jump links | Locate — find the annotated regions, read commentary beside the code |
| [PR writeup for reviewers](original-examples/17-pr-writeup.html) · [live](https://thariqs.github.io/html-effectiveness/17-pr-writeup.html) | Writing the author-side description of a change | Motivation → before/after → file-by-file tour → focus section | Follow — step through the change in the author's intended order |
| [Module map](original-examples/04-code-understanding.html) · [live](https://thariqs.github.io/html-effectiveness/04-code-understanding.html) | Orienting a reader to an unfamiliar package | Boxes-and-arrows SVG + hot path highlight + per-module cards | Locate — start at the entry point for your use case, navigate to detail |

Inspect the spatial relationships and information hierarchy of the closest example; design around your current material rather than copying its shell.

## Thariq's three demos

- **Annotated pull request** — "A diff rendered with margin notes, severity tags
  and jump links — easier to scan than scrolling a terminal."
- **PR writeup for reviewers** — "The author's side: motivation, before/after, a
  file-by-file tour with the *why*, and where to focus the review."
- **Module map** — "An unfamiliar package drawn as boxes and arrows, with the
  hot path highlighted and entry points listed."

## Building an annotated diff

- The diff is the **spine**. Style `+`/`−` lines, add syntax highlighting, and
  pin **margin annotations** — small numbered notes beside specific lines.
  Interleaved comments break the visual flow; margin notes preserve the code as
  code *and* attach the commentary.
- Inline severity tags, color-coded: `🟥 blocking`, `🟨 nit`, `🟦 question`,
  `🟩 praise`. Reviewers scan for red first — help them.
- Jump links at the top to the annotated regions; collapsible file sections once
  the diff crosses ~3 files.
- Say **where to focus the review.** Reviewers don't have time for everything.

## Building a PR writeup

- Imperative title. 2–3 sentences of motivation.
- **Before/after as a real side-by-side**, if anything visual changed — not
  "before: X, after: Y" prose.
- A file-by-file tour grouped by *theme* ("plumbing" / "core logic" / "tests"),
  one or two sentences of *why* each — the shape of the change, not every line.
- "Where to focus" + risks + how it was tested.

## Building a module map

- A one-sentence summary of what the package does, then a **boxes-and-arrows
  diagram** (inline SVG) of the modules and their calls. (This reaches into
  Illustrations — read that reference for SVG craft.)
- Highlight the **hot path** — the common call sequence — in a distinct color.
- Call out entry points by use case: "If you're trying to do X, start at Y."
- Per-module cards under the diagram; a "data lifecycle" trace of one real input
  flowing through. Show structural relationships, not every textual reference —
  drawing every edge makes a hairball.

## Sketch — annotated diff

```html
<main class="diff-view">
  <header>
    <h1>Add keyset pagination to GET /items</h1>
    <p>3 files · +94 −12</p>
    <nav class="jump-links"><a href="#ann-1">🟥 #1 unbounded scan</a></nav>
  </header>
  <section class="file">
    <h2>src/items/list.ts</h2>
    <div class="diff">
      <div class="line ctx">  const rows = await db.items</div>
      <div class="line add" data-annotation="1">+   .where('id', '>', cursor).all();</div>
      <div class="line add">+   return rows.slice(0, limit);</div>
    </div>
    <aside class="annotation" id="ann-1">
      <span class="severity blocking">🟥 blocking</span>
      <p>This pulls every row past the cursor, then slices in memory. Push
         <code>limit</code> into the query or the page size buys nothing.</p>
    </aside>
  </section>
</main>
```
