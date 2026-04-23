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
Use Plane parent/sub-work-item structure and relations/dependencies when available so lineage is visible in the tracker itself, not just in prose.

## Structure guidance

When Plane supports it in your deployment:
- set the slice's `parent` to its milestone or umbrella issue
- use relations for predecessor/successor and peer dependencies when they clarify the audit trail
- prefer real tracker structure over chat-only or comment-only lineage
- still include enough text in the issue description or comments that exported records remain understandable

A good Plane slice usually makes these visible:
- parent milestone or umbrella issue
- predecessor slice, if this slice exists because of prior findings
- blocked-by or blocks relationships, if applicable
- likely successor candidates once Review or Restart sharpens the next move

## Evidence artifacts

Plane tickets should hold or clearly reference the artifacts that matter.
That includes things like:
- screenshots
- log excerpts
- JSON payload samples
- failing or passing test output
- deploy / rebuild proof
- before / after measurements

For each important artifact, note:
- what it is
- what it proves or fails to prove
- when it was captured
- which slice / phase it belongs to

## API reference

Before making direct Plane API writes, read `references/plane-api-usage.md`.
It now carries:
- official Plane developer-doc entry points
- the core DERRR issue/comment/module endpoints
- the deployment-proven distinction between URL links and issue relations
- the verification checklist that prevents "PATCH looked fine but membership/relation never landed" mistakes

## Good discipline

- keep milestone notes up to date
- record research findings before implementation
- record implementation start before execution
- close slices explicitly
- create restart anchors when one phase ends and another frontier begins
- preserve predecessor/successor links when closing and reopening work
- attach or reference important evidence instead of leaving it stranded in chat or shell history

## Tradeoff

Plane gives stronger lifecycle discipline, but it adds infrastructure and operational overhead.
Use it when that extra control is worth it.
