---
kb_section: backend
type: service
ids: [BE-SVC-REWARD]
service: REWARD
repo: TZ-Tigo-SuperApp-RewardReferral
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: b47cb93
updated: 2026-10-05
confidence: partial
---

# Integrations — REWARD

Hosts/secrets omitted.

| ID | Name | How | Evidence |
|---|---|---|---|
| BE-INT-REWARD-001 | HttpClient `CMM` | named client; base URL from config key (value omitted) | Program/DI |
| BE-INT-REWARD-002 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}` | outbound HTTP path shape | static string |
| BE-INT-REWARD-003 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}/{service}/{serviceMethod}` | outbound HTTP path shape | static string |
