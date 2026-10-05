---
kb_section: fe-mobile
type: catalog
ids: [FE-CAT-SCR]
feature: ALL
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: partial
---
# Screen catalog

IDs assigned for the session/auth path and the primary money paths. Other features are still unnumbered.

| ID | Screen | Feature | Flow | APIs |
|---|---|---|---|---|
| SCR-0001 | Merchant home (`HomePageWidget`) | homepage | FLW-0001 | API-0003 (resume only) |
| SCR-0002 | Splash | splash | FLW-0002 | API-0367, API-0007, API-0318 |
| SCR-0003 | Login | login | FLW-0002 | API-0001 |
| SCR-0004 | OTP second step | otp | FLW-0002 | API-0005, API-0006 |
| SCR-0005 | Onboarding phone | onboarding | FLW-0002 | API-0004 |
| SCR-0006 | Account registration (NIDA) | registration_onboarding | FLW-0003 | API-0198 |
| SCR-0007 | Verification questions | registration_onboarding | FLW-0003 | API-0200, API-0201, API-0202 |
| SCR-0008 | Set / change / reset PIN | pinchanger, registration_onboarding | FLW-0003 | API-0073, API-0075, API-0001 |
| SCR-0009 | Send money amount | sendmoney | FLW-0004 | API-0013 |
| SCR-0010 | Send money confirm | sendmoney | FLW-0004 | API-0014 |
| SCR-0011 | Cash-point amount | cash_point | FLW-0005 | API-0039, API-0040 |
| SCR-0012 | Cash-point confirm | cash_point | FLW-0005 | API-0041, API-0042 |
| SCR-0013 | ATM cash-out amount | atm_cashout | FLW-0006 | API-0158 |
| SCR-0014 | ATM cash-out confirm | atm_cashout | FLW-0006 | API-0159 |
| SCR-0015 | Airtime bundles | airtimetopups | FLW-0007 | API-0023, API-0024 |
| SCR-0016 | Bundle confirm | airtimetopups | FLW-0007 | API-0044 |
| SCR-0017 | Credit top-up amount | airtimetopups | FLW-0007 | — |
| SCR-0018 | Credit top-up confirm | airtimetopups | FLW-0007 | API-0258, API-0259 |
| SCR-0019 | Other-bill amount | billpayment | FLW-0008 | API-0034 |
| SCR-0020 | Other-bill confirm | billpayment | FLW-0008 | API-0037 |
| SCR-0021 | Government control number | billpayment | FLW-0008 | API-0035 |
| SCR-0022 | Government bill pay | billpayment | FLW-0008 | API-0037 |
| SCR-0023 | Gift history | tanzania_gift | FLW-0009 | API-0096 |
| SCR-0024 | Gift theme | tanzania_gift | FLW-0009 | API-0097, API-0098 |
| SCR-0025 | Gift preview | tanzania_gift | FLW-0009 | API-0099 (on SCR-0010) |

Next free screen ID: `SCR-0026`.
