# Insights — server

Non-obvious facts learned the hard way. One bullet each, dated. Delete when stale.

- **2026-09-23 · Single instance only** — `RunBus` (live log, cancellation) and
  `JobRunner` (p-queue) live in process memory. On boot, `app.ts` marks every
  `running` agent run as failed. Running two API instances against one DB breaks this.
- **2026-09-23 · Seed is required** — `LocalNoAuthProvider` always resolves the seeded
  system user and workspace; without `pnpm db:seed` requests fail with
  "No system user found".
- **2026-09-23 · Re-export shims** — `platform/grounding.ts`, `prompt.ts` and
  `structured.ts` only re-export from `@devdigest/reviewer-core`. Import from the engine
  directly in new code.
- **2026-09-23 · Static module registry** — `@fastify/autoload` is a dependency, but
  modules are registered statically in `modules/index.ts` because dynamic `import()` of
  `.ts` files doesn't behave the same under tsx, bundlers and vitest.
- **2026-09-23 · Two LLM homes** — OpenAI and Anthropic providers live in
  `adapters/llm`, OpenRouter lives in `reviewer-core`. Pricing comes from the live
  `PriceBook` with `adapters/llm/pricing.ts` as fallback.
- **2026-09-23 · Review runs are fire-and-forget** — the review route queues runs and
  returns; `ReviewRunExecutor` runs agents sequentially in the background and reports
  progress over SSE.
