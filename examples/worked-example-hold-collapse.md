# Worked Example: HOLD Collapse to Judge-Richness Enforcement

This example shows the shape of a DERRR loop using a real style of agent-behavior problem.

## Milestone

Make candidate generation behavior auditable and trustworthy before tuning.

## Slice 1

### Document
Question:
- Why are live decisions collapsing to HOLD with singleton candidate sets?

Hypothesis:
- persistence or validator normalization is collapsing richer upstream outputs into HOLD-only artifacts.

Evidence target:
- inspect persisted artifacts and trace whether candidate richness already disappears upstream.

Boundary:
- observation and tracing only, no policy change yet.

### Execute
- inspect persisted decision artifacts
- inspect validator and persistence code paths

### Review
Observed:
- persisted artifacts already contained HOLD-only candidate sets upstream of persistence fallback
- validator preserved candidate sets rather than shrinking them

Result:
- original hypothesis weakened
- persistence is not the primary culprit

### Research
New research question:
- which upstream path is producing the weak outputs?

### Restart
Create successor slice:
- trace upstream provider/judge response production path

## Slice 2

### Document
Question:
- are raw model outputs missing `policy_action` and `candidate_actions`, or is the parser losing them?

Hypothesis:
- models are omitting these fields because the debate prompt contract does not require them.

Evidence target:
- raw response audit logging before parse

Boundary:
- instrumentation only

### Execute
- add narrow raw-response audit logging

### Review
Observed:
- raw outputs themselves lacked `policy_action` and `candidate_actions`

Result:
- omission is upstream of parse

### Research
- inspect role prompts and shared local wrapper contract

### Restart
Create successor slice:
- align prompt/schema contract to require richer structured outputs

## Slice 3

### Document
Question:
- will requiring structured debate fields materially break the old collapse regime?

Hypothesis:
- enforcing `policy_action` and `candidate_actions` in debate prompts will improve judge and final decision richness.

Boundary:
- prompt/schema hardening only

### Execute
- patch prompts
- rebuild and restart

### Review
Observed:
- structured output improved materially
- judge became richer first
- bull and bear lagged

### Research
- longer soak showed role asymmetry and acceptance softness

### Restart
Create successor slices for:
- bear schema parity
- stricter debate-role acceptance
- judge-specific acceptance
- shared wrapper alignment

## Later loop lesson

A later judge-richness enforcement slice proved a different kind of lesson:
- a correctness-improving rejection gate can expose a new audit-gap question
- that means the next bottleneck may still belong to the same milestone

## Why this example matters

This worked example shows the DERRR pattern:
- document before execution
- use one narrow slice at a time
- let review invalidate weak hypotheses
- use research to identify the next real question
- restart explicitly rather than smearing the next slice into the last one
