# Contributing

Parva Machina is a one-person studio and the game repositories are private, so
contributing here does not usually mean a pull request. It means telling us
something we could not have found on our own.

That is not a polite formulation. The games collect no telemetry at all — no
analytics, no crash reports, not even an anonymised counter. Every single thing
we know about how a game behaves outside this machine arrived because somebody
wrote in.

## The most useful things you can send

**A reproducible bug.** Which game, web or mobile, what you expected, what
happened, and where — a level number, map name, wave, turn, incident name. Those
identifiers are stable and let us reach the exact state you were in.

**A balance complaint with a seed.** Regnarium and Umbraward both expose a seed;
SysAdmin Crisis and Regnarium export a save as JSON. With a seed we can replay
your run against the balance harness. Without one we are guessing at a feeling.
One seeded report is worth ten unseeded ones.

**A translation fix.** Turkish and English are both maintained as originals,
not as a translation of the other. A wrong term, an awkward line or a string that
does not fit its button is a real defect in either language, and it lands in the
next build.

**An accessibility problem.** Colour contrast, hit target size, text that cannot
be resized, motion that cannot be turned off, a screen that fights a screen
reader, a mechanic that assumes a fast hand. These are the reports we are least
able to discover ourselves.

## Where to send it

- **[Open an issue](https://github.com/ParvaMachina/.github/issues/new/choose)**
  in this repository if you have a GitHub account. The forms ask for exactly the
  fields above, and the issue is public.
- **<contact@parvamachina.com>** if you do not, or if you would rather it were
  not public. Same reader, same tracker.
- **Security issues go neither place.** Read [SECURITY.md](SECURITY.md) first.

See [SUPPORT.md](SUPPORT.md) for what happens after you send it.

## If you do have write access to a game repository

Every repository carries the rules that matter in its own `.ssot/` directory, and
some also keep a short `CLAUDE.md` for agents working in them. Read the
`.ssot/ADR` entries before the code — they are why the code looks the way it
does. What follows is only what is true across all of them.

### The order of operations

**Decision first, code second.** When code and a `.ssot/` document disagree, the
document is right until someone decides otherwise — and then both change, in that
order, in the same change set. A pull request that quietly makes the code differ
from a recorded decision will be sent back even if the code is better.

### Four invariants, enforced by the build

These are not style preferences. Each is an architecture decision record, and
each is checked by a lint rule or a dependency audit that fails the build:

1. **No network at runtime.** After the first load, a game makes no request.
   `fetch` and `XMLHttpRequest` are forbidden in game code; a dependency that
   calls out cannot enter a game manifest. Network access lives in `tools/` —
   build-time only — and nowhere else.
2. **The rule core is pure.** `packages/core` has zero runtime dependencies and
   may not import `react`, `react-native` or `next`, may not touch `window`,
   `document` or `navigator`, and may not call `Math.random`, `Date.now` or
   `new Date()` with no argument. Randomness is seeded and time is passed in;
   this is what makes a replay reproduce and a bug report reach us intact.
3. **Nothing is collected.** No analytics, crash-reporting or remote-config
   package may appear in any game package's manifest, imported or not.
4. **Both languages, always.** A user-visible string is added to Turkish and
   English in the same change, through the typed `t()`. A completeness test
   fails the build on a missing key in either.

### Before you open a pull request

Run the repository's own gate. It differs per project — `npm run ci` in
Umbraward, the `lint` / `typecheck` / `test` / `build` chain elsewhere — and the
repository README names it. Green locally, not "green in CI eventually."

Numbers that came out of a measurement go in the pull request body as measured
values, not as "done". Coverage thresholds, frame budgets, bundle sizes and
balance gates all have targets recorded in `.ssot/PLAN.md`; state what you got.

### Change scope

One decision per pull request. A balance change, a rendering change and a
translation pass are three pull requests, because they fail for different
reasons and get reverted for different reasons.

Do not bump a save schema version, change a balance number, or add a dependency
as a side effect of something else. Each of those is the subject of its own
change, with its own justification.

## Commit messages

Imperative mood, English, one line under about 72 characters, then a blank line
and prose explaining **why** — the what is already in the diff.

No trailers. No co-author lines, no tool signatures, no generated-with
attribution, no session links. The message ends with the last sentence of its
own prose.
