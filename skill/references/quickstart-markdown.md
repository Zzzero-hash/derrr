# Markdown Quick Start

Use this mode when you want DERRR with minimal infrastructure.

## Suggested file layout

```text
derrr/
  active.md
  milestones.md
  research.md
  slices/
```

## Minimal workflow

1. Create or update `derrr/active.md` with the current milestone, slice, phase, and hypothesis.
2. Do one narrow execution step only after `active.md` reflects reality.
3. Record direct review findings in the active slice or with `../assets/templates/review-note.md` before any second Execute in the same slice.
4. If the result is unresolved, move into Research explicitly.
5. When the slice is complete or invalidated, use `../assets/templates/restart-note.md` to close it and create the next slice in `derrr/slices/`.

## Minimal active slice shape

Use the template in `../assets/templates/active-slice.md`.
See `../assets/templates/active-slice-example.md` for one filled example.

At minimum, capture:
- milestone
- slice title
- current phase
- hypothesis
- evidence target
- execution boundary
- success condition
- failure condition
- next restart rule

## Good uses for Markdown mode

- solo operator workflows
- repo-native work
- situations where auditability matters but Plane is overkill
- early adoption of the method

## Tradeoff

Markdown mode is lightweight, but state enforcement is manual.
Be strict about keeping `active.md` current.
