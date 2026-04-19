# Vault Quick Start

Use this mode when you want DERRR inside an Obsidian vault or similar note system.

## Suggested note layout

```text
DERRR/
  Active Slice.md
  Milestones.md
  Research Log.md
  Slices/
```

## Minimal workflow

1. Record the active slice in `DERRR/Active Slice.md`.
2. Keep milestone alignment visible in `DERRR/Milestones.md`.
3. Record direct review findings before any second Execute in the same slice, using the shape in `../assets/templates/review-note.md` if helpful.
4. Capture deeper traces, rival hypotheses, and helper findings in `DERRR/Research Log.md`.
5. When a slice ends, use the restart-note shape from `../assets/templates/restart-note.md` and move completed or blocked slices into `DERRR/Slices/` as durable records.
6. Create the next slice explicitly instead of implying it in the previous note.

For a filled example of an active slice, see `../assets/templates/active-slice-example.md`.

## Obsidian-friendly rule

Use links and tags if helpful, but do not let note-graph flexibility blur the active control state.
There should still be one clearly active slice.

## Good uses for Vault mode

- users who already think in notes
- users who want local-first control
- users who want DERRR without project-management infrastructure

## Tradeoff

Vault mode feels natural for humans, but it can become fuzzy if the active slice is not kept explicit.
