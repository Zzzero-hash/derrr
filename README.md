# DERRR

> **DERRR, making your dumb agents smart 🤓**
>
> A hypothesis-driven improvement loop for live or semi-live agent systems.

---

## At a glance

**DERRR helps you improve agent behavior without turning the process into chaos.**

It is built for loops that need to stay:
- narrow
- auditable
- human-controlled
- restartable
- resistant to drift

### The acronym

- **D**ocument
- **E**xecute
- **R**eview
- **R**esearch
- **R**estart

---

## What it is

DERRR is a control and investigation method for improving live agent systems when ad hoc iteration is too loose and tuning is premature.

**Use it when:**
- failures can appear at multiple layers
- speculative patching is risky
- correctness and auditability matter
- behavior must be trusted before optimization begins

**Not for:**
- universal software process ambitions
- replacing product specs
- generic debugging for every small bug
- tuning-first workflows
- pretending project management is the same thing as control

---

## Why this repo exists

DERRR crossed the line from idea to working method:
- formal method design exists
- first skill draft exists
- skill draft has been reviewed and pressure-tested
- the method has already changed a real live investigation for the better

A real example: DERRR helped avoid a wrong fix by narrowing a supposed audit hole into the more accurate question of **thin fallback artifacts with lost failure context**.

That is the standard here: not tidy theory, but a method that helps you become **less wrong** on live systems.

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

## Repo map

- `docs/derrr-formal-design.md` → the full method
- `skill/` → the practical agent-facing version
- `examples/` → worked example material from a real loop
- `dist/` → packaged skill artifacts

---

## Core operating idea

DERRR uses three scope units:

- **Milestone** → the broader frontier
- **Slice** → the current narrow unit of work
- **Phase** → the current DERRR state of that slice

### Core rule

> Do not execute before the active slice is recorded in the chosen control surface.

---

## Control surfaces

DERRR is **method-first, not tool-first**.

That means you do **not** need any special platform to use it.
You can run DERRR with plain Markdown files and a repo if that is all you want.

Supported control surfaces:
- **Markdown**: plain `.md` files in a repo or working folder
- **Obsidian**: a popular Markdown note-taking app and vault system, useful if you already live in notes
- **Plane**: an issue-tracking/project-management tool, useful if you want explicit lifecycle state and issue-based audit history

Important:
- **Plane is optional**
- **Obsidian is optional**
- **Markdown-only use is completely valid**

If you want setup docs for the optional tools:
- Obsidian docs: <https://help.obsidian.md/>
- Plane docs: <https://developers.plane.so/api-reference/introduction>
- Plane app: <https://plane.so/>
- Plane API key docs: <https://developers.plane.so/api-reference/introduction>

If you use Plane, the basic setup path is:
1. install or access Plane
2. create a workspace/project
3. create an API key
4. use Plane as the source of truth for active slices and lifecycle state

If you use Obsidian, the basic setup path is:
1. install Obsidian
2. create or open a vault
3. store DERRR notes/templates inside that vault

---

## How to read this repo

### If you want the lightest starting point
Use Markdown only and read the skill references for the Markdown quickstart.

### If you want the full method
Start with `docs/derrr-formal-design.md`

### If you want the practical version
Look at `skill/`

### If you want proof this came from real use
Read `examples/`

---

## What happens next

Use the first draft skill on additional real loops and tighten the method only where observed misuse, drift, or confusion actually justifies it.

---

## Motto

> DERRR should make you more disciplined, but more importantly, it should make you **less wrong**.
