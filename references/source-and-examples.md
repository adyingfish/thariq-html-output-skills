# Sources and Examples Index

This file records three things: where the skill's claims come from, an index of
the 31 original examples the skill snapshots, and the provenance of that snapshot.

---

## Attribution map

The skill draws on three distinct sources. They are not interchangeable.

| Source | Role | Cite as |
|---|---|---|
| Thariq Shihipar, [*Using Claude Code: The unreasonable effectiveness of HTML*](https://claude.com/blog/using-claude-code-the-unreasonable-effectiveness-of-html) | **Normative basis** — the nine categories and their demo descriptions, the "skim it vs. actually read it" framing, single-file self-containment, "always end with an export button" | "the article", "Thariq's post" |
| The [example gallery](https://thariqs.github.io/html-effectiveness/) — repo [ThariqS/html-effectiveness](https://github.com/ThariqS/html-effectiveness) | **Presentational evidence** — 20 gallery examples plus the 11 under *Know your unknowns*; what each category looks like when built | "original example", the file name |
| Skill layer — `SKILL.md`, `references/*.md` | **Practical extension** — recognition test, composition model, three obligations, reader-action table, implicit trigger rules, self-check, Direct-entry tables, the Unknowns cross-reference | "skill-layer guidance", "this reference" |

Anything described as Thariq's should trace to the article or the gallery.
Skill-layer additions are labelled as such wherever they appear. Where they
conflict, the article wins.

---

## Main gallery · 20 examples

Order and titles follow the gallery's `index.html`. File numbers are Thariq's
and do not follow category order. Local copies are verbatim.

| File | Thariq's title | Lens | Local | Live |
|---|---|---|---|---|
| `01-exploration-code-approaches.html` | Three code approaches | Exploration & Planning | [open](original-examples/01-exploration-code-approaches.html) | [live](https://thariqs.github.io/html-effectiveness/01-exploration-code-approaches.html) |
| `02-exploration-visual-designs.html` | Visual design directions | Exploration & Planning | [open](original-examples/02-exploration-visual-designs.html) | [live](https://thariqs.github.io/html-effectiveness/02-exploration-visual-designs.html) |
| `16-implementation-plan.html` | Implementation plan | Exploration & Planning | [open](original-examples/16-implementation-plan.html) | [live](https://thariqs.github.io/html-effectiveness/16-implementation-plan.html) |
| `03-code-review-pr.html` | Annotated pull request | Code Review & Understanding | [open](original-examples/03-code-review-pr.html) | [live](https://thariqs.github.io/html-effectiveness/03-code-review-pr.html) |
| `17-pr-writeup.html` | PR writeup for reviewers | Code Review & Understanding | [open](original-examples/17-pr-writeup.html) | [live](https://thariqs.github.io/html-effectiveness/17-pr-writeup.html) |
| `04-code-understanding.html` | Module map | Code Review & Understanding | [open](original-examples/04-code-understanding.html) | [live](https://thariqs.github.io/html-effectiveness/04-code-understanding.html) |
| `05-design-system.html` | Living design system | Design | [open](original-examples/05-design-system.html) | [live](https://thariqs.github.io/html-effectiveness/05-design-system.html) |
| `06-component-variants.html` | Component variants | Design | [open](original-examples/06-component-variants.html) | [live](https://thariqs.github.io/html-effectiveness/06-component-variants.html) |
| `07-prototype-animation.html` | Animation sandbox | Prototyping | [open](original-examples/07-prototype-animation.html) | [live](https://thariqs.github.io/html-effectiveness/07-prototype-animation.html) |
| `08-prototype-interaction.html` | Clickable flow | Prototyping | [open](original-examples/08-prototype-interaction.html) | [live](https://thariqs.github.io/html-effectiveness/08-prototype-interaction.html) |
| `10-svg-illustrations.html` | SVG figure sheet | Illustrations & Diagrams | [open](original-examples/10-svg-illustrations.html) | [live](https://thariqs.github.io/html-effectiveness/10-svg-illustrations.html) |
| `13-flowchart-diagram.html` | Annotated flowchart | Illustrations & Diagrams | [open](original-examples/13-flowchart-diagram.html) | [live](https://thariqs.github.io/html-effectiveness/13-flowchart-diagram.html) |
| `09-slide-deck.html` | Arrow-key slide deck | Decks | [open](original-examples/09-slide-deck.html) | [live](https://thariqs.github.io/html-effectiveness/09-slide-deck.html) |
| `14-research-feature-explainer.html` | How a feature works | Research & Learning | [open](original-examples/14-research-feature-explainer.html) | [live](https://thariqs.github.io/html-effectiveness/14-research-feature-explainer.html) |
| `15-research-concept-explainer.html` | Concept explainer | Research & Learning | [open](original-examples/15-research-concept-explainer.html) | [live](https://thariqs.github.io/html-effectiveness/15-research-concept-explainer.html) |
| `11-status-report.html` | Weekly status | Reports | [open](original-examples/11-status-report.html) | [live](https://thariqs.github.io/html-effectiveness/11-status-report.html) |
| `12-incident-report.html` | Incident timeline | Reports | [open](original-examples/12-incident-report.html) | [live](https://thariqs.github.io/html-effectiveness/12-incident-report.html) |
| `18-editor-triage-board.html` | Ticket triage board | Custom Editing Interfaces | [open](original-examples/18-editor-triage-board.html) | [live](https://thariqs.github.io/html-effectiveness/18-editor-triage-board.html) |
| `19-editor-feature-flags.html` | Feature flag editor | Custom Editing Interfaces | [open](original-examples/19-editor-feature-flags.html) | [live](https://thariqs.github.io/html-effectiveness/19-editor-feature-flags.html) |
| `20-editor-prompt-tuner.html` | Prompt tuner | Custom Editing Interfaces | [open](original-examples/20-editor-prompt-tuner.html) | [live](https://thariqs.github.io/html-effectiveness/20-editor-prompt-tuner.html) |

---

## *Know your unknowns* · 11 examples

> "The map is not the territory — the gap between them is your unknowns. Eleven
> self-contained `.html` artifacts for discovering them before, during, and
> after implementation." — gallery index, `unknowns/index.html`

Entry conditions and phase guidance are in `unknowns.md`.

| File | Thariq's title | Phase | Local | Live |
|---|---|---|---|---|
| `unknowns/01-blindspot-pass.html` | Blindspot pass | Pre | [open](original-examples/unknowns/01-blindspot-pass.html) | [live](https://thariqs.github.io/html-effectiveness/unknowns/01-blindspot-pass.html) |
| `unknowns/02-color-grading-explainer.html` | Teach me my unknowns | Pre | [open](original-examples/unknowns/02-color-grading-explainer.html) | [live](https://thariqs.github.io/html-effectiveness/unknowns/02-color-grading-explainer.html) |
| `unknowns/03-design-directions.html` | Four design directions | Pre | [open](original-examples/unknowns/03-design-directions.html) | [live](https://thariqs.github.io/html-effectiveness/unknowns/03-design-directions.html) |
| `unknowns/04-toolbar-mock.html` | Mock before you wire | Pre | [open](original-examples/unknowns/04-toolbar-mock.html) | [live](https://thariqs.github.io/html-effectiveness/unknowns/04-toolbar-mock.html) |
| `unknowns/05-churn-brainstorm.html` | Brainstorm the intervention | Pre | [open](original-examples/unknowns/05-churn-brainstorm.html) | [live](https://thariqs.github.io/html-effectiveness/unknowns/05-churn-brainstorm.html) |
| `unknowns/06-interview.html` | The interview | Pre | [open](original-examples/unknowns/06-interview.html) | [live](https://thariqs.github.io/html-effectiveness/unknowns/06-interview.html) |
| `unknowns/07-reference-port.html` | Point at a reference | Pre | [open](original-examples/unknowns/07-reference-port.html) | [live](https://thariqs.github.io/html-effectiveness/unknowns/07-reference-port.html) |
| `unknowns/08-implementation-plan.html` | The tweakable plan | Pre | [open](original-examples/unknowns/08-implementation-plan.html) | [live](https://thariqs.github.io/html-effectiveness/unknowns/08-implementation-plan.html) |
| `unknowns/09-implementation-notes.html` | Implementation notes | During | [open](original-examples/unknowns/09-implementation-notes.html) | [live](https://thariqs.github.io/html-effectiveness/unknowns/09-implementation-notes.html) |
| `unknowns/10-pitch-doc.html` | The buy-in doc | Post | [open](original-examples/unknowns/10-pitch-doc.html) | [live](https://thariqs.github.io/html-effectiveness/unknowns/10-pitch-doc.html) |
| `unknowns/11-change-quiz.html` | Quiz me before I merge | Post | [open](original-examples/unknowns/11-change-quiz.html) | [live](https://thariqs.github.io/html-effectiveness/unknowns/11-change-quiz.html) |

---

## Snapshot provenance

| Field | Value |
|---|---|
| Upstream repository | [https://github.com/ThariqS/html-effectiveness](https://github.com/ThariqS/html-effectiveness) |
| Upstream commit | `1787245d94aa680edf18b52027e3f859032776ba` (2026-07-03, "Merge branch 'add-project-docs'") |
| Snapshot taken | 2026-09-09 |
| Fetch method | `https://raw.githubusercontent.com/ThariqS/html-effectiveness/1787245d94aa680edf18b52027e3f859032776ba/<path>` |
| Local location | `references/original-examples/` — 20 files at top level, 11 under `unknowns/`, plus `LICENSE` |
| License | Apache License 2.0 (`LICENSE` copied alongside). Every file's first line carries `Copyright 2026 Anthropic PBC · SPDX-License-Identifier: Apache-2.0`; those headers are preserved. Upstream has no `NOTICE` file. |
| Upstream status | README states: "Sample code. Not maintained and not accepting contributions." |
| Skill baseline before this change | `f8a251e270c0a25ceb9f2a0a449599fc5dbb42ad` |

### Manifest

Verify with:

```
cd references/original-examples && sha256sum -c <(grep -E '^[0-9a-f]{64}' ../source-and-examples.md | awk '{print $1"  "$3}')
```

```
af7d5651f1dedec3ad8bd724e2f0bc92725dbde74518963e774f464996c80af4   14570  01-exploration-code-approaches.html
5c50ddb8415dbde8248cb97fab1e8cbbfabb35f2ad3718bc3c313b319dee4227   14045  02-exploration-visual-designs.html
73e5c5cea0811576288f20765b9ec565c0ec0be7d026f760da4cba3f9462de5d   28712  16-implementation-plan.html
c14a52aa31b3bd207b52490c7e967bf68ae1c3920199753ad189c1e35af8f23a   26306  03-code-review-pr.html
96c12f9545160cc1b5e5a38b53c32c443fcc304b49f56ccb26438d5094795b9b   24540  17-pr-writeup.html
b7c9a751c9170e34307a3fe15d0ed0e61a76bcccef3de355a167d910778f4157   17966  04-code-understanding.html
5f497b1667ddad12822a60906c3d57db98439b0540278431b3cc54201bb07903   18169  05-design-system.html
dfc4783665998544c0883be3e12f8bcd45400e177acc0c90f76c998f51df31a7   16665  06-component-variants.html
07e908d47a14297e0feb8fb589d9102c5d8231792c95c08af3211c029fb904e1   12517  07-prototype-animation.html
5e13db1460f9258a971b60339c2994140ece350c419b73d81d1fe83b591db51f   10880  08-prototype-interaction.html
33de35f9d5a6d1c4a412fbfafaef88595771aad03bb2f69d90ee4834239dde4a   18426  10-svg-illustrations.html
86f9ff01431897849ae6fe12693864fbdf6c43eb271977eca416e071dc324ccf   15355  13-flowchart-diagram.html
1fa94d65c9aa8524bf7b562eaa9666900b317661e650fae1c223e3e30441c971   16604  09-slide-deck.html
79a6bfc0d3836898ffc0f39cefa11eab19e9a2e4fade708a81ac1d0f6a5612bb   12407  14-research-feature-explainer.html
1563ed1140ce0a04bc506758d378dc809c871c3112690cc654d34c1cc98e6c62   13635  15-research-concept-explainer.html
66f6eefaa632fbdb8dd9a96b588a5cf864d85ba188eb7dd1ed6edfbb25c20a09   16459  11-status-report.html
f90ef9c3910803a3df2d75cc7fcd83d1f72b6c4494781fd239965c54e7efe2f6   15568  12-incident-report.html
99d4f0832580e01a12872bb1abe18048180d1c6f158fc3613634e96306b1a723   18654  18-editor-triage-board.html
9915ba51040854a4a50112016ced9b1f9ace831621d69802b70e07f9f756c180   18985  19-editor-feature-flags.html
a5663f4d361be2e2cadfd94e8f153d7b7484510a862a654106fb553c714baeae   21252  20-editor-prompt-tuner.html
214806f52972292b222bcbd0fe7731b9ebae935cfeb2d34a2eac00828ea420c8   27389  unknowns/01-blindspot-pass.html
ef19bf9eb94b54d7d2ac5633988d4e37ae19beafa0aee6404831bf26667ba622   27895  unknowns/02-color-grading-explainer.html
1df7db424472ca796492b3226cda6c968792c8d53b727f54774a0a01c6765c01   41116  unknowns/03-design-directions.html
f7cd46eaed3191d91a7d5304c5b6130157c607ccc4d9a7546ff3dbb7b6b9a9d7   35478  unknowns/04-toolbar-mock.html
b6d291b2ee25ebadc1a424ae505f0bf444db26ca594702a72d299b7f182bd7db   29987  unknowns/05-churn-brainstorm.html
7dbcf9fb911fdeb550088e6ee2ade522f516c04b4213f7921d1571cc619f539c   27269  unknowns/06-interview.html
6148bca49c8e0d90b253673810c36085750a96bcdee92bb315cb23af85e358b5   36665  unknowns/07-reference-port.html
af42486265c813000da5607392fd57da7c6b5a6da1a5e5679906670a82473563   36988  unknowns/08-implementation-plan.html
29ec0592a619fb7c2d4f3b141b933dbf2f8a8492550e013e0755e309f8634894   26697  unknowns/09-implementation-notes.html
aa20fd57f94e7306af37650db85604c43072687002dde0ac5fb5849c87c632f1   30094  unknowns/10-pitch-doc.html
bedc5600b31030ec4a1fe53545ee214c9bee5ac935def4af9bf636934f3407dd   32621  unknowns/11-change-quiz.html
30deeaa611125310673e7c14b4892fb102fb56697ecfab3b49b77ca0190de7e1   11343  LICENSE
```
