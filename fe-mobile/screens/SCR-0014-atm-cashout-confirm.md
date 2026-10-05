---
kb_section: fe-mobile
type: screen
ids: [SCR-0014]
feature: atm_cashout
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# SCR-0014 ATM cash-out confirm (`AtmCashoutConfirmationWidget`)

**Controller:** `AtmCashoutConfirmationWidgetController` · **Flow:** FLW-0006 · **API:** API-0159

## Entry

SCR-0013 Next. Arguments: selected `ListOfAtm` and a helper whose `sendAmount` is the typed amount and whose `feeAmount` is the literal `"10.0"`.

## Actions

| Action | Validation | API | Result |
|---|---|---|---|
| PIN | Length 4 (BR-0008) | — | Enables confirm |
| Biometrics | Hardware auth and stored secret | API-0159 | Same call, PIN from preferences |
| Confirm | PIN complete | API-0159 | Success sheet |

The call sends `atmId` from `ListOfAtm.id`, the amount with the currency stripped, and the PIN. `accessToken` in the body is an empty string. The logged-in MSISDN is added as `customerMSISDN`.

## Response branches

Success opens a non-dismissible sheet. The only field shown is envelope `transactionStatus`. OK replaces the stack with `NewBottomNavigationBarWidget`.

The model also parses `responseData.ResponseStatus`, `ResponseDescription`, `ResponseCode`, and `ReferenceID`. The sheet does not show them.

Failure clears the PIN and shows the error dialog. Default `vatInclusiveFee` is `55.0` until `setFeeVat` runs; this screen does not call a fee API.

## Evidence

- `lib/ui/controllers/atm_cashout/atm_cashout_confirmation_widget_controller.dart` › `getAtmCashoutGenerateOtp` @ `6328b7254`
- `lib/ui/widgets/atm_cashout/atm_cashout_confirmation_widget.dart` › `getGenerateOtp`
- `lib/models/network/atm_cashout/atm_cashout_generate_otp_response_model.dart`
