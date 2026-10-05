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

IDs assigned for session/auth, local send money, cash-out, dashboard balance, airtime top-up, and bill pay. Other features are still unnumbered.

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
| SCR-0013 | Dashboard wallet balance | dashboard | — | API-0018 |
| SCR-0014 | Airtime top-up amount | airtimetopups | FLW-0006 | API-0257 |
| SCR-0015 | Airtime top-up confirm | airtimetopups | FLW-0006 | API-0258, API-0259 |
| SCR-0016 | Pay-bill amount | billpayment | FLW-0007 | API-0034 |
| SCR-0017 | Pay-bill confirm | billpayment | FLW-0007 | API-0037 |
| SCR-0018 | Government control number | billpayment | FLW-0007 | API-0035 |

Next free screen ID: `SCR-0019`.
