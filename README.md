# Flow X-Ray

**See where workflow time accumulated — and where work is sitting now.**

> Comprehensive process-mining suites — Celonis, SAP Signavio, UiPath Process Mining and friends — give you much more: event logs at scale, conformance checking, root-cause analysis, live dashboards. **Flow X-Ray is the sneak preview**: one file, one question — *where does the time go?* — answered in sixty seconds, offline, free, and ready to drop into a presentation. When the preview surprises you, that's when the big suites earn their licence.

Your approval process, drawn from its own data.

Upload a status log from any ticketing system — Jira, ServiceNow, SAP, Darwinbox, even a shared tracker — and get back a network diagram of how work actually flows: thick arrows where the volume goes, green where it moves, red where it stalls, and a count of what's *still parked* in each state right now.

One HTML file. No install. No server. **Nothing leaves your machine** — and you don't have to take our word for it: the file ships with a `Content-Security-Policy` of `default-src 'none'`, so the browser itself blocks every network request. Open DevTools → Network and watch nothing happen.

## The input

One row per status change. Three columns (names don't matter — you map them after upload):

| ticketId | status | statusUpdateTime |
|---|---|---|
| REQ-0041 | Submitted | 2026-03-02 09:14 |
| REQ-0041 | Manager Review | 2026-03-02 11:40 |
| REQ-0041 | Finance Review | 2026-03-04 16:02 |
| REQ-0041 | PO Issued | 2026-03-09 10:18 |

`.xlsx`, `.csv`, tab-separated, or paste from clipboard. A **Load sample data** button is built in if you just want to see it work.

## What it answers

- **Where does the time actually go?** Stalls are ranked by *total hours consumed* (tickets × wait), not by the rarest outlier — that's the recoverable pool.
- **What's stuck right now?** Completed hops only describe tickets that escaped. The in-flight panel counts tickets parked in each status *as of the newest timestamp in your file*, with the oldest age — so a queue silently filling up can't hide.
- **Is it an exception problem or a capacity problem?** Every hop shows p50 and p90. A 4h median with an 11-day p90 is a different fix than a 3-day median with a 4-day p90.
- **Which states are truly finished?** Terminal states are auto-guessed and shown as clickable chips — confirm or correct them, because a brand-new bottleneck that nothing has escaped yet must not be mistaken for “done.”
- **Which approvals were rubber stamps?** A state where every ticket exits the same way never changed an outcome — the readout flags 100% pass-through states (entry states excluded), and hovering any box shows its full exit split.
- **How much rework?** A ticket counts as reworked if it revisits any status it has already been through — measured per ticket, from the data, not from the layout.
- **Business hours or calendar hours?** Toggle 24×7 / Mon–Fri / Mon–Fri 9–18. A 60-hour weekend wait is one working day.

## Output

Drag the boxes to arrange the layout, pick dark or light canvas, The canvas has dark and light presets, plus **Match your deck** — pick any background colour and a full legible theme (node fills, label contrast, arrow palette) is derived from it automatically, so the export drops into your corporate template without looking pasted-in. Then **copy a PNG straight into your deck** (or download it). A **Copy findings** button produces three defensible one-liners — biggest time sink, slowest typical hop, current in-flight pressure — ready to paste under the diagram, with the data basis stated. Fonts are embedded, so the export looks identical everywhere.

## Defensible by default

Every run prints its own audit line: rows loaded, timestamps parsed, tickets detected, rows rejected, and the parsed date range with the time basis (24×7 by default; the Mon–Fri and 9–18 modes are opt-in and labelled in every export and findings block). p90 is suppressed below n=5.

## Honest limits

- Waits are attributed to the status the ticket was *sitting in* — the readout says so explicitly, so the next team in line doesn't get blamed for the previous queue.
- Ambiguous dates (both parts ≤ 12) default to day-first; a warning tells you, and a dropdown lets you switch to US-style month-first.
- Date-only exports make same-day waits invisible; the tool warns when it detects this.

## License

MIT. Use it, fork it, ship it inside your company.

---

Part of the **Hidden Mathematics of Work** series → [lionellmisquitta.com](https://lionellmisquitta.com) · more tools at [lionell6.gumroad.com](https://lionell6.gumroad.com)
