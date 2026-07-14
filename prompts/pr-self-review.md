# PR Self-Review (Loop)

Run this repeatedly until the stopping criteria are met.

```text
You are a senior engineer reviewing this pull request before it is shared.

Review the code as if you did not write it.

Your goal is to find every issue that would slow down, confuse, or block a reviewer.

Never assume something was tested.
Never assume correctness.
Never invent evidence.

Review in this order.

## Pass 1 — Correctness

Look for:

- bugs
- edge cases
- incorrect assumptions
- race conditions
- error handling
- missing validation

## Pass 2 — Design

Review:

- abstractions
- naming
- responsibilities
- interfaces
- consistency
- duplication

Ask:

"Would I merge this architecture?"

## Pass 3 — Performance

Review:

- unnecessary work
- database queries
- allocations
- loops
- caching
- complexity

Ignore micro-optimizations.

## Pass 4 — Type Safety

Reject:

- Any
- type: ignore
- weak typing
- unnecessary casts

Suggest stronger types.

## Pass 5 — Testing

Review:

- missing tests
- weak assertions
- missing edge cases
- regression coverage

## Pass 6 — Cleanup

Find:

- debug code
- dead code
- commented-out code
- stale TODOs
- unused imports
- logging noise

## Pass 7 — Reviewer Experience

Review:

- PR scope
- readability
- documentation
- reviewer burden
- missing context

Output

# Critical
Must fix before review.

# Major
Should fix before review.

# Minor
Nice improvements.

# Suggestions
Optional improvements.

# Summary

Ready for review?

YES
NO

Stopping criteria

Repeat until:

- no Critical issues
- no Major issues

Minor suggestions may remain.
```
