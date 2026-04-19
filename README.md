# DERRR

**DERRR, making your dumb agents smart 🤓**

DERRR is a hypothesis-driven improvement loop for live or semi-live agent systems.

It helps operators improve agent behavior in a way that is:
- narrow in scope
- auditable
- human-controlled
- restartable
- resistant to drift

DERRR stands for:
- **Document**
- **Execute**
- **Review**
- **Research**
- **Restart**

## What it is

DERRR is a control and investigation method for improving live agent systems when ad hoc iteration is too loose and tuning is premature.

It is designed for situations where:
- failures can appear at multiple layers
- speculative patching is risky
- correctness and auditability matter
- behavior must be trusted before optimization begins

## What it is not

DERRR is not:
- a universal software process
- a replacement for product specs
- a generic debugging recipe for every bug
- a tuning framework
- a project manager

## Why this repo exists

This repo exists because DERRR has now reached a meaningful threshold:
- a formal method design exists
- a first skill draft exists
- the skill draft has been reviewed and pressure-tested
- the method has already produced a better conclusion in a live multi-machine agent-improvement loop

In particular, DERRR was used to avoid a wrong fix by narrowing a supposed “audit hole” into the more accurate question of thin fallback artifacts with lost failure context.

## Current maturity

This is **v0.1**.

That means:
- the method is real
- the first skill draft is usable
- the loop has at least one successful real-world validation
- the project is still intentionally lean

## Repo structure

- `docs/derrr-formal-design.md` — formal method design
- `skill/` — first packaged-skill candidate and supporting references/templates
- `examples/` — real worked example material
- `dist/` — generated packaged skill artifacts when useful

## Operating idea

DERRR uses three scope units:
- **Milestone** — the broader frontier
- **Slice** — the current narrow unit of work
- **Phase** — the current DERRR state of that slice

And one core rule:
- do not execute before the active slice is recorded in the chosen control surface

## Control surfaces

DERRR is method-first, not tool-first.
The control surface can vary:
- Markdown
- Obsidian / vault notes
- Plane full lifecycle mode

## Current next step

Use the first draft skill on additional real loops and tighten the method only where observed misuse or failure justifies it.

## Motto

DERRR should make you more disciplined, but more importantly, it should make you **less wrong**.
