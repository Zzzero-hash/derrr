# DERRR Formal Design

## Status

This document defines the DERRR method as a formal design.
It is still pre-packaging and pre-SKILL, but the core mechanics are treated as stable enough to specify directly.

## 1. Purpose

DERRR is a hypothesis-driven improvement method for live or semi-live agent systems.

Its purpose is to improve agent behavior in a way that is:
- narrow in scope
- auditable
- restartable
- human-controlled
- resistant to drift

DERRR is intended for situations where:
- failures may appear at multiple layers
- speculative iteration is risky
- correctness and observability matter
- tuning should be deferred until behavior is trustworthy

## 2. Core Loop

DERRR stands for:
- Document
- Execute
- Review
- Research
- Restart

The loop is not merely mnemonic. Each phase has a distinct control role.

- **Document** establishes control state before action.
- **Execute** performs one narrow action aligned to that control state.
- **Review** determines the direct effect of the action.
- **Research** investigates unresolved behavior or competing explanations.
- **Restart** closes the current slice explicitly and creates a clean successor state.

## 3. Design Principles

### 3.1 Narrowness over throughput

DERRR optimizes for trustworthy iteration, not raw speed.
A narrow slice is preferable to a broad speculative change.

### 3.2 Source-of-truth explicitness

The control surface for the current loop must be explicit.
The source of truth cannot remain implicit in chat history alone.

### 3.3 Layered observability

A symptom must be traced across the layers where it can appear.
DERRR treats observability as a first-class design concern, not a debugging afterthought.

### 3.4 Human control

The user remains the operator.
Agent helpers, reviewers, or workers may assist, but they do not replace the control layer.

### 3.5 Explicit closure

A slice is not complete because the team has mentally moved on.
Closure and successor creation must be explicit.

### 3.6 Anti-drift discipline

DERRR forbids scope expansion by implication.
Each new frontier requires a new slice.

## 4. Canonical Terms

DERRR uses three core scope units.

### 4.1 Milestone

A milestone is the current broader frontier of correctness or capability.
It defines the outer boundary of the present work.

### 4.2 Slice

A slice is the narrow unit of work within a milestone.
A slice should be small enough that its hypothesis, target evidence, and boundaries can be stated clearly.

### 4.3 Phase

A phase is the current state of a slice inside the DERRR loop.
Phases are not independent work items. They are control states of the active slice.

### 4.4 Nesting model

The nesting model is:
- milestone
  - slice
    - phase transitions through DERRR

## 5. Slice Contract

Every slice must define:
- narrow question
- current hypothesis
- execution boundary
- evidence target
- success condition
- failure or invalidation condition
- expected restart rule

A slice may be observational, implementation-oriented, research-oriented, review-oriented, or decision-oriented, but it should have one dominant type.

## 6. Slice Types

Primary slice types:
- observation
- implementation
- soak/review
- research
- decision

This classification exists to prevent mixed, mushy work.
If a slice is doing too many things at once, it should be split.

## 7. Observability Model

### 7.1 Observability ladder

DERRR uses the following observability ladder:
1. Prompt or contract layer
2. Raw response layer
3. Parsed output layer
4. Accepted or validated output layer
5. Persisted artifact layer
6. Runtime behavior layer
7. Aggregate or soak layer

### 7.2 Governing question

The primary observability question is:
- where did the failure first become visible?

Secondary questions include:
- where did the failure likely originate?
- what layer is masking or reshaping the problem?
- are logs, counters, and artifacts aligned?
- is the store faithfully representing the failure path?

### 7.3 Evidence classes

DERRR distinguishes between:
- **direct evidence**: evidence that speaks directly to the slice hypothesis
- **suggestive evidence**: evidence that points in a direction but does not yet settle the claim
- **aggregate evidence**: evidence gathered across a soak or broader sample window
- **control evidence**: evidence about the loop itself, such as missing artifacts, audit gaps, or control-state mismatch

## 8. Phase Specifications

## 8.1 Document

### Objective
Establish the control state of the active slice before execution begins.

### Required outputs
- source of truth selected
- active slice recorded
- milestone boundary acknowledged
- hypothesis recorded
- evidence target recorded
- execution boundary recorded
- success/failure conditions recorded

### Allowed operations
- create or update slice record
- identify metrics and evidence sources
- capture assumptions and blockers
- clarify milestone alignment

### Forbidden operations
- implementation before documentation exists
- invisible scope broadening
- skipping the source-of-truth decision

### Exit criterion
The slice exists in the control surface with enough specificity that another operator could understand what is being tested.

## 8.2 Execute

### Objective
Perform one narrow action aligned to the slice.

### Allowed operations
- instrumentation
- narrow implementation
- bounded measurement setup
- constrained config change
- bounded helper-agent delegation

### Forbidden operations
- unrelated cleanup
- opportunistic refactor
- tuning while correctness is unresolved
- speculative multi-patch chaining

### Exit criterion
One bounded action has been performed and is ready for direct review.

## 8.3 Review

### Objective
Determine what the last execution step actually did.

### Allowed operations
- review logs and artifacts
- compare before and after states
- measure the direct target effect
- capture anomalies
- decide whether separate soak is needed

### Forbidden operations
- treating weak evidence as closure
- patching again before acknowledging outcome
- silently converting review into research or execution

### Exit criterion
The operator has a direct read on the effect of the last action and can classify the result as sufficient, insufficient, or anomalous.

## 8.4 Research

### Objective
Investigate unresolved behavior, rival explanations, or next-bottleneck questions.

### Allowed operations
- trace code paths
- compare hypotheses
- correlate logs, counters, and artifacts
- use bounded third-party reviewers or helper agents
- perform targeted documentation lookup

### Forbidden operations
- implementation disguised as “just checking”
- broad adjacent investigation with no slice update
- helper-agent conclusions treated as control-layer truth without review

### Exit criterion
The operator either has enough evidence to open a new implementation slice or has learned that the current frontier remains unresolved and needs a further research slice.

## 8.5 Restart

### Objective
Close the current slice explicitly and create the next clean control state.

### Allowed operations
- close slice
- summarize what was learned
- create explicit successor slice
- update milestone alignment
- reset active control state

### Forbidden operations
- implied continuation without a restart artifact
- closing only in conversation and not in the source of truth
- beginning a new frontier under the old slice

### Exit criterion
The old slice is explicitly closed, blocked, or invalidated, and any next slice exists as a new control object.

## 9. Why Restart Is Its Own Phase

Restart is intentionally distinct from Review and Research.

Without Restart, teams tend to:
- imply the next slice without recording it
- blur closure into the next implementation burst
- carry hidden assumptions forward
- lose milestone alignment

Restart is therefore a control boundary, not administrative polish.
It is the phase that preserves the narrowness and cleanliness of the loop.

## 10. Human Control Model

### 10.1 Operator role

The human is the operator of the loop.
The agent assists within the loop but does not become the control authority.

### 10.2 Control checkpoints

Human confirmation is especially important before:
- changing the source of truth
- broadening scope
- moving from research into implementation when risk is meaningful
- closing milestone-level work
- using public or external systems
- introducing helper agents whose behavior changes cost, risk, or complexity

### 10.3 Constraint-setting

Human answers should become explicit loop constraints.
Examples:
- markdown-only mode
- strict audit mode
- helpers allowed or disallowed
- one-slice-only enforcement
- separate soak-slice preference
- speed-biased versus audit-biased posture

## 11. Control Surfaces

DERRR is method-first.
The control surface may change without changing the method itself.

## 11.1 Vault Mode

Control surface:
- Obsidian vault or similar note graph

Target user:
- note-first operator
- low-infrastructure individual user

Suggested structure:
- DERRR/Active Slice.md
- DERRR/Milestones.md
- DERRR/Research Log.md
- DERRR/Slices/

## 11.2 Plain Markdown Mode

Control surface:
- markdown files in repo or working directory

Target user:
- git-native user
- lightweight repo-centric workflow

Suggested structure:
- derrr/active.md
- derrr/milestones.md
- derrr/research.md
- derrr/slices/

## 11.3 Plane Full Mode

Control surface:
- Plane issues, states, modules, and comments

Target user:
- operational team or persistent multi-slice workflow

Important rule:
- Plane is a full installation mode, not a universal dependency of DERRR.

## 12. In-Phase Infrastructure

DERRR becomes powerful when infrastructure exists inside the phases.

### 12.1 Document infrastructure
Should eventually include:
- active slice template
- milestone note template
- source-of-truth declaration
- hypothesis and evidence blocks

### 12.2 Execute infrastructure
Should eventually include:
- execution checklist
- instrumentation-versus-implementation guidance
- helper-agent delegation rules
- assumption capture block

### 12.3 Review infrastructure
Should eventually include:
- sample window guidance
- before/after comparison format
- anomaly capture block
- closure threshold prompts

### 12.4 Research infrastructure
Should eventually include:
- rival hypothesis worksheet
- log/artifact correlation prompts
- helper-agent evidence handling rules
- audit-gap checks

### 12.5 Restart infrastructure
Should eventually include:
- closure note template
- restart note template
- successor slice template
- milestone alignment note template

## 13. Anti-Drift Rules

DERRR should encode explicit anti-drift rules, including:
- do not execute before the slice is documented
- do not tune while correctness is unresolved
- do not broaden scope mid-slice without updating the control state
- do not treat helper agents as control-layer replacements
- do not imply successor work only in chat
- do not close a slice mentally without recording it

## 14. Method Failure Modes

DERRR should acknowledge when the method itself is the wrong fit.

It is likely too heavy when:
- the task is a simple one-file fix with clear cause and trivial validation
- the work is pure feature construction with no live behavioral uncertainty
- the user explicitly wants rapid exploratory prototyping over auditability
- the overhead of phase control exceeds the value of the improvement loop

## 15. Lessons Incorporated from Real Iteration

The formal design incorporates these operational lessons:
- document before execution
- keep the source of truth explicit
- separate persistence symptoms from upstream causes
- distinguish schema or correctness work from tuning work
- use soak or review as distinct slices when necessary
- bounded helper agents can be powerful when they remain subordinate to the control layer
- measured evidence beats “seems better”
- a fix can expose a new bottleneck without invalidating the value of the prior fix
- correctness gains that reduce auditability can still remain within the same milestone frontier

## 16. Non-Goals

DERRR does not attempt to be:
- a universal software process
- a replacement for product specification
- a replacement for CI/CD
- a generic debugging skill for every bug
- a benchmark or tuning framework

## 17. Future Packaging Boundary

This formal design is richer than an eventual SKILL.md should be.

When packaged as a skill, the design should be reduced into:
- a concise SKILL.md
- mode-specific reference docs
- concrete templates and examples
- explicit trigger and skip boundaries

## 18. Positioning

### One-line positioning

DERRR is a hypothesis-driven improvement method for live agent systems that combines slice discipline, layered observability, and phase control to make iteration auditable, narrow, and restartable.

### Short pitch

Spec-driven development tells you what to build.
DERRR tells you how to improve a live agent system without drifting into guesswork.
