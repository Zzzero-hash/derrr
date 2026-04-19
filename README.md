# DERRR

<p align="center">
  <strong>DERRR, making your dumb agents smart 🤓</strong><br/>
  A hypothesis-driven improvement loop for live or semi-live agent systems.
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
</p>

---

## Why DERRR exists

**DERRR helps you improve agent behavior without turning the process into chaos.**

It is for situations where:
- failures can appear at multiple layers
- speculative patching is risky
- correctness matters more than speed-running fixes
- tuning should wait until the system is trustworthy

A real example: DERRR helped avoid a wrong fix by narrowing a supposed audit hole into the more accurate question of **thin fallback artifacts with lost failure context**.

That is the standard here: not tidy theory, but a method that helps you become **less wrong** on live systems.

---

## The loop

<table>
  <tr>
    <td><strong>D</strong>ocument</td>
    <td>Record the active slice before acting.</td>
  </tr>
  <tr>
    <td><strong>E</strong>xecute</td>
    <td>Do one narrow action only.</td>
  </tr>
  <tr>
    <td><strong>R</strong>eview</td>
    <td>Check what actually happened.</td>
  </tr>
  <tr>
    <td><strong>R</strong>esearch</td>
    <td>Trace unresolved behavior or rival explanations.</td>
  </tr>
  <tr>
    <td><strong>R</strong>estart</td>
    <td>Close the slice and open the next one explicitly.</td>
  </tr>
</table>

### Core rule

> Do not execute before the active slice is recorded in the chosen control surface.

---

## Quick start paths

### 1) I want the lightest version
Use plain Markdown.

Start with the skill references and run DERRR from notes in a repo or folder.

### 2) I want the full method
Read [`docs/derrr-formal-design.md`](./docs/derrr-formal-design.md)

### 3) I want the practical agent-facing version
Open [`skill/`](./skill/)

### 4) I want proof this came from real use
Read [`examples/`](./examples/)

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
