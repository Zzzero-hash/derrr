# DERRR

<p align="center">
  <img src="https://grovextech.com/assets/derrr/banner.svg" alt="DERRR — Document · Execute · Review · Research · Restart. Making your dumb agents smart." width="100%" />
</p>

<p align="center">
  <strong>DERRR, making your dumb agents smart 🤓</strong><br/>
  <em>A hypothesis-driven development and maintenance loop for agent systems and large codebases.</em>
</p>

<p align="center">
  <a href="./docs/derrr-formal-design.md">🧪 Formal design</a> ·
  <a href="./skill/">🛠️ Skill</a> ·
  <a href="./examples/">👹 Examples</a>
</p>

<p align="center">
  <code>v0.1</code>
  <code>method-first</code>
  <code>markdown-friendly</code>
  <code>plane-optional</code>
  <code>obsidian-optional</code>
  <code>MIT licensed</code>
</p>

<p align="center">
  <img alt="README artifact check" src="https://img.shields.io/github/actions/workflow/status/Zzzero-hash/derrr/readme-artifact-check.yml?branch=main&label=readme%20artifact%20check" />
  <img alt="Last commit" src="https://img.shields.io/github/last-commit/Zzzero-hash/derrr" />
</p>

> [!TIP]
> **DERRR is for when the model is freelancing, the codebase is sprawling, the logs are a swamp, and the team is one cursed patch away from writing fan fiction about the root cause.**

## What this is

DERRR is a loop for developing and maintaining messy systems without lying to yourself.

It is for:
- weird agent behavior
- large codebases with too many moving parts
- regressions that keep coming back in new costumes
- teams that need an actual audit trail, not vibes and folklore

It is **not** just a debugging gimmick.
It is a development and maintenance discipline for systems that get slippery under pressure.

```text
Document → Execute → Review → Research → Restart
```

In plain English:
- write down the active slice before touching the system
- do one narrow thing
- review what actually happened
- research only when the next move is still unclear
- restart cleanly instead of wandering into patch soup

<p align="center">
  <img src="https://grovextech.com/assets/derrr/loop-diagram.svg" alt="The DERRR loop: Document, Execute, Review, Research, Restart, then back to Document." width="720" />
</p>

## Why this exists

A lot of AI and agent work currently runs on:
- vibes
- screenshots
- half-read logs
- lucky prompt edits
- accidental regressions
- somebody saying "seems fixed?"

That is not a serious development loop.
That is goblin ranching.

DERRR exists to turn that into something tighter:
- one active slice at a time
- one bounded move at a time
- explicit review before more changes
- explicit restart instead of fake closure
- audit trail first, heroics second

## The goblin pitch

Without DERRR:
- weird thing happens
- three people invent three theories
- two patches land together
- the system behaves for seven minutes
- everyone declares victory
- nobody knows what actually changed

With DERRR:
- active slice gets recorded first
- one narrow move gets executed
- review says what proved, failed, or stayed weird
- restart closes the slice cleanly
- next move comes from evidence instead of caffeine improv

## Core rule

> Do not execute before the active slice is recorded in the chosen control surface.

No freestyling your way into fake confidence.

## Choose your flavor

DERRR is **method-first, not tool-first**.

You can use it with:
- **Markdown** for the lightest repo-native version
- **Obsidian** if you already live in a vault
- **Plane** if you want explicit lifecycle state and a stronger audit trail
- **the skill** if you want to put the method in front of an assistant

Important:
- Plane is optional
- Obsidian is optional
- Markdown-only is completely valid

## Start here

- **I want the quick pitch** → stay here
- **I want the full method** → [`docs/derrr-formal-design.md`](./docs/derrr-formal-design.md)
- **I want the practical assistant version** → [`skill/`](./skill/)
- **I want real field mileage** → [`examples/`](./examples/)

## Good fit / bad fit

**Good fit:**
- multi-step behavior failures
- audit gaps
- persistence mismatches
- validator/coercion weirdness
- soak and review loops
- repeated regressions in messy systems

**Bad fit:**
- trivial one-file fixes
- pure feature building with no active uncertainty
- broad brainstorming with no real bottleneck
- tuning-first workflows
- looking organized without actually learning anything

Also, yes, a drooling little goblin as the logo sounds extremely correct.

## Status

**v0.1**

Real enough to use, early enough to still have a little duct tape showing.

## Brand kit

Editable source SVGs live under [`assets/`](./assets/):

- [`assets/banner-v2.svg`](./assets/banner-v2.svg) — README / landing banner source
- [`assets/logo/derrr-logo-primary.svg`](./assets/logo/derrr-logo-primary.svg) — full mark with drooling clipboard goblin
- [`assets/logo/derrr-icon.svg`](./assets/logo/derrr-icon.svg) — square icon / avatar
- [`assets/logo/derrr-logo-mono.svg`](./assets/logo/derrr-logo-mono.svg) — monochrome, uses `currentColor`
- [`assets/social/derrr-social-preview.svg`](./assets/social/derrr-social-preview.svg) — 1280×640 Open Graph card source
- [`assets/diagrams/derrr-loop.svg`](./assets/diagrams/derrr-loop.svg) — loop diagram source

Canonical hosted render targets live at:
- `https://grovextech.com/assets/derrr/banner.svg`
- `https://grovextech.com/assets/derrr/logo-primary.svg`
- `https://grovextech.com/assets/derrr/icon.svg`
- `https://grovextech.com/assets/derrr/social-preview.png`
- `https://grovextech.com/assets/derrr/loop-diagram.svg`

If you want the whole goblin bundle in one place, start with [`assets/README.md`](./assets/README.md). It has:
- canonical file inventory
- palette + mascot rules
- export commands for PNGs
- hosted asset conventions for `grovextech.com`
- GitHub social preview instructions

## License

MIT. See [`LICENSE`](./LICENSE).
