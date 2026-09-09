# Reports

> "Recurring documents — status updates, post-mortems — benefit most from a bit
> of structure and color. A small chart and a colored timeline turn something
> people skim into something they actually read." — Thariq

Recurring documents get read when they're scannable and ignored when they're
walls of text. Structure and color are what flip that.

## Direct entry — closest original examples

| Example | When to use it | Dominant form | Key reader action |
|---|---|---|---|
| [Weekly status](original-examples/11-status-report.html) · [live](https://thariqs.github.io/html-effectiveness/11-status-report.html) | Recurring team status that needs to be read in 90 seconds on Monday morning | Three visually distinct columns (shipped / in flight / blocked), one small chart, a separated "Asks" section | Locate — scan columns to find the status, spot the chart, act on the asks |
| [Incident timeline](original-examples/12-incident-report.html) · [live](https://thariqs.github.io/html-effectiveness/12-incident-report.html) | Post-mortem with a minute-by-minute sequence and follow-up commitments | Vertical timeline (timestamps one side, events other side) + log excerpts at relevant timestamps + action-item checklist | Track — follow the timeline to see pace and clusters, locate the root cause, commit on the action items |

Note: the post-mortem naturally composes with Research & Learning when the root cause needs real system explanation for an audience that was not watching the incident.

## Thariq's two demos

- **Weekly status** — "What shipped, what slipped, and a small chart — formatted
  for a quick skim on Monday morning."
- **Incident timeline** — "A post-mortem with a minute-by-minute timeline, log
  excerpts and the follow-up checklist."

## Building a status report

- Title with the week, team, author.
- Top section: **shipped / in flight / blocked**, in three visually distinct,
  color-coded columns or rows — distinguishable at a glance.
- One line per item with a link to the PR/ticket; a sentence of context only if
  it needs one. A status report is read in 90 seconds or not at all.
- A **small chart** somewhere — even a sparkline of PR throughput. A recurring
  report gets skimmed; a chart is where the eye lands.
- **"Asks"** — specific things the author needs from the reader, separated
  visually. They get lost when intermixed with status.

## Building an incident report / post-mortem

- Header: incident name, severity, total duration, customer impact in one
  concise summary. Leadership reads only this and the action items — don't bury
  the impact line.
- A **minute-by-minute timeline** as a vertical column, timestamps on one side,
  events on the other. This is the spine; render it as a real visual timeline,
  not a numbered list, so the reader sees the *pace* — long flat stretches, then
  clusters. Every event needs a clock.
- Log excerpts inline at the timestamps that matter, in `<pre>`, color-coded by
  source/severity.
- **Root cause** as its own section, for the audience that wasn't watching the
  timeline.
- **"What worked" alongside "what didn't"** — post-mortems turn punitive without
  the former and educational with it.
- Follow-up **action items as a checklist with owners and deadlines.** Without
  owners, follow-ups don't happen. These are commitments, not a wishlist.

Note: the post-mortem is the natural composite in this lens — its timeline is a
Report, but its root-cause section is really Research & Learning (explaining the
system to someone who wasn't there). Read that reference too when the cause needs
real explaining.
