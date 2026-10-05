---
kb_section: backend
type: service
ids: [BE-SVC-INSUR]
service: INSUR
repo: TZ-Tigo-SuperApp-Insurrance
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 38747da
updated: 2026-10-05
confidence: partial
---

# Integrations — INSUR

Hosts/secrets omitted.

| ID | Name | How | Evidence |
|---|---|---|---|
| BE-INT-INSUR-001 | HttpClient `CMM` | named client; base URL from config key (value omitted) | Program/DI |
| BE-INT-INSUR-002 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}` | outbound HTTP path shape | static string |
| BE-INT-INSUR-003 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}/{service}/{serviceMethod}` | outbound HTTP path shape | static string |
