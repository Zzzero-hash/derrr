---
name: derrr
description: Hypothesis-driven improvement loop for live or semi-live agent systems with active behavioral uncertainty. Use when the problem shows up as malformed structured output, persistence mismatches, validator/coercion confusion, audit gaps, soak-driven review needs, repeated regressions, or cases where tuning should wait until behavior is trustworthy. Best for multi-step behavior investigation and correction where the user wants explicit slice control and auditable iteration. Do not use for trivial one-file fixes, pure feature building, or broad brainstorming with no active behavioral uncertainty.
---

# DERRR

Run the loop as:
- Document
- Execute
- Review
- Research
- Restart

Use only three scope units:
- **Milestone**: the broader frontier
- **Slice**: the current narrow unit of work
- **Phase**: the current DERRR state of that slice

Simple nesting:
- milestone
  - slice
    - phase transitions through DERRR

## Core rule

Do not execute before the active slice is recorded in the chosen control surface.

If the control surface is Plane Full, Plane is the source of truth for active slice identity, parentage, module assignment, and state. Prefer live Plane reads over memory, branch names, or chat summaries whenever they disagree or might be stale.

If the control surface is Plane Full, every milestone and slice must be assigned to exactly one module before execution begins. Module assignment is mandatory because objective progress visibility depends on structurally grouped work, not just states and labels. Verify that the assignment actually landed in the deployment's real module-membership surface, not merely that a generic issue update returned success.

This skill is for live improvement loops with real behavioral uncertainty.
If the task is a trivial one-file fix, use a simpler workflow.

When the control surface supports structure, use the structure.
Do not leave lineage, dependencies, or evidence only in chat when the system can carry them directly.

## First question

Ask one setup question first:
- Which control surface should hold the loop: **Markdown**, **Vault**, or **Plane Full**?

If the user does not know, default to:
- **Markdown** for the lightest portable setup
- **Vault** if they already work in Obsidian
- **Plane Full** only when they already want explicit issue-state lifecycle control

Then proceed with the matching reference:
- Markdown → read `references/quickstart-markdown.md`
- Vault → read `references/quickstart-obsidian.md`
- Plane Full → read `references/full-install-plane.md`

If Plane Full work will touch the API directly, also read `references/plane-api-usage.md` before making tracker writes.

Before naming or resuming a Plane slice, ground yourself in live tracker state first. Verify:
- the exact active issue id and title
- its current state
- its parent milestone or umbrella item
- its module membership
- any predecessor/successor or dependency links that matter to the current slice

If live Plane state cannot be queried, do not confidently invent or rename slice identity from memory alone. Say that live tracker access is missing and ask for it or for a user-confirmed issue id.

## What to do in each phase

### Document
- record the active slice
- record the hypothesis
- record the evidence target
- record the execution boundary
- record success/failure conditions
- name the current milestone frontier
- if using Plane Full, assign the milestone and slice to one module immediately
- if using Plane Full, verify module membership through the deployment's real membership surface when needed, especially if normal issue reads do not echo module linkage
- record parent / child / predecessor / dependency structure when the control surface supports it
- record expected evidence artifacts when known in advance (screenshots, logs, JSON samples, test output, deploy proof)

Minimum bar before leaving Document:
- the hypothesis must be specific enough to be tested or weakened by one bounded action
- the evidence target must say what signal would directly change your confidence
- if using Plane Full, the active milestone and slice must already have module assignment
- if using Plane Full, the active slice identity must be confirmed from live tracker state rather than inferred from memory, branch names, or stale ticket prefixes
- if the Plane deployment does not expose module linkage on ordinary issue payloads, confirm via the module-issues relation endpoint or equivalent membership view before treating the board as clean
- if using a structured tracker such as Plane, the slice should include its parent milestone or umbrella issue and any already-known relations or dependencies

Forbidden:
- implementation before documentation exists
- hidden scope broadening
- placeholder slices such as "investigate this" with no testable hypothesis or evidence target
- leaving Plane milestones or slices unassigned to a module
- assuming module assignment succeeded without checking the deployment's real membership surface
- inferring active Plane issue identity from memory when live tracker reads are available or expected

### Execute
- do one narrow action only
- prefer instrumentation or measurement before broader fixes
- keep assumptions explicit after acting

Transition rule:
- do not begin a second Execute in the same slice until a Review artifact states what the previous Execute proved, failed to prove, or made anomalous

Forbidden:
- opportunistic refactors
- tuning while correctness is unresolved
- chaining speculative fixes

### Review
- inspect direct effects of the last action
- compare expected vs observed effect
- decide if direct evidence is sufficient or if soak is needed
- attach or reference the concrete evidence artifacts that support the review when available

Minimum bar before leaving Review:
- the review artifact must state what the last Execute step proved, failed to prove, or made anomalous
- the review artifact must name the evidence class: direct, suggestive, aggregate, or anomalous

Forbidden:
- treating weak evidence as closure
- patching again before acknowledging what happened
- empty review notes such as "seems better" with no proved/failed/anomalous outcome

### Research
- investigate unresolved behavior or rival explanations
- trace code paths and correlate logs/artifacts/counters
- use bounded helpers or reviewers if useful

Transition rules:
- if research produces a new hypothesis centered on a different observability layer than the active slice, treat it as a successor-slice candidate instead of silently expanding the current slice
- if research produces an adjacent hypothesis on the same observability layer but outside the current narrow question, record it as a successor-slice candidate instead of absorbing it into the current slice

Forbidden:
- implementation disguised as research
- treating helper output as control truth
- expanding the slice just because the adjacent issue feels nearby

### Restart
- close the current slice explicitly
- summarize what was learned
- create the successor slice explicitly
- re-check milestone alignment
- preserve predecessor/successor linkage in the control surface when supported
- use `assets/templates/restart-note.md` when creating the closure/restart artifact

Transition rule:
- do not accept a new active slice until the previous slice has a recorded restart artifact showing closure, blockage, or invalidation

Forbidden:
- implied continuation
- mental closure with no recorded restart artifact

## Observability rule

Trace failures through these layers:
1. prompt/contract
2. raw response
3. parsed output
4. accepted/validated output
5. persisted artifact
6. runtime behavior
7. aggregate/soak

Ask:
- Where did the failure first become visible?
- Which layer is masking or reshaping it?

## Structured control surfaces

When the chosen control surface supports hierarchy and relations, use them deliberately.

For Plane Full mode specifically:
- treat live Plane reads as authoritative for current slice identity, state, parentage, and linkage
- assign every milestone and slice to exactly one module before execution begins
- do not assume module assignment works through generic issue PATCH fields on every Plane deployment, some deployments require the dedicated module-issues relation endpoint
- after bulk module assignment, verify membership by listing module issues, not just by checking whether issue PATCH calls returned success
- set the active slice under its parent milestone or umbrella work item when appropriate
- add explicit relations for predecessor, successor, blocked-by, blocks, duplicate, or peer linkage when they clarify the audit trail
- keep the ticket body or comments self-explanatory even when relations exist, so exported or copied records still make sense
- do not rely on chat-only lineage if Plane can store it directly
- do not pick branch names, PR titles, or proof claims from recalled issue numbers until the live Plane issue has been confirmed

## Evidence artifacts

Useful debugging artifacts are first-class evidence, not decoration.
Capture and attach or link them when they materially help explain behavior.

Common artifact classes:
- screenshots
- log excerpts
- JSON samples
- failing or passing test output
- deploy or rebuild proof
- before/after metric snapshots

For each important artifact, record:
- what it is
- what it proves or fails to prove
- when it was captured
- which slice and phase it belongs to

## Human control checkpoints

Ask before:
- changing the source of truth
- broadening scope
- moving from research into implementation when risk is meaningful
- closing milestone-level work
- using public/external systems
- introducing helper agents that materially change cost or risk

## DERRR stop signals

If any of these appear, stop and tighten the loop before continuing:
- execute chained into another execute with no real review artifact
- research includes hidden implementation
- research discovers a different observability layer but tries to keep the same slice anyway
- research discovers an adjacent same-layer issue and tries to absorb it into the same slice anyway
- successor work exists only in chat, not in the control surface
- branch names or PR titles carry stale tracker ids that were never verified against live Plane
- hierarchy or relations exist only in prose even though the chosen tracker supports them directly
- important screenshots, logs, or samples exist only in chat and are not referenced in the control surface
- helper agent opinion is treated as authoritative without review
- tuning starts before correctness is trustworthy
- artifacts, logs, and counters disagree and no one owns the mismatch
- a new slice starts before the previous one has a restart artifact

Treat these as red flags, not style notes.
If one appears, pause and decide whether the current slice should be reviewed, split, restarted, or explicitly closed.

## Worked example

Read `references/worked-example-hold-collapse.md` for a concrete example drawn from a real behavior-improvement loop.

## v0.1 note

This is a first real draft.
It is meant to be useful, not grand.
If the skill starts adding more ceremony than clarity, tighten the loop instead of defending the method.
