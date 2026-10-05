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

# Business rules — GAMES

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-GAMES-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
