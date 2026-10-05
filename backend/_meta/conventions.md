---
kb_section: backend
type: meta
ids: [BE-META-CONV]
service: ALL
repo: TZ-CodeAnalysis-SuperApp
repo_ref: analysis/be/full-20261005
repo_sha: pending
updated: 2026-10-05
confidence: confirmed
---

# Conventions

| Pattern | Meaning |
|---|---|
| `BE-SVC-<CODE>` | Service |
| `BE-API-<CODE>-###` | HTTP action |
| `BE-EVT-<CODE>-###` | Event |
| `BE-JOB-<CODE>-###` | Job / consumer |
| `BE-BR-<CODE>-###` | Business rule |
| `BE-ERR-<CODE>-###` | Error |
| `BE-INT-<CODE>-###` | External integration |
| `BE-FLW-###` | Cross-service flow |
| `BE-GAP-###` | Gap |

## Confidence
- **confirmed**: traced in code at recorded SHA.
- **inferred**: Swagger/XML/name-based.
- **partial**: DTO/route confirmed; deep handler branches not fully expanded.

## Redaction
Document field **names** and validation, never secrets, PII, hosts, or key material. Samples are synthetic.
Contracts are the **decrypted** shape after AES payload unwrap.

## Agent runs
See [`agent-instructions.md`](agent-instructions.md). **One PR per run** — extra PRs trigger the frontend analysis agent.

