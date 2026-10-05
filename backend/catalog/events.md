---
kb_section: backend
type: catalog
ids: [BE-CAT-EVT]
service: ALL
repo: multi
repo_ref: checked-out
repo_sha: multi
updated: 2026-10-05
confidence: partial
---

# Events

No MassTransit bus registration found except Notification `FCMNotificationConsumer` source (bus not wired in Program.cs). RabbitMQ helpers publish audit/FCM payloads in several services.
