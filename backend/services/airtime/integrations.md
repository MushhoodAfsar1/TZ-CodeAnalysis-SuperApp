---
kb_section: backend
type: service
ids: [BE-SVC-AIRTIME]
service: AIRTIME
repo: TZ-Tigo-SuperApp-AirTimeTopup
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 7a52359
updated: 2026-10-05
confidence: partial
---

# Integrations — AIRTIME

Hosts/secrets omitted.

| ID | Name | How | Evidence |
|---|---|---|---|
| BE-INT-AIRTIME-001 | HttpClient `CMM` | named client; base URL from config key (value omitted) | Program/DI |
| BE-INT-AIRTIME-002 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}` | outbound HTTP path shape | static string |
| BE-INT-AIRTIME-003 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}/{service}/{serviceMethod}` | outbound HTTP path shape | static string |
