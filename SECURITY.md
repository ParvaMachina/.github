# Security Policy

## Reporting a vulnerability

**<contact@parvamachina.com>**, with `[security]` at the start of the subject
line.

Do not open a public issue and do not post the details anywhere public first. If
you have a GitHub account and can see the affected repository, a private
[security advisory](https://docs.github.com/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability)
is equally good and keeps the thread attached to the code.

Please include what you would want if you were on the other side: the affected
site or game, the version or build, a description of the issue, and the smallest
sequence of steps that demonstrates it.

The studio is one person. Expect an acknowledgement within **five working days**
and an assessment within **fifteen**. If the report is valid, you will be told
what the fix is and when it ships, and credited in the release notes unless you
prefer not to be.

We will not pursue anyone who reports in good faith, stays within their own
browser and their own data, and gives us a reasonable window before going
public. There is no bug bounty — the studio has no revenue.

## What is in scope

The published sites and the game builds served from them:

| | |
| --- | --- |
| Studio site | `parvamachina.com` |
| Games | `silkward.com`, `regnarium.com`, `sysadmincrisis.com`, `umbraward.com` |
| Mobile | The iOS and Android builds of the games |
| Code | Any repository under [github.com/ParvaMachina](https://github.com/ParvaMachina) |

Interesting findings, given the shape of these projects:

- A **runtime network request** from any game. Every game is built on the rule
  that it makes no network call after the first load; lint rules and dependency
  audits enforce it. If you can observe a request that is not a first-load asset
  fetch or a service worker cache fill, that is a finding in itself, whatever it
  carries.
- A **content security policy bypass** on any of the sites, or a third-party
  origin loading on a page. Everything, fonts included, is served from its own
  domain.
- **Stored cross-site scripting** through a value the game persists — a profile
  name, a custom seed, an imported save.
- **Malicious save import.** The games import JSON they did not write. A crafted
  save that escapes the parser, causes code execution, or corrupts storage
  outside its own keys is in scope.
- **Service worker or cache poisoning** that survives a reload.
- **Supply chain**: a dependency shipping to a game bundle that makes a network
  call, reads storage it has no business reading, or is typosquatted.

## What is not in scope

Not because they are unimportant, but because they are already decided:

- **Local save manipulation.** Saves are plain values in your own browser's
  storage, unsigned and unencrypted, and you can edit them freely. There is no
  server, no leaderboard and no purchase to defend, so there is nothing for a
  cheat to defraud. Editing your own save is not a vulnerability.
- **Missing account security features** — password policy, 2FA, session
  handling, rate limiting. There are no accounts and no authentication anywhere
  in these projects.
- **Data exfiltration findings that require data.** No telemetry, analytics or
  crash reporting is collected, so there is no dataset to breach.
- **Missing security headers on a third-party host**, or findings against
  Cloudflare, GitHub or an app store rather than our code.
- **Automated scanner output with no demonstrated impact**, self-XSS, clickjacking
  on a page with no state-changing action, denial of service by volume, and
  social engineering of the studio.

## Which versions get fixes

Only the **latest released build** of each game and the current deploy of each
site. There are no long-term support branches: the games are free, statically
hosted, and a fix reaches everyone on their next page load.
