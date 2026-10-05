---
kb_section: fe-mobile
type: flow
ids: [FLW-0007]
feature: airtimetopups
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# FLW-0007 Airtime credit and bundles

**APIs:** API-0023, API-0024, API-0044, API-0258, API-0259 · **Screens:** SCR-0015–SCR-0018 · **Rules:** BR-0008, BR-0015, BR-0016

Two journeys share the airtime folder. Bundle purchase does not call the credit top-up methods.

```mermaid
sequenceDiagram
  participant User
  participant Bundles as SCR-0015
  participant BundlePay as SCR-0016
  participant Amount as SCR-0017
  participant Pay as SCR-0018
  User->>Bundles: buy bundle
  Bundles->>Bundles: API-0023 and API-0024
  User->>BundlePay: confirm bundle
  BundlePay->>BundlePay: API-0044 ProductProvisionV2
  User->>Amount: credit top-up
  User->>Pay: PIN
  alt other operator
    Pay->>Pay: API-0258 AirTimeTopUpOthers
  else self
    Pay->>Pay: API-0259 AirTimeTopUpV1
  end
```

Field diff: [../contracts/atm-airtime-bills.md](../contracts/atm-airtime-bills.md).

## Evidence

- `lib/ui/controllers/airtimetopups/` @ `6328b7254`
- `lib/core/network/manager/api_ manager.dart` › `creditAirTimeTopUpOthers`, `requestProductProvision`, `networkBoBundles`, `networkGetSeziakoBundles`
