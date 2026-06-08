# Design

> "HTML *is* the medium your design system ships in, so it's the natural format
> for talking about it. Tokens become swatches, components become contact
> sheets, and the artifact can be fed straight back into the next prompt." —
> Thariq

The honest format for talking about design is the medium design ships in. Render
the thing as itself, never as a screenshot or a description of it.

## Thariq's two demos

- **Living design system** — "Colors, type scale and spacing tokens pulled from
  a repo and rendered as swatches you can copy from."
- **Component variants** — "Every size, state and intent of one component laid
  out on a single sheet for review."

## Building a living design system

- A section per token category: color, type, spacing, radii, shadows, motion.
- **Render each token as itself**: colors as swatches, type as real text at the
  real scale, spacing as visible labelled gaps, shadows on a card. `#5B6CFF`
  next to its swatch beats `#5B6CFF` alone every time.
- A **copy button** on every swatch/specimen — the value on click, the token
  name (`--color-accent-500`) on shift-click, or two buttons. The artifact is
  half reference, half tool; the copy action is the point, and it's what lets
  the artifact feed "straight back into the next prompt."
- **Pull from the codebase** if there is one — read the Tailwind config / theme
  file / CSS variables rather than inventing plausible-looking tokens. Fidelity
  to the source of truth is everything; a divergent system is worse than none.

## Building a component contact sheet

- One component, every state on a single page: sizes × intents × states (hover,
  focus, disabled, loading, error). Group by axis — a row per size, a column per
  intent.
- Render the **real** component (or the closest HTML/CSS approximation), with the
  props that produced each variant underneath it.
- Don't skip the "weird" states (loading, empty, error) — those are exactly what
  design systems forget to specify and engineering ad-libs.
- One component per sheet. Multi-component pages turn into a tour, which is a
  different artifact.

## Reuse across artifacts

A design-system artifact is worth saving (`design-system.html`) and feeding into
every later artifact as the source of CSS variables. It's one-time work that
keeps everything after it on-brand. Suggest it the first time a project with a
real visual identity asks for HTML output.
