---
kb_section: backend
type: service
ids: [BE-SVC-ACCOUNT]
service: ACCOUNT
repo: TZ-Tigo-SuperApp-Account
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 5c549d6
updated: 2026-10-05
confidence: partial
---

# Integrations — ACCOUNT

Hosts/secrets omitted.

| ID | Name | How | Evidence |
|---|---|---|---|
| BE-INT-ACCOUNT-001 | HttpClient `CMM` | named client; base URL from config key (value omitted) | Program/DI |
| BE-INT-ACCOUNT-002 | HttpClient `SMM` | named client; base URL from config key (value omitted) | Program/DI |
| BE-INT-ACCOUNT-003 | `api/Account/auth` | outbound HTTP path shape | static string |
| BE-INT-ACCOUNT-004 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}` | outbound HTTP path shape | static string |
| BE-INT-ACCOUNT-005 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}/{service}/{serviceMethod}` | outbound HTTP path shape | static string |
