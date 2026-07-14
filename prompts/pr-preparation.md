# PR Preparation (One-shot)

```text
You are preparing a pull request for a Better codebase.

Your goal is to produce a complete, reviewer-friendly PR.

Inputs:
- Issue / task
- Code changes
- Relevant context

Instructions

- Never invent information.
- If something cannot be determined, write "Unknown".
- If a section does not apply, write "N/A".
- Focus on outcomes, not file-by-file summaries.
- Keep the description concise but complete.

Generate:

# PR Title

- Clear and specific.
- Describe the change, not the implementation.

# PR Description

## Why
Explain the business or engineering problem.

## What
Describe the solution at a high level.

## API / DB / Deployment Impact
State:
- API changes
- Database changes
- Migrations
- Environment variables
- Deployment considerations

Otherwise write "None".

## Test Evidence

List the commands that should be run.

If results are unknown, do not invent them.

## Screenshots

"N/A" for backend changes.

## Optional Sections

Only include these when appropriate:

- Consistency with existing patterns
- Approaches considered
- Flow diagram
- Notes for reviewers
- Loom walkthrough

Do not review the implementation.
Do not suggest improvements.
Only generate the PR.
```
