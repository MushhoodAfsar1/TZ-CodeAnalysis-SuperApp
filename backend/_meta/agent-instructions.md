---
kb_section: backend
type: meta
ids: [BE-META-AGENT]
service: ALL
repo: TZ-CodeAnalysis-SuperApp
repo_ref: main
repo_sha: pending
updated: 2026-10-05
confidence: confirmed
---

# BE analysis agent instructions

Read this at the start of every `run-all` / `refresh` / deepen pass.

## Write targets
- Analysis repo only: `https://github.com/MushhoodAfsar1/TZ-CodeAnalysis-SuperApp`
- Output: `backend/` (never `.cursor/`, never `fe-mobile/`, never `mobile/`)
- BE `TZ-Tigo-SuperApp-*` checkouts are **read-only**

## HARD: exactly one pull request

Each BE analysis run must produce **at most one** GitHub PR against `main`.

A new PR on this repo starts the **frontend analysis agent**. Opening two PRs (or a BE PR plus an accidental `cursor/*` / FE PR) runs that agent twice. That happened on 2026-10-05 (PRs #3, #4, and #5).

| Do | Do not |
|---|---|
| One branch `analysis/be/<command>-<YYYYMMDD>` from up-to-date `main` | Also PR the Cloud Agent default `cursor/*` branch |
| If a PR for that branch exists, **push and update it** | Call `open_git_pr` a second time |
| Call `open_git_pr` **once**, after the last successful push | Open a PR per service, per resume, or per catalog rebuild |
| Webhook the next agent **once** after that PR exists | Webhook with no PR, or webhook twice |
| Suffix `-2` only if the date branch already exists **and** it has **no** open PR | Open a competing refresh PR the same day |

Do not merge, force-push, or push `main` unless a human explicitly asks.

Resume-without-finishing: commit+push the current branch, record resume in local memory, **do not** open a second PR, **do not** webhook.
