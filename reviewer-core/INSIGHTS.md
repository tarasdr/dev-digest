# Insights — reviewer-core

Non-obvious facts learned the hard way. One bullet each, dated. Delete when stale.

- **2026-09-23 · Pinned zod** — `tsconfig.json` maps `zod` to `./node_modules/zod` so the
  shared contracts (which live under `server/`) and the engine use the same zod instance.
- **2026-09-23 · Map-reduce trigger** — `strategy: 'auto'` switches to per-file
  map-reduce only when the diff is over 400 changed lines AND touches more than one file.
- **2026-09-23 · Unused slots** — `skills`, `memory`, `specs` and `toReviewPayload` exist
  for later lessons; the starter server passes only diff, system prompt, repo map and
  callers.
- **2026-09-23 · Cost can be null** — `costUsd` becomes `null` if any chunk's provider
  can't price the call; treat it as "unknown", not zero.
