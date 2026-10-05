---
kb_section: backend
type: service
ids: [BE-SVC-EXPENSE]
service: EXPENSE
repo: TZ-Tigo-SuperApp-Expense
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: e821ac9
updated: 2026-10-05
confidence: partial
---

# Integrations — EXPENSE

Hosts/secrets omitted.

| ID | Name | How | Evidence |
|---|---|---|---|
| BE-INT-EXPENSE-001 | HttpClient `CMM` | named client; base URL from config key (value omitted) | Program/DI |
| BE-INT-EXPENSE-002 | HttpClient `SSL` | named client; base URL from config key (value omitted) | Program/DI |
| BE-INT-EXPENSE-003 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}` | outbound HTTP path shape | static string |
| BE-INT-EXPENSE-004 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}/{service}/{serviceMethod}` | outbound HTTP path shape | static string |
