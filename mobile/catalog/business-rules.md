---
kb_section: mobile
type: catalog
ids: [FE-CAT-BR]
service: ALL
repo: TZ-Tigo-SuperApp-Mobile
repo_ref: main
repo_sha: 6328b7254
be_kb_ref: cursor/frontend-mobile-api-analysis-ad82
be_kb_sha: 2655b7a
updated: 2026-10-05
confidence: confirmed
---

# Business rules index

Detail lives in the service file. This table is the index only.

| FE-BR | Rule | Alignment | Detail |
|---|---|---|---|
| FE-BR-SESS-001 | Refresh the session only in the last 35 seconds before refresh-token expiry, and only when the access JWT is already expired. | fe-only | [SESS rules](../services/sess/business-rules.md) |
| FE-BR-SESS-002 | After refresh-token expiry, go to login and do not call refresh. | fe-only | [SESS rules](../services/sess/business-rules.md) |
| FE-BR-SESS-003 | Skip refresh during logout. A missing or undecodable access token goes to login. A guest session is left in place. | fe-only | [SESS rules](../services/sess/business-rules.md) |
| FE-BR-SESS-004 | HTTP 410 refreshes the session and retries the original call, at most twice on that chain. | both (`BE-ERR-SESS-002`; the cap is fe-only) | [SESS rules](../services/sess/business-rules.md) |
| FE-BR-SESS-005 | HTTP 411 sends the logged-in user to login. | fe-only | [SESS rules](../services/sess/business-rules.md) |
| FE-BR-SESS-006 | Pointer and resume checks run only while `isLoggedIn` is true. | fe-only | [SESS rules](../services/sess/business-rules.md) |
| FE-BR-SESS-007 | Session expiry replaces the stack with login. The session-expired copy is not shown. | fe-only | [SESS rules](../services/sess/business-rules.md) |
