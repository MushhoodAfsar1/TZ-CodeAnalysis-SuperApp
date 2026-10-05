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

# Integrations — RESERV

Hosts/secrets omitted.

| ID | Name | How | Evidence |
|---|---|---|---|
| BE-INT-RESERV-001 | HttpClient `CMM` | named client; base URL from config key (value omitted) | Program/DI |
| BE-INT-RESERV-002 | HttpClient `proxyClient` | named client; base URL from config key (value omitted) | Program/DI |
| BE-INT-RESERV-003 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}` | outbound HTTP path shape | static string |
| BE-INT-RESERV-004 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}/{service}/{serviceMethod}` | outbound HTTP path shape | static string |
