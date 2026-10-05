---
kb_section: backend
type: service
ids: [BE-SVC-GAMES]
service: GAMES
repo: TZ-Tigo-SuperApp-Games
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 10c8daa
updated: 2026-10-05
confidence: partial
---

# Errors — GAMES

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-GAMES-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-GAMES-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
