# Insights — project-wide

Non-obvious facts learned the hard way. One bullet each, dated. Delete when stale.
Package-specific insights go in `<package>/INSIGHTS.md`.

- **2026-09-23 · No workspace** — packages link through tsconfig `paths` to raw `.ts`
  source, not published modules. `reviewer-core` resolves `@devdigest/shared` from
  `../server/src/vendor/shared`, so the engine depends on a folder inside the server.
- **2026-09-23 · Shared contracts drift** — `server/src/vendor/shared` and
  `client/src/vendor/shared` are manual copies and already differ (`adapters.ts`,
  `contracts/trace.ts`, `eval-ci.ts`, `knowledge.ts`, `productionize.ts`). Diff them
  before relying on a field existing on both sides.
- **2026-09-23 · Duplicate zod instances** — each package has its own `zod`, so
  `instanceof ZodError` can fail across packages. `reviewer-core` pins `zod` to its own
  `node_modules`; `server/src/app.ts` also detects ZodError by shape.
- **2026-09-23 · Lesson placeholders** — the DB schema, shared contracts and
  `client/messages/en` already contain entities for later lessons (eval, ci, skills,
  knowledge…). Empty tables and unused contracts are expected, not dead code.
- **2026-09-23 · Task tags** — code comments use tags like `T1.3`, `T3`, `F1`. They are
  internal task IDs, not course lesson numbers.
