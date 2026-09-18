# Support

Something in a Parva Machina game is broken, unfair, unclear or badly
translated. Here is where it goes.

## Write to us

**<contact@parvamachina.com>**

There is no contact form, no forum and no Discord. A form needs a server and the
games do not have one; a community platform needs moderation time that a
one-person studio does not have. Email is read.

You do not need a GitHub account, and you do not need access to a game
repository — most of them are private.

## Before you write

The games take no telemetry, so nothing about your session reached us. Whatever
you can tell us is all we will ever have. In rough order of usefulness:

1. **Which game**, and whether it was the web version or the mobile one.
2. **What you expected, and what happened instead.** One sentence each is fine.
3. **Where.** A level number, map name, wave, turn number, incident name — these
   are stable identifiers and they let us reproduce the state you were in.
4. **A seed or a save**, if the game shows one. Regnarium and Umbraward both
   expose a seed; SysAdmin Crisis and Regnarium can export their save as JSON
   from the settings screen. A seed usually reproduces a balance problem
   exactly.
5. **Browser and device**, for a web bug. "Safari on an iPhone 13" is enough.
6. **A screenshot or a short recording**, for anything visual.

## What happens next

The studio is one person, so there is no support rota and no promised response
time. What there is:

- Every email gets read.
- A reproducible bug gets an entry in the game's own tracker and a fix in a
  release.
- A balance complaint with a seed attached is worth more than ten without one,
  because it can be replayed against the balance harness.
- A translation fix lands in the next build; both Turkish and English are
  maintained as originals, so a correction to either is welcome.

Feedback is the only signal this studio has. There is no analytics dashboard
deciding what gets built next — writing in is what actually changes a game.

## Security

A security issue goes to the same address, but with `[security]` at the start of
the subject line and no public issue anywhere first. Follow
[SECURITY.md](SECURITY.md).

## The things that will not change

Some reports arrive regularly and the answer is always the same. These are
architectural decisions, recorded in each repository's `.ssot/` directory, not
open questions:

- **There is no cloud save, and there will not be one.** Saves live in your
  browser's own storage because there is no server. Use the game's export button
  before clearing site data or switching devices.
- **There are no accounts, leaderboards or multiplayer.** All three need a
  server.
- **There is no in-game purchase to restore.** The games are free and sell
  nothing.
- **Clearing your browser's site data erases your progress.** This is the same
  storage; nothing is held elsewhere that could restore it.
