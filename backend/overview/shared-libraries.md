---
kb_section: backend
type: overview
ids: [BE-OVR-SHR]
service: ALL
repo: multi
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: multi
updated: 2026-10-05
confidence: confirmed
---
# Shared libraries

There is **no shared NuGet** in this set. The same classes are **copied** per service:

- `RequestModel` with `payload`
- `RequestSecurity` AES helpers
- `EncryptionProviderFilter<T>` / `EncriptionProviderFilter<T>` (spelling varies)
- `SessionValidationFilter`
- `CacheService` (StackExchange.Redis)
- `AuditLogsService` (RabbitMQ / MassTransit)
- Logger `ILoggerService` / Serilog + `SensitiveDataMasker`

EF Core + Npgsql with retry (3 × 4s) is common. MassTransit.RabbitMQ on many services; some use `RabbitMQ.Client` directly.
