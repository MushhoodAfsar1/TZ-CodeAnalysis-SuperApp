---
kb_section: backend
type: service
ids: [BE-SVC-RESERV]
service: RESERV
repo: TZ-Tigo-SuperApp-Reservation
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: dfd072a
updated: 2026-10-05
confidence: partial
---

# Errors — RESERV

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-RESERV-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-RESERV-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
