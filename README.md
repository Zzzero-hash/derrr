# DERRR

<p align="center">
  <strong>DERRR, making your dumb agents smart 🤓</strong><br/>
  <em>A hypothesis-driven improvement loop for live or semi-live agent systems.</em>
</p>

<p align="center">
  <a href="./docs/derrr-formal-design.md">Formal design</a> ·
  <a href="./skill/">Skill</a> ·
  <a href="./examples/">Examples</a>
</p>

<p align="center">
  <code>v0.1</code>
  <code>method-first</code>
  <code>markdown-friendly</code>
  <code>plane-optional</code>
  <code>obsidian-optional</code>
  <code>less-wrong-maxxing</code>
  <code>MIT licensed</code>
</p>

<p align="center">
  <strong>From black-box AI behavior to evidence-backed improvement loops.</strong>
</p>

---

## Why DERRR exists

**DERRR is about turning black-box AI behavior into something you can actually observe, test, and improve on purpose.**

A lot of AI work still runs on one-shot brilliance, lucky prompts, scattered logs, and post-hoc storytelling.
That can feel impressive right up until the system regresses, contradicts itself, or fails in production and nobody can explain why.

DERRR exists to push that in a more scientific direction:
- deeper observability for otherwise black-box AI behavior
- evidence over vibes
- repeatable improvement loops instead of random heroic saves
- live chain context instead of isolated prompt snapshots
- narrow, auditable slices instead of speculative patch piles

In plain English: DERRR tries to turn "the model did something amazing once" into a repeatable research and improvement process.

A real example: DERRR helped avoid a wrong fix by narrowing a supposed audit hole into the more accurate question of **thin fallback artifacts with lost failure context**.

That is the bar here. Not tidy theory. Not framework cosplay. A way to make AI system improvement more evidence-based, more explainable, and a lot less hand-wavy.

---

## The loop

```text
Document -> Execute -> Review -> Research -> Restart
    ^                                            |
    |____________________________________________|

aka: stop guessing, do one thing, check it, learn something, begin again
```

<table>
  <tr>
    <td><strong>D</strong>ocument</td>
    <td>Write down what you think is happening before you start flailing.</td>
  </tr>
  <tr>
    <td><strong>E</strong>xecute</td>
    <td>Do one narrow thing, not five "while we're in here" things.</td>
  </tr>
  <tr>
    <td><strong>R</strong>eview</td>
    <td>Check what actually happened, not what you hoped happened.</td>
  </tr>
  <tr>
    <td><strong>R</strong>esearch</td>
    <td>Trace the weirdness until the next real move becomes obvious.</td>
  </tr>
  <tr>
    <td><strong>R</strong>estart</td>
    <td>Close the slice cleanly and start the next one like an adult.</td>
  </tr>
</table>

### Core rule

> Do not execute before the active slice is recorded in the chosen control surface.
>
> In other words: no freestyling your way into fake confidence.

---

## Quick start paths

<table>
  <tr>
    <td>📝 <strong>I want the lightest version</strong></td>
    <td>Use plain Markdown. No dashboard, no platform, no ceremony. Just notes, slices, and receipts.</td>
  </tr>
  <tr>
    <td>🧠 <strong>I want the full method</strong></td>
    <td>Read <a href="./docs/derrr-formal-design.md"><code>docs/derrr-formal-design.md</code></a>.</td>
  </tr>
  <tr>
    <td>🤖 <strong>I want the practical agent-facing version</strong></td>
    <td>Open <a href="./skill/"><code>skill/</code></a>.</td>
  </tr>
  <tr>
    <td>🔬 <strong>I want proof this came from real use</strong></td>
    <td>Read <a href="./examples/"><code>examples/</code></a>.</td>
  </tr>
  <tr>
    <td>⚡ <strong>I want the short pitch</strong></td>
    <td>DERRR is what you use when you want to stop treating AI behavior like magic and start treating it like an observable system.</td>
  </tr>
</table>

---

## What DERRR is

DERRR is a control and investigation method for improving live agent systems when ad hoc iteration is too loose and tuning is premature.

<table>
  <tr>
    <th align="left">Good fit</th>
    <th align="left">Bad fit</th>
  </tr>
  <tr>
    <td valign="top">
      - multi-step behavior failures<br/>
      - audit gaps<br/>
      - persistence mismatches<br/>
      - validator/coercion confusion<br/>
      - soak and review loops<br/>
      - repeated regressions
    </td>
    <td valign="top">
      - trivial one-file fixes<br/>
      - pure feature building with no live behavioral uncertainty<br/>
      - broad brainstorming with no active failure to narrow<br/>
      - tuning-first workflows<br/>
      - anything where you are mostly trying to look organized instead of actually learn something
    </td>
  </tr>
</table>

---

## Control surfaces

DERRR is **method-first, not tool-first**.

That means you do **not** need any special platform to use it.
Markdown-only use is completely valid.

### Supported modes

- **Markdown**  
  Plain `.md` files in a repo or working folder.

- **Obsidian**  
  A Markdown note-taking app built around local note vaults. Useful if you already work that way.

- **Plane**  
  An issue-tracking and project-management tool. Useful if you want explicit lifecycle state, issue history, and a stronger audit trail.

### Important

- **Plane is optional**
- **Obsidian is optional**
- **Markdown-only is a first-class way to use DERRR**

### Optional tool setup links

- Obsidian docs: <https://help.obsidian.md/>
- Plane app: <https://plane.so/>
- Plane API/docs: <https://developers.plane.so/api-reference/introduction>

### If you want to use Plane

1. install or access Plane
2. create a workspace and project
3. create an API key
4. use Plane as the source of truth for active slices and lifecycle state

### If you want to use Obsidian

1. install Obsidian
2. create or open a vault
3. store DERRR notes and templates inside that vault

---

## Repo map

| Path | What it is |
| --- | --- |
| [`docs/derrr-formal-design.md`](./docs/derrr-formal-design.md) | the full method |
| [`skill/`](./skill/) | the practical agent-facing version |
| [`examples/`](./examples/) | worked example material from a real loop |
| [`dist/`](./dist/) | packaged skill artifacts |
| [`README.md`](./README.md) | the fast pitch for humans who want the point before the theory |

---

## Current maturity

> **Status: v0.1**
>
> Real enough to use, early enough to still have a little duct tape showing.

That means:
- the method is real
- the first skill draft is usable
- the loop has at least one real-world validation
- the project is intentionally lean
- rough edges are expected

### Translation

This is not a giant polished platform.
It is a sharp working method with real field mileage, now being turned into a proper public artifact.

---

## What happens next

Use the first draft skill on additional real loops and tighten the method only where observed misuse, drift, or confusion actually justifies it.

---

## Credibility, sources, and credit

DERRR was not invented in a vacuum. It is a practical synthesis shaped by real live-loop work and by adjacent ideas from:
- observability and tracing culture in software/systems engineering
- scientific debugging and hypothesis-driven investigation
- issue-driven operational workflows
- evidence-first evaluation habits from ML and AI systems work

This repo's specific DERRR framing, wording, templates, and operating loop were developed in the course of real work by Christian Penrod with agent assistance.

### External tools and docs referenced in the repo

- Obsidian docs: <https://help.obsidian.md/>
- Plane app: <https://plane.so/>
- Plane API/docs: <https://developers.plane.so/api-reference/introduction>

If this repo becomes more useful over time, those references should probably grow into a more explicit acknowledgments section rather than pretending the project emerged from pure mountain-cave revelation.

---

## License

This project is licensed under the **MIT License**.
See [`LICENSE`](./LICENSE).

---

## Support

If DERRR helps you make an AI system less wrong, a star on the repo is appreciated.

If you want to support the work directly:
- Buy Me a Coffee: <https://buymeacoffee.com/zero.hash>

---

## Motto

> DERRR should make you more disciplined, but more importantly, it should make you **less wrong**.
>
> If it ever becomes more pompous than useful, the method has failed the vibe check.

```text
less guessing
more tracing
less patch soup
more evidence
less magic
more system
```
