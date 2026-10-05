---
kb_section: backend
type: service
ids: [BE-SVC-EXTPAY]
service: EXTPAY
repo: TZ-Tigo-SuperApp-ExternalPayment
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 51718e1
updated: 2026-10-05
confidence: partial
---

# Errors — EXTPAY

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-EXTPAY-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-EXTPAY-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
