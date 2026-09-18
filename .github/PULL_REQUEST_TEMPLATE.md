<!--
One decision per pull request. A balance change, a rendering change and a
translation pass are three pull requests — they fail for different reasons and
they get reverted for different reasons.

Full guidance: https://github.com/ParvaMachina/.github/blob/main/CONTRIBUTING.md
-->

## What this changes

<!-- One or two sentences. The diff already says what; say why. -->

## Why

<!--
Which decision does this serve? If it contradicts something recorded in .ssot/,
that document is updated in this same pull request — link both.
-->

Related decision: <!-- .ssot/ADR-0xx, PRD §x, or an issue number -->

## Measured values

<!--
Numbers that came out of a run go here as numbers, not as "done". Delete the
rows that do not apply; do not delete a row because you did not measure it.
-->

| Gate | Target | Measured |
| --- | --- | --- |
| Repository gate (`npm run ci` or lint / typecheck / test / build) | green | |
| Core coverage | per `.ssot/PLAN.md` | |
| Frame or tick budget | per `.ssot/PLAN.md` | |
| Bundle or atlas size | per `.ssot/PLAN.md` | |
| Balance harness | per `.ssot/PLAN.md` | |

## Invariants

<!-- These are enforced by lint and dependency audits; confirm you have not routed around one. -->

- [ ] **No network at runtime.** No `fetch`, no `XMLHttpRequest`, no dependency that calls out has entered a game manifest. Network code stays in `tools/`.
- [ ] **The rule core stays pure.** No new runtime dependency in `packages/core`; no `react` / `react-native` / `next` import; no `window`, `document` or `navigator`; no `Math.random`, `Date.now` or argument-less `new Date()`.
- [ ] **Nothing is collected.** No analytics, crash-reporting or remote-config package added anywhere.
- [ ] **Both languages.** Every new user-visible string exists in Turkish and English, through the typed `t()`.

## Deliberate changes that need saying out loud

<!-- Tick only what this pull request actually does, and justify each one in a line. -->

- [ ] Bumps `SAVE_SCHEMA_VERSION` — migration path:
- [ ] Changes a balance number — old → new, and the harness result:
- [ ] Adds or updates a dependency — which, and why nothing already present does the job:
- [ ] Changes a public URL, route or `/network.json` field — what else consumes it:
- [ ] Adds a generated asset — tool, prompt provenance, and size delta:

## Screenshots

<!-- Anything visual. Before and after, both orientations if it touches layout. -->

---

<!--
Commit messages: imperative, English, no trailers. No co-author lines, no tool
signatures, no generated-with attribution.
-->
