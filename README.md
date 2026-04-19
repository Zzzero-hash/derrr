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
</p>

---

## Why DERRR exists

**Because live agent improvement gets stupid fast if you do not control it.**

DERRR is for moments when:
- the agent is doing something weird
- the logs and artifacts disagree
- everyone wants to patch three things at once
- tuning is being suggested way too early
- the real answer is probably "slow down, narrow it, prove it"

A real example: DERRR helped avoid a wrong fix by narrowing a supposed audit hole into the more accurate question of **thin fallback artifacts with lost failure context**.

That is the bar here. Not tidy theory. Not framework cosplay. Just a method that helps you become **less wrong** on live systems.

---

## The loop

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

---

## Quick start paths

### 1) I want the lightest version
Use plain Markdown.

No dashboard, no platform, no ceremony. Just notes, slices, and receipts.

### 2) I want the full method
Read [`docs/derrr-formal-design.md`](./docs/derrr-formal-design.md)

### 3) I want the practical agent-facing version
Open [`skill/`](./skill/)

### 4) I want proof this came from real use
Read [`examples/`](./examples/)

### 5) I want the short pitch
DERRR is what you use when "just vibe-debug it" has started costing real money, trust, or time.

---

## What DERRR is

DERRR is a control and investigation method for improving live agent systems when ad hoc iteration is too loose and tuning is premature.

### Good fit
- multi-step behavior failures
- audit gaps
- persistence mismatches
- validator/coercion confusion
- soak and review loops
- repeated regressions

### Bad fit
- trivial one-file fixes
- pure feature building with no live behavioral uncertainty
- broad brainstorming with no active failure to narrow
- tuning-first workflows
- anything where you are mostly trying to look organized instead of actually learn something

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

- [`docs/derrr-formal-design.md`](./docs/derrr-formal-design.md) → the full method
- [`skill/`](./skill/) → the practical agent-facing version
- [`examples/`](./examples/) → worked example material from a real loop
- [`dist/`](./dist/) → packaged skill artifacts

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

---

## What happens next

Use the first draft skill on additional real loops and tighten the method only where observed misuse, drift, or confusion actually justifies it.

---

## Motto

> DERRR should make you more disciplined, but more importantly, it should make you **less wrong**.
>
> If it ever becomes more pompous than useful, the method has failed the vibe check.
