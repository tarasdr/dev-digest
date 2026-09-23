# Insights — e2e

Non-obvious facts learned the hard way. One bullet each, dated. Delete when stale.

- **2026-09-23 · `specs/` is executable** — unlike other packages, `e2e/specs/` holds
  runnable `*.flow.json` files. Written test plans go in `test-plans/`.
- **2026-09-23 · Assertions are waits** — `wait --text` / `wait --url` time out and exit
  non-zero, which fails the step; that is the assertion mechanism.
- **2026-09-23 · First-repo redirect** — flow 02 follows the home redirect to the first
  repo, so any extra imported repo in the DB breaks it. Use the hermetic runner.
