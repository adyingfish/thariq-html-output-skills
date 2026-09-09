# Custom Editing Interfaces

> "Sometimes it's hard to describe what you want in a text box. Ask for a
> throwaway editor for the exact thing you're working on — and always end with
> an export button that turns whatever you did in the UI back into something you
> can paste into the agent or commit. You stay in the loop; the loop gets
> tighter." — Thariq

The most distinctive use of the format. A text box is the wrong shape for some
tasks — triaging 30 tickets, tuning a regex, reordering a flow. Build a
single-file editor purpose-built for the one task.

## Direct entry — closest original examples

| Example | When to use it | Dominant form | Key reader action |
|---|---|---|---|
| [Ticket triage board](original-examples/18-editor-triage-board.html) · [live](https://thariqs.github.io/html-effectiveness/18-editor-triage-board.html) | Sorting a batch of tickets into priority buckets | Four columns (Now / Next / Later / Cut) with drag-and-drop, tally per bucket, "Copy as markdown" export | Adjust — drag until the cut feels right, copy the ordering out |
| [Feature flag editor](original-examples/19-editor-feature-flags.html) · [live](https://thariqs.github.io/html-effectiveness/19-editor-feature-flags.html) | Editing a set of feature toggles where some have dependencies | Grouped toggles with dependency warnings, "copy diff" for changed keys only | Adjust — toggle, watch the warnings, export only the delta |
| [Prompt tuner](original-examples/20-editor-prompt-tuner.html) · [live](https://thariqs.github.io/html-effectiveness/20-editor-prompt-tuner.html) | Iterating on a prompt template against multiple sample inputs | Editable template left, three live previews right re-rendering as you type | Try + Adjust — edit the template and watch all three samples update in real time |

The non-negotiable export is what distinguishes an editor from a toy. Add the export *before* any other feature.

## The non-negotiable rule

**Every editor ends with an export.** "Copy as markdown / JSON / prompt,"
"download as CSV" — whatever turns the UI state into something pasteable back
into the agent, a commit, or the next prompt. This is Thariq's "you stay in the
loop." Without the export, the editor is a toy; with it, it closes the loop. If
you find yourself building one without an export path, add the export *first*.

## Thariq's three demos

- **Ticket triage board** — "Drag thirty tickets across Now / Next / Later / Cut,
  then copy the final ordering out as markdown."
- **Feature flag editor** — "Toggles grouped by area, dependency warnings when a
  prerequisite is off, and a 'copy diff' button for just the changed keys."
- **Prompt tuner** — "Editable template on the left with variable slots
  highlighted; three sample inputs on the right re-render live as you type."

## Building one

- The **work area is the dominant focus**; header, controls, and export sit
  around it. A one-sentence header on what this editor is for.
- **Pre-fill the data.** The user already gave it to you in the prompt — don't
  make them type it twice. Build the triage board for *these* thirty real
  tickets, not a generic "task manager."
- Interaction primitives matched to the data: drag-and-drop for ordering,
  toggles for booleans, selects for enums, sliders for ranges.
- A live **current-state readout** — counts per bucket, char count, validation
  errors visible immediately. Show constraint conflicts *at the moment they
  happen*, not as a footer disclaimer.
- **Keyboard support** for repetitive actions — `j`/`k` or `1`/`2`/`3` when the
  user is about to label 100 things, not just clicks.
- State persistence within the session (agents without a filesystem: in-memory
  only; agents writing local files: `localStorage` is fine and worth it).
- No settings, no backend, no auth. It's a tool, not a product. Judged by whether
  the user can finish and leave — make it fast and direct.

## Sketch — triage board

```html
<main>
  <header><h1>Triage board</h1>
    <p>Thirty tickets, pre-sorted into a first guess. Drag until the cut feels
       right, then copy the board out as markdown.</p></header>
  <div class="board">
    <section data-bucket="now"><h2>Now</h2><ul></ul></section>
    <section data-bucket="next"><h2>Next</h2><ul></ul></section>
    <section data-bucket="later"><h2>Later</h2><ul></ul></section>
    <section data-bucket="cut"><h2>Cut</h2><ul></ul></section>
  </div>
  <footer>
    <span id="tally"></span>
    <button id="reset">Reset</button>
    <button id="export">Copy as markdown</button>
  </footer>
  <script>
    const tickets = [/* the thirty, pre-filled from the prompt */];
    /* render into buckets · HTML5 drag-and-drop · state in a Map<id,bucket> */
    /* export → one ## heading per bucket, one line per ticket */
  </script>
</main>
```
