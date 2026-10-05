---
kb_section: backend
type: service
ids: [BE-SVC-SESS]
service: SESS
repo: TZ-Tigo-SuperApp-Session
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 6f24061
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-SESS business rules

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-SESS-001 | Session JWT is bound to msisdn + deviceid | session | AccountController.Auth | JwtExpiryMins | auth | confirmed |
| BE-BR-SESS-002 | Refresh requires matching stored refresh token, access token, and unexpired refresh | session | Refresh | JwtRefreshExpiryMins | refreshToken | confirmed |
| BE-BR-SESS-003 | Auth refuses unknown msisdn via profile CheckAuthenticationAsync | eligibility | Auth | — | auth | confirmed |

