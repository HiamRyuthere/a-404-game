<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:101010,50:3b6cff,100:c8e01c&height=210&section=header&text=A%20404%20Game&fontSize=72&fontColor=ffffff&animation=fadeIn&fontAlignY=36&desc=Not%20found%3F%20Fine.%20Fight%20for%20the%20belt.&descAlignY=57&descSize=19" width="100%" alt="A 404 Game banner" />

**A self-contained 404 page with a real 3D fighting game built into it.**

One HTML file. One HTTP request. No dependencies, no trackers, no excuses for a boring error page.

<br />

[![Single file](https://img.shields.io/badge/ship%20as-1%20HTML%20file-101010?style=flat-square)](#install)
[![Dependencies](https://img.shields.io/badge/dependencies-zero-3b6cff?style=flat-square)](#)
[![Engine](https://img.shields.io/badge/renderer-raw%20WebGL-c8e01c?style=flat-square&labelColor=101010)](#how-it-works)
[![Requests](https://img.shields.io/badge/external%20requests-0-2ea043?style=flat-square)](#privacy)
[![License: MIT](https://img.shields.io/badge/license-MIT-ff4a3d?style=flat-square)](LICENSE)

</div>

<div align="center">

### ▶ [Play it now](https://hiamryuthere.github.io/a-404-game/)

**https://hiamryuthere.github.io/a-404-game/**

No install, no download. Opens in the browser and the fight starts on click.

</div>

---

## Overview

**A 404 Game** turns the least visited page on a website into the one people send to their friends.

It is a complete one-on-one fighting game — three rounds, a real moveset, a boss — rendered in plain WebGL and embedded inside a single HTML file. The whole thing ships as one request, so it costs a visitor almost nothing to load, and costs you nothing to deploy.

The page still does its actual job: it explains what a 404 is, why it happened, and what to do next. The game just makes people read it.

<br />

## Origin

This started while I was working on an unrelated project. A 404 page needed filling, one thing led to another, and the placeholder turned into an actual fighting game with a moveset and a boss fight.

By the time the other project moved on, the 404 page had become the more interesting piece of work. So it is being opened here as a project in its own right — not as a leftover, but as something that deserved a proper home, a proper README, and the chance to be useful to someone else's site.

<br />

## What's in the box

| | |
|---|---|
| 🥊 **A real fighter** | Best of 3 rounds, 60 seconds each, health bars, round pips, hitstun, knockback. |
| 🎮 **Full moveset** | Punch, kick, uppercut (launches), sweep (knockdown), jump, and a block that cuts damage to a sliver. |
| 👊 **A boss** | Win the final round and you get a **FINISH HIM!** window. The monster has 220 HP and hits for 1.75×. |
| 🧑‍🤝‍🧑 **Three fighters** | **Bajji** (balanced), **Pahalwan** (heavy hitter), **Chhota** (quick) — different speed, power and HP. |
| 🖥️ **Raw WebGL** | A software-modelled 3D arena and fighters in plain WebGL. No three.js, no engine, no build step. |
| 📱 **Touch ready** | On-screen pad appears on mobile: walk, jump, punch, kick, uppercut, sweep, block. |
| 🌗 **Light and dark** | Follows your system preference, remembers your choice in `localStorage`. |
| ♿ **Accessible-ish** | ARIA labels throughout, keyboard-first controls, dialogs with proper roles, `prefers-reduced-motion` honoured. |
| 🔒 **Genuinely private** | No cookies, no analytics, no fonts, no CDN. A strict CSP enforces it. |

<br />

## How to play

| Key | Action |
|:---:|:---|
| <kbd>←</kbd> <kbd>→</kbd> | Walk |
| <kbd>↑</kbd> / <kbd>W</kbd> | Jump |
| <kbd>Z</kbd> | Punch — fast, light |
| <kbd>X</kbd> | Kick — slower, heavier |
| <kbd>V</kbd> | Uppercut — launches them |
| <kbd>B</kbd> | Sweep — knocks them down |
| <kbd>C</kbd> | Block (hold) |
| <kbd>R</kbd> | Restart |

On touch devices the same actions appear as on-screen buttons.

<br />

## Install

**The whole product is one file.** Pick whichever fits your setup.

### 1. Drop it in

```bash
curl -O https://raw.githubusercontent.com/HiamRyuthere/a-404-game/main/index.html
# then serve it as your 404 route
```

**Nginx**

```nginx
error_page 404 /404.html;
```

**Netlify** — add `404.html` to your publish directory. **Vercel** — add it to `public/404.html`. **GitHub Pages** — add `404.html` next to `index.html`.

### 2. Serve it as the whole site

Rename `index.html` to `404.html` where your host expects an error page, or keep it as `index.html` to make it the homepage. Either works — it is the same file.

### 3. Just open it

Double-click `index.html`. No server needed; it runs entirely in the browser.

<br />

## Privacy

The page makes **zero external requests**. That is not a claim, it is enforced:

```html
<meta http-equiv="Content-Security-Policy"
      content="default-src 'none'; style-src 'unsafe-inline';
               script-src 'unsafe-inline'; img-src data:;
               base-uri 'none'; form-action 'none'">
```

If someone later adds a CDN, a font, or a tracker, the browser blocks it. The only thing stored is your theme preference, and only in your own browser.

The WebGL context is created lazily — nothing renders until someone presses **Start fight**.

<br />

## Project structure

```text
a-404-game/
├── index.html    # the entire page: markup, styles, art, game, WebGL engine
├── README.md
└── LICENSE
```

One file on purpose. A 404 page has to load instantly, work when the rest of your assets are broken, and be trivial to deploy. Splitting it across `app.js` and `style.css` would make it easier to read and harder to ship.

> If you want to modify it, the file is sectioned with banner comments — tokens, layout, markup, engine, renderer, game loop. Search for `/* =====` to navigate.

<br />

## Customising

- **Colours** — the design tokens sit in `:root` and `[data-theme="dark"]` at the top of the `<style>` block.
- **Copy** — the headline lives in `<h1 class="lede">`.
- **Roster** — the `CHARS` and `BOSS` arrays hold names, colours and stats (`spd`, `pow`, `hp`).
- **Moves** — the `MOVES` object holds frame timings, range, damage and knockback per attack.
- **The 404 explainer** — the modal text is plain HTML; rewrite it in your own words.

<br />

## Roadmap

Ideas, not promises:

- [ ] Difficulty selector (the boss is deliberately unfair)
- [ ] Best-of-3 score persistence via `localStorage`
- [ ] Gamepad support
- [ ] A `404.min.html` build for people who care about the last few KB
- [ ] Screenshot and short clip in this README

<br />

## Contributing

Issues and pull requests are welcome. For anything larger than a typo fix, open an issue first so we can agree on the direction before you spend time on it.

```bash
git clone https://github.com/HiamRyuthere/a-404-game.git
cd a-404-game
# open index.html — there is no build step
```

<br />

## ⚠️ Read this before you use it

> **The code in this repository was written with AI assistance.**
>
> It was reviewed and tested in a browser before being committed, but AI-assisted code is not a substitute for your own judgement.
>
> **Before using this in anything critical** — production systems, anything handling user data, payments, authentication, or anything a business depends on — **read the code yourself and review it properly.** Treat it exactly as you would treat any third-party snippet you found on the internet.
>
> For a 404 page, the risk is small: it is static, self-contained, and touches no data. Reviewing it takes an afternoon, and you should still do it.

<br />

## License

Released under the [MIT License](LICENSE). Use it, change it, ship it, sell it — just keep the licence notice.

<br />

<div align="center">

**The page nobody planned to visit, now the one they remember.**

⭐ If this made a 404 page less depressing, star the repo.

</div>
