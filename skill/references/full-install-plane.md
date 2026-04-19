# Plane Full Mode

Use this mode when you want stronger lifecycle control than Markdown or Vault can provide.

Plane is a full installation mode for DERRR, not the default dependency.

## Use Plane when

- multiple slices need visible state transitions
- the team wants explicit issue closure and successor handling
- milestone alignment needs to be operationally visible
- comments, state changes, and issue boundaries are part of the audit trail

## Minimum expectations

Each active slice should exist as its own issue.
Finished slices should be moved to Done.
Active soak/review should be explicit when it matters.
Follow-on work should be created as a successor issue, not implied only in comments.

## Good discipline

- keep milestone notes up to date
- record research findings before implementation
- record implementation start before execution
- close slices explicitly
- create restart anchors when one phase ends and another frontier begins

## Tradeoff

Plane gives stronger lifecycle discipline, but it adds infrastructure and operational overhead.
Use it when that extra control is worth it.
