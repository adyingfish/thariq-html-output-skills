# Decks

> "A handful of `<section>` tags and twenty lines of JS is a slide deck. Point
> the agent at a Slack thread or a design doc and get something you can arrow-key
> through in a meeting — no Keynote, no export step." — Thariq

For short presentations someone will narrate to a room. If the content is dense
reference material the reader studies alone, a deck is the wrong lens — use
Research & Learning instead.

## Thariq's demo

- **Arrow-key slide deck** — "A short presentation as one HTML file. Left and
  right to navigate, no build step."

## Building one

- One `<section>` per slide. A presenter view that shows only the current slide,
  full-viewport — not a scroll.
- **Arrow keys** (`←`/`→`, optionally space) advance and reverse. A deck without
  keyboard nav is just a webpage with slides on it.
- A small slide counter in the corner (`4 / 12`). A "press F for fullscreen"
  hint or button — browser chrome distracts in a presentation.
- Default to 16:9 with letterboxing on other aspect ratios, so layout doesn't
  shift between slides.

## Per slide

- **One idea per slide.** If it has two, split it. Forced focus is the point.
- **Big type** — readable from the back of a room (32–48px body, larger titles).
- **Minimal words** — a slide is a visual aid for a speaker, not a document. A
  paragraph on the slide means the speaker competes with their own slide.
- Don't homogenize: one slide is a chart, the next a quote, the next a code
  block. Skip cute transitions — they distract and break on fast clicks. Make
  sure light-on-dark renders cleanly; most rooms project dark.

## Skeleton — the whole substrate

```html
<!doctype html><html lang="en"><head><meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1"><title>Deck</title>
<style>
  :root{color-scheme:dark}
  body{margin:0;height:100vh;display:grid;place-items:center;
       background:#0c0d10;color:#f3f3ee;font:clamp(20px,3vw,34px)/1.4 system-ui}
  .slide{display:none;max-width:24ch;text-align:center;padding:0 6vw}
  .slide[data-on]{display:block}
  .page{position:fixed;bottom:1rem;right:1.1rem;font:13px ui-monospace;opacity:.55}
</style></head><body>
  <div class="slide" data-on><h1>Shape over format</h1></div>
  <div class="slide"><h1>One artifact, many lenses</h1></div>
  <div class="slide"><h1>Trust the read</h1></div>
  <div class="page"></div>
  <script>
    const deck=[...document.querySelectorAll('.slide')], page=document.querySelector('.page');
    let at=0;
    const show=n=>{at=(n+deck.length)%deck.length;
      deck.forEach((s,k)=>k===at?s.setAttribute('data-on',''):s.removeAttribute('data-on'));
      page.textContent=(at+1)+' / '+deck.length;};
    onkeydown=e=>({ArrowRight:()=>show(at+1),' ':()=>show(at+1),
      ArrowLeft:()=>show(at-1),f:()=>document.documentElement.requestFullscreen()}[e.key]?.());
    show(0);
  </script>
</body></html>
```

Twenty lines of JS, no build step, opens directly in a browser.
