---
kb_section: backend
type: service
ids: [BE-SVC-WALLET]
service: WALLET
repo: TZ-Tigo-SuperApp-Wallet
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 27737b1
updated: 2026-10-05
confidence: partial
---

# Integrations — WALLET

Hosts/secrets omitted.

| ID | Name | How | Evidence |
|---|---|---|---|
| BE-INT-WALLET-001 | HttpClient `CMM` | named client; base URL from config key (value omitted) | Program/DI |
| BE-INT-WALLET-002 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}` | outbound HTTP path shape | static string |
| BE-INT-WALLET-003 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}/{service}/{serviceMethod}` | outbound HTTP path shape | static string |
