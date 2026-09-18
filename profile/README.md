# Parva Machina

**_parva machina_ — Latin for "small machine."** The name is the design brief: a
mechanism whose rules are visible, whose parts can be counted, and which you can
open and look inside.

A one-person game studio in Türkiye. Four finished games, one rule core. They
open in a browser, they keep running with the network switched off, and not one
of them has ever had a server behind it.

**[parvamachina.com](https://parvamachina.com/)** · Turkish and English, both from
the first release

---

## The games

### SilkWard — turn-based puzzle

A caravan master tracing a lost sibling along the Silk Road. Every level is a
single-screen isometric diorama: you take one step, the enemies take one
deterministic step. No luck, no reflexes, no rule that reveals itself only after
it has beaten you. The story is told almost entirely without words.

`42 levels` · `three acts` · `web + mobile` · **[silkward.com](https://silkward.com/)**

### Regnarium — micro-4X strategy

4X for the player who wants one and does not have six hours. Explore, expand,
exploit and exterminate across a hex map, start to finish in a single sitting.
Combat rolls nothing: the preview you see before attacking **is** the
calculation. The opponent AI plays with the same information and the same moves
you have.

`one session` · `diceless combat` · `AI that does not cheat` · `web + mobile` · **[regnarium.com](https://regnarium.com/)**

### SysAdmin Crisis — terminal simulation

You are the only sysadmin on the night shift. Logs scroll, metrics drift, pagers
go off; you read the signature, name the incident, and fix it by typing a real
command — the same one you would type at 03:00 on a real box. Eight hours of
in-game night, then sunrise.

`00:00 – 08:00` · `real commands` · `web + mobile` · **[sysadmincrisis.com](https://sysadmincrisis.com/)**

### Umbraward — tower defence

One lantern, one road, and everything the dark can send down it. Twenty maps
across four regions, six towers, twenty enemies, three heroes, four bosses, plus
an endless mode on a weekly seed. Which tower you pick matters less than **when**
you build it: the economy is earned between waves, and each region's gimmick —
fog, tunnels, choirs, a road that turns back on itself — breaks whatever
arrangement worked last time.

`20 maps` · `endless mode` · `meta progression` · `installable PWA` · **[umbraward.com](https://umbraward.com/)**

---

## Four promises every game keeps

- **It runs offline.** Load the page once; the same game works in airplane mode.
  This is a durability decision before it is a privacy one — there was never a
  server, so there is no connection to drop and nothing to shut down.
- **Nothing is collected.** No accounts, no telemetry, no analytics, no crash
  reports. Not anonymised — absent. Saves, scores and settings stay in your
  browser's own storage.
- **No chance, no hidden rules.** No dice are rolled anywhere, and the opponent
  AI cannot use a single command you cannot.
- **Free, with nothing to sell you.** No ads, no subscription, no energy meters,
  no wait timers, no daily login rewards.

These are not a marketing page. In each repository they are enforced by lint
rules and dependency audits: the rule core may not import `react`, touch
`window`, call `Math.random`, read `Date.now` or reach `fetch`, and no analytics,
crash-reporting or remote-config package may appear in any game manifest. A pull
request that breaks a promise fails the build.

---

## How they are built

Every game is the same shape underneath.

- **A rule core** — pure TypeScript, zero runtime dependencies. The whole game
  lives here: state, rules, opponent AI, win condition. No DOM, no React Native,
  no clock, no randomness that is not seeded.
- **A web shell** — statically exported, installable as a PWA. There is no
  server side, because there is nothing to run.
- **A mobile shell** — iOS and Android on the same engine. Not a separate
  edition; a second window onto the same game.

Umbraward is the one deliberate exception: it renders through PixiJS 8 on Vite
and ships as a mobile-first web build rather than a native shell. The core rule —
deterministic simulation, no network at runtime — is identical.

Each repository keeps its decisions in a `.ssot/` directory — a single source of
truth holding the PRD, the architecture decision records, the game design
document and the execution log. When code and document disagree, the decision is
updated first and the code second.

---

## This organisation

| Repository | What it is |
| --- | --- |
| [`.github`](https://github.com/ParvaMachina/.github) | This profile, plus the issue templates, security policy and code of conduct shared across the organisation |
| `parvamachina.com` | The studio site — Astro, static, no third-party request on any page |
| `SilkWard` · `Regnarium` · `SysAdminCrisis` · `Umbraward` | The four games |

The game repositories are private while the studio is one person. You do not need
one to report something: see **[Support](https://github.com/ParvaMachina/.github/blob/main/SUPPORT.md)**,
or write to the address below. Bug reports, balance complaints and translation
fixes are the only signal here — there is no analytics dashboard quietly deciding
what gets built next.

---

## Press and brand

Everything needed to write about, stream or record these games is on the
[press kit](https://parvamachina.com/en/press/) — fact sheet, per-game details,
brand assets, and what you are allowed to do with them. You do not need to ask
permission.

The mark is a measuring instrument seen from above: a square frame, an inscribed
circle, a brass dot at the centre.

Palette `#131211` ground · `#e8e3d8` paper · `#c8892f` brass
Typefaces Archivo (headings, body) · JetBrains Mono (labels, data)

---

## Contact

**<contact@parvamachina.com>**

There is no contact form, because a form needs a server. An email is enough —
they get read.

---

## Türkçe

**Parva Machina**, Latince "küçük makine" demek ve ad doğrudan tasarım
sözleşmesi: kuralları görünen, parçaları sayılabilen, açıp içine bakabileceğiniz
bir mekanizma.

Türkiye'de, tek kişilik bir oyun stüdyosu. Dört bitmiş oyun, tek bir kural
çekirdeği. Hepsi tarayıcıda açılır, ağ kapalıyken de çalışmaya devam eder ve
hiçbirinin arkasında hiçbir zaman bir sunucu olmadı.

| Oyun | Tür | Nedir | Sitesi |
| --- | --- | --- | --- |
| **SilkWard** | Sıra tabanlı bulmaca | İpek Yolu boyunca kayıp kardeşinin izini süren bir kervan başı. 42 bölüm, üç perde. | [silkward.com](https://silkward.com/) |
| **Regnarium** | Mikro-4X strateji | Altı saati olmayana 4X: tek oturumda keşfet, genişle, üret, rakipleri alt et. Savaşta zar yok. | [regnarium.com](https://regnarium.com/) |
| **SysAdmin Crisis** | Terminal simülasyonu | Gece vardiyasındaki tek sistem yöneticisi sizsiniz. Olayı okuyup gerçek komutla çözersiniz. | [sysadmincrisis.com](https://sysadmincrisis.com/) |
| **Umbraward** | Kule savunma | Bir fener, bir yol ve karanlığın gönderebileceği her şey. Dört bölge, yirmi harita. | [umbraward.com](https://umbraward.com/) |

**Dört söz, dördü de her oyunda geçerli:**

- **Çevrimdışı çalışır.** Sayfayı bir kez açın; aynı oyun uçak modunda da çalışır.
- **Hiçbir şey toplanmaz.** Hesap yok, telemetri yok, analitik yok, çökme raporu
  yok. Anonimleştirilmiş değil — hiç yok.
- **Şans yok, gizli kural yok.** Hiçbir yerde zar atılmaz; rakip yapay zekâ
  sizin kullanamadığınız tek bir hamleyi kullanamaz.
- **Ücretsiz ve satacak bir şeyi yok.** Reklam yok, abonelik yok, enerji ya da
  bekleme sayacı yok, günlük giriş ödülü yok.

Bunlar bir pazarlama sayfası değil: her depoda lint kuralları ve bağımlılık
denetimleriyle zorunlu kılınıyorlar. Sözü bozan bir pull request build'i
düşürür.

Oyunlar Türkçe ve İngilizce'yi ilk sürümden itibaren birlikte taşır; ikisi de
sonradan eklenmiş bir çeviri değil.

Hata, denge sorunu ya da kötü bir çeviri gördüyseniz
**<contact@parvamachina.com>** yeter — okunuyor.
