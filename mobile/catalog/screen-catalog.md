---
kb_section: mobile
type: catalog
ids: [FE-CAT-SCR]
service: ALL
repo: TZ-Tigo-SuperApp-Mobile
repo_ref: main
repo_sha: 6328b7254
be_kb_ref: cursor/frontend-mobile-api-analysis-ad82
be_kb_sha: 2655b7a
updated: 2026-10-05
confidence: partial
---

# Screen catalog

A screen file exists only when that screen calls a backend API or enforces a rule. App-shell and network-layer triggers are listed in the matrix and do not get a screen ID.

| FE-SCR | Screen name (business) | Widget class | Layout (legacy/revamp) | Controller | Feature | BE-APIs called | Rules | File? | Conf. |
|---|---|---|---|---|---|---|---|---|---|
| FE-SCR-001 | Merchant home | `HomePageWidget` | legacy | `HomePageWidgetController` | homepage | BE-API-SESS-002 | FE-BR-SESS-001, FE-BR-SESS-002, FE-BR-SESS-003, FE-BR-SESS-006 | yes | partial |
