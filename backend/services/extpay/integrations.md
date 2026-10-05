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

# Integrations — EXTPAY

Hosts/secrets omitted.

| ID | Name | How | Evidence |
|---|---|---|---|
| BE-INT-EXTPAY-001 | HttpClient `CMM` | named client; base URL from config key (value omitted) | Program/DI |
| BE-INT-EXTPAY-002 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}` | outbound HTTP path shape | static string |
| BE-INT-EXTPAY-003 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}/{service}/{serviceMethod}` | outbound HTTP path shape | static string |
