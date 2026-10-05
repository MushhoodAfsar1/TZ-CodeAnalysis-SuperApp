---
kb_section: fe-mobile
type: screen
ids: [SCR-0021]
feature: billpayment
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# SCR-0021 Government control number (`EnterControlNumberWidget`)

**Controller:** `EnterControlNumberWidgetController` · **Flow:** FLW-0008 · **API:** API-0035

## Entry

Government bills list (`GovernmentBillsWidget` → `BillPaymentWidget`) or Zanzibar. Company name decides the police flag when it contains `Traffic Police`.

## Actions

| Action | Validation | API | Result |
|---|---|---|---|
| Type reference | Length at least 7 enables Next | — | |
| Next | Reference long enough | API-0035 | Amount screen or a bill picker |

`isControlNumber` follows the selected chip (`groupValue == 0`). `flowId` selects `asseType`: Dawasa uses `ASSESS-A` or `ASSESS-C`. Tarura and traffic use `ASSESS-A` or `ASSESS-E`. Other flows send `ASSESS-A`. Traffic on non-staging builds also sends `resultUrl`. The URL value is not recorded here. `spCode` is set for police and for Tarura when the chip is not a control number. `asseTypeValue` is the typed reference. `sourceMSISDN` is the logged-in or merchant number.

## Response branches

Success requires `responseData.resp.gepgBillChkResp.billDtls.billDtl` to be non-empty. One bill opens the government amount widget with `billHdr.shortCode`, `billCtrNum`, and `payOpt`. Several bills open a picker. Empty details stay on this screen. Failure shows the gov-inquiry error.

Zanzibar uses the same API from its own controller. That widget is not a separate screen ID.

## Evidence

- `lib/ui/controllers/billpayment/enter_control_number_widget_controller.dart` @ `6328b7254`
- `lib/ui/widgets/billpayment/enter_control_number_widget.dart`
- `lib/core/network/manager/api_ manager.dart` › `requestGovPaymentInquiry`
