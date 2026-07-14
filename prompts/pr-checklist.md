# PR Checklist — Better

Reference prompt for preparing or self-reviewing a pull request at Better.
Paste into any agent or use as a checklist manually.

---

You are preparing a pull request for a Better codebase. Walk through every
section below. If a section does not apply, write "N/A" — never leave it
blank.

## 1. Branch & Commits

- Branch named `author/type/description` (e.g. `udit/fix/login-timeout`).
- Commits: `type: description` (≤50 chars), imperative mood ("Add" not "Added").
- Types: `feat` · `fix` · `chore` · `refactor` · `docs` · `test` · `perf` · `ci`.
- One logical change per PR. If you have two unrelated changes, split into two PRs.
- Raise or update PRs daily when possible.

## 2. PR Title

- Clear, specific description of what changed.
- Good: "Add email login functionality".
- Bad: "Update login stuff", "Fix bugs", "WIP".

## 3. PR Description — Required

Every PR must have these, filled in completely:

- **Why** — the business or operator problem. Not "refactored X", but "users
  were hitting a timeout on login because Y, which blocks Z".
- **What** — outcomes and high-level design. Not a file list.
- **API / DB / Deployment impact** — write "None" if none. Call out new
  endpoints, schema changes, migration needs, environment variable changes.
- **Test evidence** — exact commands run and their results. Not "tested
  locally". Show: `pytest tests/test_login.py — 12 passed, 0 failed`.
- **Screenshots** — UI changes get screenshots or screen recordings.
  Backend-only changes: write "N/A".

## 4. PR Description — When Warranted

Add these sections when the change is non-trivial:

- **Consistency** — how this fits existing patterns in the codebase.
- **Approaches considered** — for design forks. Name rejected alternatives
  and why. Skip if the change is obvious.
- **Flow diagram** — Mermaid or text when the interaction path is hard to
  follow from code alone.
- **Notes for reviewers** — SOC2, security, audit concerns, scope boundaries.
- **Loom video** — for feature PRs. Label what the video demonstrates.

## 5. Stacked / Slice PRs

When splitting one issue across PRs:

- State "part N of M" and link the parent issue.
- **Not in this slice** — explicit exclusions to stop scope creep questions.
- **Depends on** — name the base PR or branch.
- **How to review** — ordered entry points into the diff.

## 6. Meta

- Assignee = yourself.
- Labels set (feature, bug, documentation, etc.).

## 7. Self-Review (MANDATORY before requesting review)

This catches 90% of issues before wasting reviewer time:

- [ ] **Line-by-line diff review** — pretend you're reviewing someone else's code.
- [ ] **Tests pass** — your change works AND existing related behavior is not broken.
- [ ] **PR template complete** — every required section filled in.
- [ ] **Loom recorded** — when it saves reviewer time (feature PRs).
- [ ] **Automated tests added** — backend PRs must have test coverage for new behavior.
- [ ] **Cleanup** — no debug code, console.log, dead code, commented-out blocks, stale TODO comments.
- [ ] **Prior feedback addressed** — every review thread from previous rounds resolved.
- [ ] **Lint and typecheck pass** — run the project's lint/typecheck commands.
- [ ] **Zero `Any` types** — use the real type (model, dataclass, `dict[str, str]`, `list[int]`). Unknown boundary data → `object`, never `Any`. No `# type: ignore` either.

## 8. AI-Assisted Changes

If an agent (Cursor, Codex, Hermes, etc.) touched the branch:

- Post a comment summarizing what the agent changed and why.
- List what was verified statically vs what needs a human runtime check.
- Call out design choices deliberately left as-is.
- Author must re-review and verify in the app. Do not merge on the agent's
  word alone.

## 9. After Review

- Eng review complete.
- PM Acceptance on PR before merge to production (for feature PRs).
- All reviews and feedback submitted within the PR on GitHub, not in DMs.
- Deploy to staging, verify before production.
- Sprint exit: demo on staging from a business standpoint.
- For bug fixes: after production deploy, verify and notify the reporter.

## 10. Communication Norms

- Give reviewers ~24 hours before nudging. Follow up if blocking other work.
- Daily status update (PPP) should reference the PR with a hyperlink.
- When stuck: push your changes, raise a PR, THEN ask for help with context.
  Never just say "I'm stuck at XXX" — show what you tried.

## 11. Instant Reject Conditions

These get a PR sent back immediately:

- Incomplete or empty description.
- Multiple unrelated logical changes in one PR.
- Debug noise left in (console.log, debugger, print statements).
- No test evidence.
- Prior review feedback ignored.
- `Any` type or `# type: ignore` anywhere in the PR diff.

---

## Gold Standard

[operate #482](https://github.com/jalantechnologies/operate/pull/482) —
"feat: turn database monitoring on or off, per connection"

Why it works: explains current system, what changes, what it doesn't cover,
rejected alternatives with reasons, Mermaid flow diagram, SOC2 callout,
exact test commands, Loom walkthroughs. Read it before writing your next PR.

---

## Sources

- `~/Workspace/Better/handbook/engineering/pr-etiquette.md`
- `~/Workspace/Better/handbook/engineering/index.md`
- `~/Workspace/Better/handbook/engineering/lead.md`
- `~/Workspace/Better/handbook/product-management/index.md`
- `~/Workspace/Better/handbook/common/working_at_better.md`
- `~/.hermes/skills/better-pr-review/` (PR body tiers, gold standard breakdown)
