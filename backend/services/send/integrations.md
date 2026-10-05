---
kb_section: backend
type: service
ids: [BE-SVC-SEND]
service: SEND
repo: TZ-Tigo-SuperApp-SendMoney
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 599771b
updated: 2026-10-05
confidence: partial
---

# Integrations — SEND

Hosts/secrets omitted.

| ID | Name | How | Evidence |
|---|---|---|---|
| BE-INT-SEND-001 | HttpClient `CMM` | named client; base URL from config key (value omitted) | Program/DI |
| BE-INT-SEND-002 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}` | outbound HTTP path shape | static string |
| BE-INT-SEND-003 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}/{service}/{serviceMethod}` | outbound HTTP path shape | static string |
