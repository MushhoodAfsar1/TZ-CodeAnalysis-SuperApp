---
kb_section: backend
type: service
ids: [BE-SVC-WALLET]
service: WALLET
repo: TZ-Tigo-SuperApp-Wallet
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 27737b1
updated: 2026-10-05
confidence: partial
---

# Errors — WALLET

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-WALLET-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-WALLET-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
