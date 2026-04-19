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

You can run it through:
- Markdown
- Obsidian / vault notes
- Plane full lifecycle mode

Plane is a supported operating mode, not a required dependency.

---

## How to read this repo

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
