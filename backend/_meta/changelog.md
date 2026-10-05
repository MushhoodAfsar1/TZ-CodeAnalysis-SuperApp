---
kb_section: backend
type: meta
ids: [BE-META-LOG]
service: ALL
repo: TZ-CodeAnalysis-SuperApp
repo_ref: analysis/be/full-20261005
repo_sha: pending
updated: 2026-10-05
confidence: confirmed
---

# Changelog

- 2026-10-05 — `run-all` static deep pass: inventory + per-action contracts for 29 repos (decrypted DTO where EncryptionProviderFilter/type index resolved).
- 2026-10-05 — Merged `main` (PR #1) into `analysis/be/full-20261005`. Same-path add/add kept this branch. PR #1's extra `apis/*-post-api-*.md` copies (942) dropped as duplicates. Login flow kept PR #1's confirmed hops in `flows/login-registration-otp-session.md`.
- 2026-10-05 — Ops: BE analysis agents must open **exactly one PR** per run (`_meta/agent-instructions.md`). Extra PRs each start the frontend agent.
