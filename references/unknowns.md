# Know Your Unknowns

> "The map is not the territory — the gap between them is your unknowns. Eleven
> self-contained `.html` artifacts for discovering them before, during, and
> after implementation." — Thariq, *Know your unknowns* gallery index

This is a cross-cutting reference. It does not replace the nine lenses — it
adds a second question to each of them: *what does the reader not yet know they
need to know, and can the artifact help them find out?*

Use it when there are unresolved preferences, assumptions, or knowledge gaps
that will affect the outcome. Skip it when the task is clear and the reader
already has everything they need.

## When to enter this reference

Enter when any of these apply:

- The reader hasn't seen the design space and can't express a preference until
  they have (pre-implementation: **explore**)
- A decision or interaction can only be judged by experiencing it, not
  describing it (pre-implementation: **prototype / try**)
- Important constraints or requirements are still vague or implicit
  (pre-implementation: **clarify**)
- The implementation diverged from the plan in ways that haven't been recorded
  (mid-implementation: **track deviation**)
- The reader needs to verify their own understanding of what was built before
  handing off or merging (post-implementation: **understanding check**)

Do not add an unknowns step to tasks that are already clear. Do not default to
running an interview or quiz before every implementation. Use answers already
given; avoid unnecessary gates.

## The three phases and their eleven examples

Thariq organises this gallery into three phases. The eleven examples below are
his, under his own titles; verbatim copies live in `original-examples/unknowns/`
(Apache-2.0 — see `source-and-examples.md`). The *Collaborative task* and
*Composes naturally with* columns are skill-layer summaries, not his wording;
his own one-line description of each sits in the gallery index and in the file.

### Pre-implementation · 8 examples

| # | Example (Thariq's title) | Collaborative task | Composes naturally with |
|---|---|---|---|
| 01 | [Blindspot pass](original-examples/unknowns/01-blindspot-pass.html) · [live](https://thariqs.github.io/html-effectiveness/unknowns/01-blindspot-pass.html) | Surface constraints the plan is missing | Code Review, Exploration |
| 02 | [Teach me my unknowns](original-examples/unknowns/02-color-grading-explainer.html) · [live](https://thariqs.github.io/html-effectiveness/unknowns/02-color-grading-explainer.html) | Learn the domain vocabulary needed to describe requirements precisely | Research & Learning, Prototyping |
| 03 | [Four design directions](original-examples/unknowns/03-design-directions.html) · [live](https://thariqs.github.io/html-effectiveness/unknowns/03-design-directions.html) | Identify preferences from rendered options | Exploration, Design, Editing |
| 04 | [Mock before you wire](original-examples/unknowns/04-toolbar-mock.html) · [live](https://thariqs.github.io/html-effectiveness/unknowns/04-toolbar-mock.html) | Experience the interaction before the real build | Prototyping, Design |
| 05 | [Brainstorm the intervention](original-examples/unknowns/05-churn-brainstorm.html) · [live](https://thariqs.github.io/html-effectiveness/unknowns/05-churn-brainstorm.html) | Choose and narrow an intervention direction | Exploration, Editing |
| 06 | [The interview](original-examples/unknowns/06-interview.html) · [live](https://thariqs.github.io/html-effectiveness/unknowns/06-interview.html) | Clarify a vague or contested decision | Exploration, Editing |
| 07 | [Point at a reference](original-examples/unknowns/07-reference-port.html) · [live](https://thariqs.github.io/html-effectiveness/unknowns/07-reference-port.html) | Verify semantic alignment with a reference implementation | Code Review, Research |
| 08 | [The tweakable plan](original-examples/unknowns/08-implementation-plan.html) · [live](https://thariqs.github.io/html-effectiveness/unknowns/08-implementation-plan.html) | Surface and prioritise choices still subject to change | Exploration, Editing |

### During implementation · 1 example

| # | Example (Thariq's title) | Collaborative task | Composes naturally with |
|---|---|---|---|
| 09 | [Implementation notes](original-examples/unknowns/09-implementation-notes.html) · [live](https://thariqs.github.io/html-effectiveness/unknowns/09-implementation-notes.html) | Record where the plan and reality diverged | Reports, Code Review |

### Post-implementation · 2 examples

| # | Example (Thariq's title) | Collaborative task | Composes naturally with |
|---|---|---|---|
| 10 | [The buy-in doc](original-examples/unknowns/10-pitch-doc.html) · [live](https://thariqs.github.io/html-effectiveness/unknowns/10-pitch-doc.html) | Help reviewers understand and judge the work | Reports, Decks, Prototyping |
| 11 | [Quiz me before I merge](original-examples/unknowns/11-change-quiz.html) · [live](https://thariqs.github.io/html-effectiveness/unknowns/11-change-quiz.html) | Verify your own understanding of what changed | Code Review, Research |

## What the artifact owes the reader in each phase

**Pre-implementation — make the unknown judgeable.** Put the thing to judge at
the centre of the page. If the reader is choosing between design directions,
render all four, not a description of them. If they are clarifying requirements,
make the ambiguity visible and the choices explicit. Preserve the distinction
between assumptions, observations, and the reader's own decisions; do not
present inferences as confirmed facts.

**Mid-implementation — make the deviation legible.** Record what was planned,
what was actually found or built, what decision was made as a result, and what
remains open. Keep the distinction between a decided item and an undecided one
clearly visible. Export should carry the deviation record, not just the final
state.

**Post-implementation — make the understanding checkable.** Locate any
misunderstanding against specific evidence or explanation. Give the reader
something to push back on, not a summary to agree with. Feedback should be
portable — the reader should be able to carry the result of the check into the
next step.

## Three decisions for each unknowns use

**Identify.** Which kind of uncertainty is actually affecting this task?
- Use information already provided; do not re-collect answers you have.
- Only when something is still unresolved and genuinely affects the outcome
  should you consider exploring, prototyping, interviewing, or explaining.

**Surface.** What presentation makes the uncertain thing judgeable?
- Read the relevant phase examples to find the closest original.
- Put the thing to judge in the dominant position on the page; explanation,
  history, and context go in a sidebar, annotation, or on-demand expansion.

**Carry forward.** What does this interaction leave behind?
- Offer an export of preferences, decisions, open questions, deviation evidence,
  or understanding-check results so the next step gets new information.
- Selecting a button is not the same as resolving the risk; say what it means.
- Original answers, choices, and annotations should be recoverable as plain text.

## Boundary notes

Enter this reference only when collaboration is genuinely needed to discover or
clarify something. A clear task with a clear answer should be executed directly.

- Do not default to running an interview first.
- Do not run a knowledge quiz unless the user's task calls for one.
- Do not require all projects to pass through all three phases.

Treat individual decisions, conservative defaults, and sign-off requirements in
the original examples as context-specific behaviour, not general permission rules
for the skill.
