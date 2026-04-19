# Active Slice Example

## Milestone
- Make candidate generation behavior auditable and trustworthy before tuning.

## Slice Title
- Determine whether raw role outputs are missing structured action fields before parse.

## Slice Type
- observation

## Current Phase
- Document

## Narrow Question
- Are `policy_action` and `candidate_actions` disappearing in the parser, or are models omitting them in raw output?

## Current Hypothesis
- The models are omitting these fields because the debate prompt contract does not require them.

## Evidence Target
- Raw response audit logging before parse for bull, bear, and judge role outputs.

## Execution Boundary
- Instrumentation only. No policy changes, no validator changes, no prompt changes in this slice.

## Success Condition
- We can tell whether the missing fields are absent in raw output or lost later during parse/validation.

## Failure or Invalidation Condition
- The instrumentation does not capture enough raw boundary detail to distinguish omission from parser loss.

## Restart Rule
- If this slice succeeds:
  - open a successor slice for the first proven upstream cause.
- If this slice fails or is invalidated:
  - open a narrower instrumentation slice focused on the missing observability layer.

## Notes
- This slice exists to avoid changing prompts or validators based on guesswork.
- If raw output already lacks the fields, the parser is not the main culprit.
