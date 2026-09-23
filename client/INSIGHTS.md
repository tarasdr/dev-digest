# Insights — client

Non-obvious facts learned the hard way. One bullet each, dated. Delete when stale.

- **2026-09-23 · Contract copy** — `src/vendor/shared` is a copy of
  `server/src/vendor/shared` and has already drifted (e.g. `sessionId` exists only on
  the server's `LLMProvider` options). Check the server copy before trusting a type here.
- **2026-09-23 · Future-lesson messages** — `messages/en` already has files for later
  lessons (blast, brief, ci, conventions…). They are placeholders, not dead strings.
