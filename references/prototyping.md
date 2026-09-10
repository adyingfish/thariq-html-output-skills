# Prototyping

> "Motion and interaction can't be described, only felt. A throwaway page with
> the real easing curve or the real click-through tells you in five seconds what
> a paragraph of prose never could." — Thariq

This is the lens where prose fails hardest. You can't write an easing curve; you
have to move it. Build the real thing, scoped to the one interaction in
question.

## Direct entry — closest original examples

| Example | When to use it | Dominant form | Key reader action |
|---|---|---|---|
| [Animation sandbox](original-examples/07-prototype-animation.html) · [live](https://thariqs.github.io/html-effectiveness/07-prototype-animation.html) | Dialling in a transition before wiring it into real code | The animated object front and centre; sliders for duration, easing, delay; live CSS output with a copy button | Try — drag a slider and watch the result; copy when it feels right |
| [Click-through flow](original-examples/08-prototype-interaction.html) · [live](https://thariqs.github.io/html-effectiveness/08-prototype-interaction.html) | Checking whether a multi-screen interaction feels correct before building | Four or so linked screens, enough fidelity to feel the flow, click targets that advance or go back | Follow + Try — tap through the interaction to judge whether it reads as intended |

The animation sandbox earns a live demo; the click-through earns linked screens. Use the simplest form that lets the reader *feel* the interaction, not describe it.

## Thariq's two demos

- **Animation sandbox** — "The transition in isolation with sliders for duration
  and easing, so you can tune it before wiring it in."
- **Clickable flow** — "Four screens linked together — enough fidelity to feel
  whether the interaction is right."

## Building an animation sandbox

- The thing being animated, in isolation, big and centered.
- A slider/toggle for every parameter that matters — duration, delay, easing,
  distance, color shift — updating live as the user drags.
- A **re-trigger / replay button**, so the user doesn't wait for a natural
  trigger. One-shot animations are useless for tuning.
- A **live code block** at the bottom showing the current parameters as CSS / JS
  / framer-motion config, updating with the sliders, plus a copy button. This is
  the whole reason the page exists — to tune values and paste them into the real
  codebase. Without the copy step it's just a demo.
- An easing-curve graph beats a dropdown of names; people tune curves visually.
- Stay scoped to the one transition the user asked about — not a generic
  "animation playground."

## Building a clickable flow

- 3–6 screens linked in their natural order. Real buttons: "next" advances,
  "back" goes back.
- A **screen-tray** thumbnail strip with the current screen highlighted, so the
  user can jump anywhere and compare screen 1 to screen 4 directly.
- Just enough fidelity to test the *shape* of the flow — render the fields the
  flow turns on, not every field. Pixel-perfection is a different artifact.

## Sketch — animation sandbox

```html
<main>
  <section class="stage"><div id="toast" class="toast">Saved</div></section>
  <aside class="controls">
    <label>Slide <input type="range" id="dist" min="0" max="80" value="24"><output>24px</output></label>
    <label>Duration <input type="range" id="dur" min="80" max="1200" value="320"><output>320ms</output></label>
    <label>Easing <select id="ease"><option>cubic-bezier(.2,.9,.3,1)</option><option>ease-out</option></select></label>
    <button id="play">▶ Replay</button>
  </aside>
  <pre id="out">/* the transform + transition, live as you drag */</pre>
  <button id="copy">Copy CSS</button>
</main>
```

---

## When to bring in the Unknowns gallery

If the work has unresolved preferences, assumptions, or knowledge gaps — pre-implementation options still open, a choice the user has not yet made, or a hypothesis that needs testing — consult [`unknowns.md`](unknowns.md) for an appropriate exploration, prototype, clarification, or understanding check before building the final artifact.