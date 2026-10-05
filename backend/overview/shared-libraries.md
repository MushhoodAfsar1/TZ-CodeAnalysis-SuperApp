---
kb_section: backend
type: overview
ids: [BE-OV-SHR]
service: ALL
repo: multi
repo_ref: checked-out
repo_sha: multi
updated: 2026-10-05
confidence: confirmed
---

# Shared libraries

There is **no** shared NuGet/project (`Common`/`Crypto`) across the 29 repos. Filters, `RequestSecurity`, `BaseResponse`, `ApiResponseHandler`, and `RabbitMQConnectionHelper` are **copied per service**.

`Shared.Entities.FCM` is a duplicated namespace, not a shared assembly.

HttpClient names: `CMM` (CONFIG), `SMM` (Session, Account only), `IdentityApi` (CONFIG → Identity).
