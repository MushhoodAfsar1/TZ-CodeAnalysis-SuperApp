---
kb_section: fe-mobile
type: catalog
ids: [FE-META-COV]
feature: ALL
fe_ref: main
fe_sha: 6328b7254
updated: 2026-10-05
confidence: partial
---

# Coverage

FE `main` @ `6328b7254`. Backend KB `main` @ `0c13cc4`. API inventory is done. Session/auth and the primary send-money and agent cash-out paths are `deep-analyzed`. Other feature rows stay `not-started`.

| Feature slug | FE paths (main) | Screens | APIs touched | Status | analyzed_sha | Updated | Notes |
|---|---|---:|---:|---|---|---|---|
| `_api-inventory` | `lib/core/network/manager/api_ manager.dart` | 0 | 367 | inventoried | `6328b7254` | 2026-10-05 | Live calls only. Callers are files, not screens. |
| `add_notification` | `lib/ui/controllers/add_notification/` | 0 | 3 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `advance_salary` | `lib/ui/controllers/advance_salary/` | 0 | 5 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `aft` | `lib/ui/controllers/aft/` | 0 | 3 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `airtimetopups` | `lib/ui/controllers/airtimetopups/` | 0 | 5 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `appmedia` | `lib/ui/controllers/appmedia/` | 0 | 1 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `atm_cashout` | `lib/ui/controllers/atm_cashout/` | 0 | 2 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `bankaccounts` | `lib/ui/controllers/bankaccounts/` | 0 | 7 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `billpayment` | `lib/ui/controllers/billpayment/` | 0 | 6 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `block_my_number` | `lib/ui/controllers/block_my_number/` | 0 | 2 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `bus_ticketing` | `lib/ui/controllers/bus_ticketing/` | 0 | 6 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `card_theme` | `lib/ui/controllers/card_theme/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `cardtheme` | `lib/ui/controllers/cardtheme/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `cash_point` | `lib/ui/controllers/cash_point/` | 2 | 6 | deep-analyzed | `6328b7254` | 2026-10-05 | SCR-0011–0012, FLW-0005. Consumer fee/payment matched. Merchant and Mchango branches named, contracts not re-diffed. |
| `changeAccount` | `lib/ui/controllers/changeAccount/` | 0 | 2 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `chat_bot` | `lib/ui/controllers/chat_bot/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `commonapis` | `lib/ui/controllers/commonapis/` | 0 | 4 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `contactselection` | `lib/ui/controllers/contactselection/` | 0 | 10 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `controller_commons` | `lib/ui/controllers/controller_commons/` | 0 | 15 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `corporate_expenses_management` | `lib/ui/controllers/corporate_expenses_management/` | 0 | 7 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `customer_support` | `lib/ui/controllers/customer_support/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `dashboard` | `lib/ui/controllers/dashboard/` | 0 | 18 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `dashboard_bg_themes` | `lib/ui/controllers/dashboard_bg_themes/` | 0 | 1 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `dashboard_theme` | `lib/ui/controllers/dashboard_theme/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `dashboard_v2` | `lib/ui/controllers/dashboard_v2/` | 0 | 8 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `dashboardv3` | `lib/ui/controllers/dashboardv3/` | 0 | 4 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `device_loan` | `lib/ui/controllers/device_loan/` | 0 | 1 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `deviceconnected` | `lib/ui/controllers/deviceconnected/` | 0 | 2 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `diaspora` | `lib/ui/controllers/diaspora/` | 0 | 1 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `dynamic_qr_merchant` | `lib/ui/controllers/dynamic_qr_merchant/` | 0 | 2 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `easyloadandbundles` | `lib/ui/controllers/easyloadandbundles/` | 0 | 10 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `emergency_block` | `lib/ui/controllers/emergency_block/` | 0 | 1 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `estate_download` | `lib/ui/controllers/estate_download/` | 0 | 1 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `faq` | `lib/ui/controllers/faq/` | 0 | 1 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `favorites` | `lib/ui/controllers/favorites/` | 0 | 4 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `feedback` | `lib/ui/controllers/feedback/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `fiber` | `lib/ui/controllers/fiber/` | 0 | 3 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `financial_service` | `lib/ui/controllers/financial_service/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `header` | `lib/ui/controllers/header/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `homepage` | `lib/ui/controllers/homepage/` | 1 | 0 | partial | `6328b7254` | 2026-10-05 | SCR-0001 session resume only. Other merchant-home APIs not traced. |
| `insurance` | `lib/ui/controllers/insurance/` | 0 | 5 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `inviteearn` | `lib/ui/controllers/inviteearn/` | 0 | 4 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `invoice_management` | `lib/ui/controllers/invoice_management/` | 0 | 4 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `kikoba` | `lib/ui/controllers/kikoba/` | 0 | 28 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `login` | `lib/ui/controllers/login/` | 1 | 1 | deep-analyzed | `6328b7254` | 2026-10-05 | SCR-0003, FLW-0002. Login call is API-0001 (caller file is controller_commons). |
| `maps` | `lib/ui/controllers/maps/` | 0 | 1 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `mchango` | `lib/ui/controllers/mchango/` | 0 | 23 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `merchant` | `lib/ui/controllers/merchant/` | 0 | 1 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `mini_apps` | `lib/ui/controllers/mini_apps/` | 0 | 5 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `mixx_point` | `lib/ui/controllers/mixx_point/` | 0 | 5 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `movie_tickets` | `lib/ui/controllers/movie_tickets/` | 0 | 8 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `myprofile` | `lib/ui/controllers/myprofile/` | 0 | 1 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `notification` | `lib/ui/controllers/notification/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `onboarding` | `lib/ui/controllers/onboarding/` | 1 | 1 | deep-analyzed | `6328b7254` | 2026-10-05 | SCR-0005. API-0004 CheckAuthV2 contract-mismatch. |
| `otp` | `lib/ui/controllers/otp/` | 1 | 2 | deep-analyzed | `6328b7254` | 2026-10-05 | SCR-0004. GenerateOtpV2 and VerifyOtpV2 stay fe-only. |
| `permission_info` | `lib/ui/controllers/permission_info/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `pinchanger` | `lib/ui/controllers/pinchanger/` | 1 | 3 | deep-analyzed | `6328b7254` | 2026-10-05 | Included in SCR-0008. Change PIN and reset PIN traced. Third API in the folder count not re-opened. |
| `pincode` | `lib/ui/controllers/pincode/` | 0 | 0 | deep-analyzed | `6328b7254` | 2026-10-05 | PIN field helper only. Length 4. No API. |
| `promotions` | `lib/ui/controllers/promotions/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `qrscan` | `lib/ui/controllers/qrscan/` | 0 | 6 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `recent_and_favourites` | `lib/ui/controllers/recent_and_favourites/` | 0 | 5 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `registration_details` | `lib/ui/controllers/registration_details/` | 0 | 1 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `registration_onboarding` | `lib/ui/controllers/registration_onboarding/` | 3 | 8 | partial | `6328b7254` | 2026-10-05 | FLW-0003 happy path. Biometric and micro-business branches not traced. API-0202 contract-mismatch. |
| `request_to_pay` | `lib/ui/controllers/request_to_pay/` | 0 | 3 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `request_to_pay_consumer` | `lib/ui/controllers/request_to_pay_consumer/` | 0 | 3 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `sattlment` | `lib/ui/controllers/sattlment/` | 0 | 6 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `schedule` | `lib/ui/controllers/schedule/` | 0 | 4 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `search` | `lib/ui/controllers/search/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `see_all_menu` | `lib/ui/controllers/see_all_menu/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `selfcare` | `lib/ui/controllers/selfcare/` | 0 | 10 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `sendmoney` | `lib/ui/controllers/sendmoney/` | 2 | 15 | partial | `6328b7254` | 2026-10-05 | FLW-0004 local P2P only. Gift, IMT, QR, and send-to-many not fully traced. |
| `serviceclient` | `lib/ui/controllers/serviceclient/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `sidemenu` | `lib/ui/controllers/sidemenu/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `splash` | `lib/ui/controllers/splash/` | 1 | 3 | deep-analyzed | `6328b7254` | 2026-10-05 | SCR-0002. Gateway token, pre-login config, BO cards. |
| `stock_market` | `lib/ui/controllers/stock_market/` | 0 | 14 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `tanzania_gift` | `lib/ui/controllers/tanzania_gift/` | 0 | 3 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `tanzania_loan` | `lib/ui/controllers/tanzania_loan/` | 0 | 15 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `tanzania_saving` | `lib/ui/controllers/tanzania_saving/` | 0 | 6 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `tigocard` | `lib/ui/controllers/tigocard/` | 0 | 4 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `transaction_reversal` | `lib/ui/controllers/transaction_reversal/` | 0 | 1 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `transactions` | `lib/ui/controllers/transactions/` | 0 | 2 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `unsolicited_sms` | `lib/ui/controllers/unsolicited_sms/` | 0 | 3 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `user_management` | `lib/ui/controllers/user_management/` | 0 | 4 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `userprofile` | `lib/ui/controllers/userprofile/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `visacard` | `lib/ui/controllers/visacard/` | 0 | 1 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `withdrawal` | `lib/ui/controllers/withdrawal/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `revamp-card_new` | `lib/ui/new_ui_revamp/card_new/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `revamp-clms` | `lib/ui/new_ui_revamp/clms/` | 0 | 2 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `revamp-customer_support` | `lib/ui/new_ui_revamp/customer_support/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `revamp-dashboard_new` | `lib/ui/new_ui_revamp/dashboard_new/` | 0 | 9 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `revamp-home_new` | `lib/ui/new_ui_revamp/home_new/` | 0 | 1 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `revamp-master_card` | `lib/ui/new_ui_revamp/master_card/` | 0 | 6 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `revamp-notification` | `lib/ui/new_ui_revamp/notification/` | 0 | 3 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `revamp-personal_loan_new` | `lib/ui/new_ui_revamp/personal_loan_new/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `revamp-promotions` | `lib/ui/new_ui_revamp/promotions/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `revamp-search` | `lib/ui/new_ui_revamp/search/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `revamp-see-all-menu` | `lib/ui/new_ui_revamp/see-all-menu/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `revamp-send_money` | `lib/ui/new_ui_revamp/send_money/` | 0 | 1 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `revamp-side_menu` | `lib/ui/new_ui_revamp/side_menu/` | 0 | 1 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `revamp-sports_event` | `lib/ui/new_ui_revamp/sports_event/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `revamp-top-up` | `lib/ui/new_ui_revamp/top-up/` | 0 | 5 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `revamp-utils` | `lib/ui/new_ui_revamp/utils/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `revamp-widgets` | `lib/ui/new_ui_revamp/widgets/` | 0 | 0 | not-started | — | 2026-10-05 | Screen inventory not started. |
| `core` | — | 0 | 1 | not-started | — | 2026-10-05 | Caller files outside a feature folder, or no caller. |
| `utils` | — | 0 | 3 | not-started | — | 2026-10-05 | Caller files outside a feature folder, or no caller. |
| `(no caller file)` | — | 0 | 39 | not-started | — | 2026-10-05 | Caller files outside a feature folder, or no caller. |

API totals: 367 live · path-only 275 · contract-mismatch 7 · matched 2 · fe-only 83 · gaps 118.

Deep-analyzed or partial this pass: splash, login, otp, onboarding, registration_onboarding, pinchanger, pincode, homepage (session hook), sendmoney (P2P), cash_point. Remaining feature rows are `not-started`.

