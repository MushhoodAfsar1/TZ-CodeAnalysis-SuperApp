---
kb_section: backend
type: service
ids: [BE-SVC-MERSET]
service: MERSET
repo: TZ-Tigo-SuperApp-MerchantSettlementScheduler
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: d638213
updated: 2026-10-05
confidence: partial
---

# Integrations — MERSET

Hosts/secrets omitted.

| ID | Name | How | Evidence |
|---|---|---|---|
| BE-INT-MERSET-001 | HttpClient `CMM` | named client; base URL from config key (value omitted) | Program/DI |
| BE-INT-MERSET-002 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}/{service}/{serviceMethod}` | outbound HTTP path shape | static string |
