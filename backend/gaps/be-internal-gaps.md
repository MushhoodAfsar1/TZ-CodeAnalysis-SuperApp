---
kb_section: backend
type: gap
ids: [BE-GAP-001, BE-GAP-002, BE-GAP-003, BE-GAP-004, BE-GAP-005, BE-GAP-006, BE-GAP-007, BE-GAP-008, BE-GAP-009, BE-GAP-010]
service: ALL
repo: multi
repo_ref: checked-out
repo_sha: multi
updated: 2026-10-05
confidence: confirmed
---

# BE internal gaps

| ID | Type | Description | Evidence | Impact | Severity | Suggested owner | Status |
|---|---|---|---|---|---|---|---|
| BE-GAP-001 | unknown-dispatch | No gateway/BFF repo; public URLs may differ from controller routes | workspace has 29 services only | FE match keys may need gateway overlay | high | platform | open |
| BE-GAP-002 | duplicate-logic | Crypto/filters/ApiResponseHandler copied per repo | each `Filters/`, `Helpers/RequestSecurity.cs` | drift (typo Encription*, is_encrypted vs isEncrypted) | medium | architecture | open |
| BE-GAP-003 | missing-auth | CONFIG registers JWT but Program lacks `UseAuthentication` | CONFIG Program.cs | portal JWT may not run | high | CONFIG | open |
| BE-GAP-004 | missing-auth | MChango `UseAuthentication` without `AddAuthentication` | MChango Program.cs | middleware no-op / fail | high | MCHANGO | open |
| BE-GAP-005 | undocumented-behaviour | Notification `FCMNotificationConsumer` has no MassTransit bus in Program.cs | NOTIF Program.cs vs Consumers/ | consumer never runs | medium | NOTIF | open |
| BE-GAP-006 | dead-endpoint | Many `enc`/`dec` helper actions appear unauthenticated | controllers named enc/dec/encrypt/decrypt | crypto oracle risk if exposed | high | each service | open |
| BE-GAP-007 | inconsistent-error-model | Session filter uses `errordescription`; handler uses `errorDescription`; 410 vs 400 | SessionValidationFilter vs ApiResponseHandler | FE branching | medium | platform | open |
| BE-GAP-008 | spec-vs-code-mismatch | Reservation CreateClient("CMM") without named client registration | Reservation Program.cs | runtime failure on response mapping | medium | RESERV | open |
| BE-GAP-009 | spec-vs-code-mismatch | CONFIG 432 `[Http*]` vs 430 first-pass files: leftovers are public `BannerController.Create` / `Update` (`[HttpPost("…"), DisableRequestSizeLimit]`). Now filed as BE-API-CONFIG-431/432 | CONFIG `BannerController.cs` | parser miss, not unbound methods | low | CONFIG | closed 2026-10-05 |
| BE-GAP-010 | spec-vs-code-mismatch | SEND `VerifySendMoneyRequest` DTO field `useCaseName` vs repository `request.userCaseName` | SendMoneyRepository.VerifySendMoney | rail selection may ignore use case | medium | SEND | open |
