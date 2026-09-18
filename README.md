# ParvaMachina/.github

The organisation-level repository for [Parva Machina](https://parvamachina.com/).
It ships no code. It holds two things GitHub reads from a specially named
repository:

1. **The organisation profile** — [`profile/README.md`](profile/README.md) is what
   renders at [github.com/ParvaMachina](https://github.com/ParvaMachina).
2. **Default community health files** — the code of conduct, contributing guide,
   security policy, support page, issue forms and pull request template that
   every repository in the organisation inherits unless it defines its own.

## Layout

```
.
├── profile/
│   └── README.md               → the org profile page
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── config.yml          → the chooser: links + whether blank issues are allowed
│   │   ├── bug_report.yml
│   │   ├── balance_or_design.yml
│   │   ├── translation.yml
│   │   └── accessibility.yml
│   └── PULL_REQUEST_TEMPLATE.md
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── SECURITY.md
├── SUPPORT.md
├── LICENSE
└── README.md                   → this file
```

Two directory rules are GitHub's, not preference:

- The profile README must be at **`profile/README.md`**. At the repository root
  it is just this repo's own README and never reaches the organisation page.
- Default **issue forms and the pull request template** must live under
  `.github/` *inside this repository* — hence the `.github/.github/` nesting.
  The other health files are read from the repository root.

## What inheritance does and does not cover

A repository that defines its own `CONTRIBUTING.md`, `SECURITY.md` or
`ISSUE_TEMPLATE/` overrides the default here. There is no merging: the more
specific file wins whole.

Defaults from this repository reach **public** repositories only. The game
repositories are private today, so what they actually inherit is the pull
request template and nothing else — the policies below are still the ones that
apply, they are simply not surfaced in their issue UI. The same is true of the
profile itself: this repository must stay public for
[github.com/ParvaMachina](https://github.com/ParvaMachina) to render anything.

## Editing the profile

The profile is a plain Markdown file, but it renders in a narrower column than a
repository README and through a reduced HTML subset. Keep to Markdown, keep
tables to four columns or fewer, and use **absolute URLs** — a relative link
resolves against this repository, not against the organisation page, so
`SUPPORT.md` would 404 for a visitor.

Facts on the profile are copied from sources that already own them, and should be
re-copied rather than re-invented when they change:

| Fact on the profile | Where it is actually decided |
| --- | --- |
| Game taglines, genres, domains | `parvamachina.com` → `src/data/games.ts`, `src/i18n/ui.ts` |
| Studio description, the four promises | `parvamachina.com` → `src/content/pages/en/about.md` |
| Fact sheet, palette, typefaces, the mark | `parvamachina.com` → `src/content/pages/en/press.md` |
| Per-game numbers (levels, maps, modes) | each game repository's `README.md` and `.ssot/` |

## Licence

The templates, policies and configuration in this repository are MIT licensed —
see [`LICENSE`](LICENSE) — so another project can lift them without asking.

That licence does not extend to the Parva Machina name, the mark, the brand
assets or the game names and descriptions. Terms for those are on the
[press kit](https://parvamachina.com/en/press/).
