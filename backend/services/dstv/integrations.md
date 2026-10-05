---
kb_section: backend
type: service
ids: [BE-SVC-DSTV]
service: DSTV
repo: TZ-Tigo-SuperApp-DigitalSubscription
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: fd31aa1
updated: 2026-10-05
confidence: partial
---

# Integrations — DSTV

Hosts/secrets omitted.

| ID | Name | How | Evidence |
|---|---|---|---|
| BE-INT-DSTV-001 | HttpClient `CMM` | named client; base URL from config key (value omitted) | Program/DI |
| BE-INT-DSTV-002 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}` | outbound HTTP path shape | static string |
| BE-INT-DSTV-003 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}/{service}/{serviceMethod}` | outbound HTTP path shape | static string |
