---
kb_section: fe-mobile
type: gap
ids: [FE-UNMAPPED]
feature: ALL
fe_ref: main
fe_sha: 6328b7254
updated: 2026-10-05
confidence: partial
---

# Unmapped endpoints

## How FE paths were compared

The gateway prefix and host were removed. Comparison is the lower-cased `/api/...` suffix plus HTTP method when both sides have one. A gateway prefix (`accounts`, `sendmoney`, `loan`, …) was used only when several backend rows shared that suffix. Identical public paths on two Group Saving controller trees stay `path-only` and list both BE IDs (see GAP for the duplicate).

## FE calls with no BE path (83)

| API | Method | Path | Gap |
|---|---|---|---|
| API-0005 | `requestGetOTP` | `accounts/api/Otp/GenerateOtpV2` | GAP-0001 |
| API-0006 | `requestVerifyOTP` | `accounts/api/Otp/VerifyOtpV2` | GAP-0002 |
| API-0008 | `requestCreateUserPIN` | `accounts/1.0.0/api/profiles/creatempin` | GAP-0003 |
| API-0021 | `requestTransactionDetail` | `accounts/1.0.0/api/profiles/transactionhistory` | GAP-0004 |
| API-0022 | `requestBillsDeleted` | `billpayment/1.0.0/api/Billing/DeleteBillReference` | GAP-0005 |
| API-0029 | `linkVisaCard` | `api/VisaPayment/LinkVisaCard` | GAP-0006 |
| API-0030 | `getVisaCardPin` | `api/VisaPayment/GetVisaCardPin` | GAP-0007 |
| API-0031 | `getVisaCardListTransaction` | `api/VisaPayment/GetVisaCardListTransaction` | GAP-0008 |
| API-0032 | `updateVisaCardStatus` | `api/VisaPayment/UpdateVisaCardStatus` | GAP-0009 |
| API-0033 | `updateVisaCardTransactionList` | `api/VisaPayment/UpdateVisaCardTransactionList` | GAP-0010 |
| API-0054 | `getAftConfig` | `configuration/api/AFTTCApp/get` | GAP-0011 |
| API-0055 | `aftCheckFee` | `wallet/api/Card/checkfee` | GAP-0012 |
| API-0056 | `aftCheckout` | `wallet/api/Card/checkout` | GAP-0013 |
| API-0057 | `aftCardVerify` | `wallet/api/Card/verify` | GAP-0014 |
| API-0059 | `getInvoiceFields` | `configuration/api/InvoiceManagement/GetInvoiceFields` | GAP-0015 |
| API-0060 | `getInvoiceDetails` | `accounts/api/Invoice/QueryInvoiceDetails` | GAP-0016 |
| API-0066 | `requestDeleteCard` | `virtualcard/api/CardManagement/DeleteCardV1` | GAP-0017 |
| API-0085 | `emergencyBlockAccount` | `accounts/api/Profile/EmergencyBlock` | GAP-0018 |
| API-0106 | `deleteTransferScheduleById` | `merchant/api/Settlement/DeleteTransferScheduleById` | GAP-0019 |
| API-0129 | `getClmsLoanAndProduct` | `loan/api/OlmsLoan/OlmsGetEligibilityAndOustanding` | GAP-0020 |
| API-0131 | `requestLoanEligibility` | `loan/api/OlmsLoan/OlmsCheckCombineEligility` | GAP-0021 |
| API-0133 | `requestPurchaseCLMSLoanProduct` | `loan/api/OlmsLoan/OlmsApplyLoan` | GAP-0022 |
| API-0135 | `requestSubmitRepayClmsLoan` | `loan/api/OlmsLoan/OlmsRepayLoan` | GAP-0023 |
| API-0136 | `getClmsUserLoans` | `loan/api/OlmsLoan/OlmsGetActiveLoans` | GAP-0024 |
| API-0139 | `requestRepayClmsLoanHistory` | `loan/api/OlmsLoan/OlmsGetRepaymentHistory` | GAP-0025 |
| API-0163 | `salaryAdvanceAllRequest` | `expenses/api/AdvanceSalary/GetSalaryAdvanceRequestsV2` | GAP-0026 |
| API-0200 | `requestGetOTPSelfOnBoard` | `accounts/api/Otp/GenerateOtpV2` | GAP-0027 |
| API-0201 | `requestVerifyOTPSelfOnBoard` | `accounts/api/Otp/VerifyOtpV2` | GAP-0028 |
| API-0204 | `ListServices` | `creditmgt/api/LendMeService/CheckEligibility` | GAP-0029 |
| API-0205 | `AdvanceLoanOffer` | `creditmgt/api/LendMeService/AdvanceLoanOffer` | GAP-0030 |
| API-0288 | `getGroupMembers` | `groupsaving/api/Member/GetMembers` | GAP-0031 |
| API-0289 | `addGroupMember` | `groupsaving/api/Member/AddMember` | GAP-0032 |
| API-0292 | `removeGroupMember` | `groupsaving/api/Member/RemoveMember` | GAP-0033 |
| API-0293 | `getRecentActivities` | `groupsaving/api/Fund/GetRecentActivities` | GAP-0034 |
| API-0294 | `updateGroupMemberRole` | `groupsaving/api/Member/UpdateRole` | GAP-0035 |
| API-0295 | `invitationAction` | `groupsaving/api/app/invitations/InvitationAction` | GAP-0036 |
| API-0296 | `getGroupInvitations` | `groupsaving/api/app/invitations/GetInvitations` | GAP-0037 |
| API-0297 | `sendContribution` | `groupsaving/api/Fund/SendContribution` | GAP-0038 |
| API-0298 | `paySocialFund` | `groupsaving/api/Fund/PaySocialFund` | GAP-0039 |
| API-0299 | `buySharesConfirm` | `groupsaving/api/Fund/BuySharesConfirm` | GAP-0040 |
| API-0301 | `changeSharePrice` | `groupsaving/api/Fund/ChangeSharePrice` | GAP-0041 |
| API-0303 | `getGroupNotifications` | `groupsaving/api/Notification/GetNotifications` | GAP-0042 |
| API-0304 | `approveNotification` | `groupsaving/api/Notification/ApproveNotification` | GAP-0043 |
| API-0306 | `requestCalculateLoanEligibility` | `groupsaving/api/Group/CalculateLoanEligibility` | GAP-0044 |
| API-0309 | `requestSetPenalty` | `groupsaving/api/Fund/SetPenalty` | GAP-0045 |
| API-0310 | `requestViewPenalty` | `groupsaving/api/Fund/QueryMemberPanalPenalties` | GAP-0046 |
| API-0311 | `requestPayPenalty` | `groupsaving/api/Fund/PayPanalty` | GAP-0047 |
| API-0312 | `kikobaTransfer` | `groupsaving/api/Fund/Transfer` | GAP-0048 |
| API-0313 | `kikobaPayPanalty` | `groupsaving/api/Fund/PayPanalty` | GAP-0049 |
| API-0315 | `kikobaPenalties` | `groupsaving/api/Fund/QueryMemberPanalPenalties` | GAP-0050 |
| API-0323 | `kikobaEstatement` | `groupsaving/api/Fund/ExportFullStatement` | GAP-0051 |
| API-0335 | `getInvoiceFee` | `sendmoney/api/SendMoney/InvoiceFee` | GAP-0052 |
| API-0336 | `requestInvoicePayment` | `sendmoney/api/SendMoney/InvoicePayment` | GAP-0053 |
| API-0337 | `getCountriesAndBanksForInternationalTransfer` | `configuration/api/IMT/getCBM` | GAP-0054 |
| API-0338 | `getBankFieldsForInternationalTransfer` | `configuration/api/IMT/getBankFields` | GAP-0055 |
| API-0339 | `getAccountMobileValidationForInternationalTransfer` | `sendmoney/api/IMT/AccountMobileValidation` | GAP-0056 |
| API-0340 | `getMobileCurrencyExchangeForInternationalTransfer` | `sendmoney/api/IMT/MobileCurrencyExchange` | GAP-0057 |
| API-0341 | `getAccountBankValidationForInternationalTransfer` | `sendmoney/api/IMT/AccountBankValidation` | GAP-0058 |
| API-0342 | `getBankCurrencyExchangeForInternationalTransfer` | `sendmoney/api/IMT/BankCurrencyExchange` | GAP-0059 |
| API-0343 | `getSubmitMobilePaymentForInternationalTransfer` | `sendmoney/api/IMT/SubmitMobilePayment` | GAP-0060 |
| API-0344 | `getSubmitBankPaymentForInternationalTransfer` | `sendmoney/api/IMT/SubmitBankPayment` | GAP-0061 |
| API-0345 | `loanInsuranceConfig` | `configuration/api/LoanInsuranceApp/get` | GAP-0062 |
| API-0347 | `getMyPlans` | `loan/api/LoanInsurance/GetMyPlans` | GAP-0063 |
| API-0348 | `getPlanDetails` | `loan/api/LoanInsurance/GetPlanDetails` | GAP-0064 |
| API-0349 | `vcMasterCardCreateCard` | `virtualcard/api/VCMasterCard/CreateCard` | GAP-0065 |
| API-0350 | `vcMasterCardViewCardDetails` | `virtualcard/api/VCMasterCard/ViewCardDetails` | GAP-0066 |
| API-0351 | `updateCardStatus` | `virtualcard/api/VCMasterCard/UpdateCardStatus` | GAP-0067 |
| API-0352 | `vcMasterCardLoadCard` | `virtualcard/api/VCMasterCard/LoadCard` | GAP-0068 |
| API-0353 | `vcMasterCardUnloadCard` | `virtualcard/api/VCMasterCard/UnloadCard` | GAP-0069 |
| API-0354 | `vcMasterCardGetCardStatement` | `virtualcard/api/VCMasterCard/GetCardStatement` | GAP-0070 |
| API-0355 | `vcMasterCardDeleteCard` | `virtualcard/api/VCMasterCard/DeleteCard` | GAP-0071 |
| API-0356 | `vcMasterCardUpdateCardName` | `virtualcard/api/VCMasterCard/UpdateCardName` | GAP-0072 |
| API-0357 | `vcMasterCardFeeCheck` | `virtualcard/api/VCMasterCard/FeeCheck` | GAP-0073 |
| API-0358 | `vcMasterCardClientInformation` | `virtualcard/api/VCMasterCard/ClientInformation` | GAP-0074 |
| API-0359 | `vcMasterCardValidateCardHolder` | `virtualcard/api/VCMasterCard/ValidateCardHolder` | GAP-0075 |
| API-0360 | `vcMasterCardRecentTransactionHistory` | `virtualcard/api/VCMasterCard/RecentTransactionHistory` | GAP-0076 |
| API-0361 | `claimFormCreateClaim` | `virtualcard/api/ClaimForm/CreateClaim` | GAP-0077 |
| API-0362 | `claimFormGetClaimStep` | `virtualcard/api/ClaimForm/GetClaimStep` | GAP-0078 |
| API-0363 | `claimFormUploadClaimAttachment` | `virtualcard/api/ClaimForm/UploadClaimAttachment` | GAP-0079 |
| API-0364 | `claimFormDeleteClaimAttachment` | `virtualcard/api/ClaimForm/DeleteClaimAttachment` | GAP-0080 |
| API-0365 | `claimFormUpdateClaimEmail` | `virtualcard/api/ClaimForm/UpdateClaimEmail` | GAP-0081 |
| API-0366 | `claimFormTransactionFeed` | `virtualcard/api/ClaimForm/TransactionFeed` | GAP-0082 |
| API-0367 | `SessionNetworkManager.requestGenerateGateWayToken` | `oauth2/token` | GAP-0083 |

## BE catalog paths with no live FE caller

Counts are path-suffix inventory only. CONFIG is summarized, not listed. Portal and identity admin catalogs were not treated as mobile-missing.

| Service | BE paths with no FE suffix match | Grouped gap |
|---|---:|---|
| ACCOUNT | 29 | GAP-0084 |
| AIRTIME | 4 | GAP-0085 |
| CONFIG | 399 | GAP-0086 |
| DSTV | 4 | GAP-0087 |
| EXPENSE | 2 | GAP-0088 |
| EXTPAY | 3 | GAP-0089 |
| GRPSAV | 52 | GAP-0090 |
| GSM | 7 | GAP-0091 |
| INSUR | 8 | GAP-0092 |
| LOAN | 6 | GAP-0093 |
| MCHANGO | 34 | GAP-0094 |
| MERCH | 21 | GAP-0095 |
| NOTIF | 16 | GAP-0096 |
| REWARD | 14 | GAP-0097 |
| SAVING | 3 | GAP-0098 |
| SELFC | 26 | GAP-0099 |
| SEND | 3 | GAP-0100 |
| SESS | 3 | GAP-0101 |
| VCARD | 3 | GAP-0102 |
| WALLET | 4 | GAP-0103 |

### Detail (excluding CONFIG)

| BE ID | Service | Method | Path |
|---|---|---|---|
| BE-API-SESS-001 | SESS | POST | `/api/Account/auth` |
| BE-API-SESS-003 | SESS | POST | `/api/Account/enc` |
| BE-API-SESS-004 | SESS | POST | `/api/Account/decreq` |
| BE-API-ACCOUNT-008 | ACCOUNT | POST | `/api/Profile/UpdateProfileImage` |
| BE-API-ACCOUNT-010 | ACCOUNT | POST | `/api/Profile/CheckAuthV1` |
| BE-API-ACCOUNT-017 | ACCOUNT | POST | `/api/Profile/encCheckAuth` |
| BE-API-ACCOUNT-018 | ACCOUNT | POST | `/api/Profile/encDeleteDevice` |
| BE-API-ACCOUNT-019 | ACCOUNT | POST | `/api/Profile/encRegistration` |
| BE-API-ACCOUNT-020 | ACCOUNT | POST | `/api/Profile/encLoginProfile` |
| BE-API-ACCOUNT-021 | ACCOUNT | POST | `/api/Profile/encUpdateProfileImage` |
| BE-API-ACCOUNT-022 | ACCOUNT | POST | `/api/QR/DecodeQr` |
| BE-API-ACCOUNT-025 | ACCOUNT | POST | `/api/QR/enc` |
| BE-API-ACCOUNT-026 | ACCOUNT | POST | `/api/QR/dec` |
| BE-API-ACCOUNT-029 | ACCOUNT | POST | `/api/Favourites/importcsvbillpayment` |
| BE-API-ACCOUNT-030 | ACCOUNT | POST | `/api/Favourites/importcsvbanktransfer` |
| BE-API-ACCOUNT-031 | ACCOUNT | POST | `/api/Favourites/importcsvsendmoney` |
| BE-API-ACCOUNT-032 | ACCOUNT | POST | `/api/Favourites/importcsvtopup` |
| BE-API-ACCOUNT-033 | ACCOUNT | POST | `/api/Favourites/importcsvmerchantpayment` |
| BE-API-ACCOUNT-034 | ACCOUNT | POST | `/api/Favourites/enc` |
| BE-API-ACCOUNT-035 | ACCOUNT | POST | `/api/Favourites/dec` |
| BE-API-ACCOUNT-036 | ACCOUNT | POST | `/api/Favourites/encGet` |
| BE-API-ACCOUNT-037 | ACCOUNT | POST | `/api/Favourites/decGet` |
| BE-API-ACCOUNT-038 | ACCOUNT | POST | `/api/Conversion/Encrypt` |
| BE-API-ACCOUNT-039 | ACCOUNT | POST | `/api/Conversion/Decrypt` |
| BE-API-ACCOUNT-044 | ACCOUNT | POST | `/api/Region/enc` |
| BE-API-ACCOUNT-045 | ACCOUNT | POST | `/api/Region/dec` |
| BE-API-ACCOUNT-046 | ACCOUNT | POST | `/api/Otp/GenerateOtp` |
| BE-API-ACCOUNT-047 | ACCOUNT | POST | `/api/Otp/VerifyOtp` |
| BE-API-ACCOUNT-048 | ACCOUNT | POST | `/api/Otp/GenerateOtpV1` |
| BE-API-ACCOUNT-049 | ACCOUNT | POST | `/api/Otp/VerifyOtpV1` |
| BE-API-ACCOUNT-050 | ACCOUNT | POST | `/api/Otp/encVerifyOtp` |
| BE-API-ACCOUNT-051 | ACCOUNT | POST | `/api/Otp/encGenerateOtp` |
| BE-API-WALLET-003 | WALLET | POST | `/api/CashOut/cashOutPayment` |
| BE-API-WALLET-004 | WALLET | POST | `/api/CashOut/encrypt` |
| BE-API-WALLET-005 | WALLET | POST | `/api/CashOut/decrypt` |
| BE-API-WALLET-007 | WALLET | POST | `/api/WalletBalance/enc` |
| BE-API-SEND-013 | SEND | POST | `/api/SendMoney/GetGift` |
| BE-API-SEND-014 | SEND | POST | `/api/SendMoney/encVerify` |
| BE-API-SEND-015 | SEND | POST | `/api/SendMoney/encTransfer` |
| BE-API-AIRTIME-003 | AIRTIME | POST | `/api/FiberProduct/SubmitPaymentCapacityChange` |
| BE-API-AIRTIME-005 | AIRTIME | POST | `/api/AirTime/AirTimeTopUp` |
| BE-API-AIRTIME-009 | AIRTIME | POST | `/api/AirTime/enc` |
| BE-API-AIRTIME-010 | AIRTIME | POST | `/api/AirTime/dec` |
| BE-API-EXTPAY-004 | EXTPAY | POST | `/api/ExternalPayment/encrypt` |
| BE-API-EXTPAY-005 | EXTPAY | POST | `/api/ExternalPayment/decrypt` |
| BE-API-EXTPAY-006 | EXTPAY | POST | `/api/ExternalPayment/test` |
| BE-API-MERCH-005 | MERCH | POST | `/api/Notification/enc` |
| BE-API-MERCH-009 | MERCH | POST | `/api/Schedular/enc` |
| BE-API-MERCH-010 | MERCH | POST | `/api/Schedular/dec` |
| BE-API-MERCH-014 | MERCH | POST | `/api/RequestToPay/BillerCallback` |
| BE-API-MERCH-018 | MERCH | POST | `/api/Merchant/RegisterDevice` |
| BE-API-MERCH-019 | MERCH | POST | `/api/Merchant/VerifyDevice` |
| BE-API-MERCH-020 | MERCH | POST | `/api/Merchant/GetSessionToken` |
| BE-API-MERCH-021 | MERCH | POST | `/api/Merchant/GenerateQR` |
| BE-API-MERCH-030 | MERCH | POST | `/api/Merchant/dec` |
| BE-API-MERCH-031 | MERCH | POST | `/api/Merchant/encRegisterDevice` |
| BE-API-MERCH-032 | MERCH | POST | `/api/Merchant/encVerifyDevice` |
| BE-API-MERCH-033 | MERCH | POST | `/api/Merchant/encGetSessionToken` |
| BE-API-MERCH-034 | MERCH | POST | `/api/Merchant/encGenerateQR` |
| BE-API-MERCH-035 | MERCH | POST | `/api/Merchant/encUpdateMerchantStatus` |
| BE-API-MERCH-036 | MERCH | POST | `/api/Merchant/encIsPinReset` |
| BE-API-MERCH-038 | MERCH | POST | `/api/Settlement/GetTransferScheduleById` |
| BE-API-MERCH-040 | MERCH | POST | `/api/Settlement/GetAllTransferSchedule` |
| BE-API-MERCH-041 | MERCH | POST | `/api/Settlement/GetActiveTransferSchedule` |
| BE-API-MERCH-044 | MERCH | POST | `/api/Settlement/importcsv` |
| BE-API-MERCH-045 | MERCH | POST | `/api/Settlement/enc` |
| BE-API-MERCH-046 | MERCH | POST | `/api/Settlement/dec` |
| BE-API-LOAN-006 | LOAN | POST | `/api/LoanManagement/GetLoanTransactions` |
| BE-API-LOAN-011 | LOAN | POST | `/api/Kitonga/GetCreditScore` |
| BE-API-LOAN-016 | LOAN | POST | `/api/Kitonga/CreditScoreAndOutstandingLoan` |
| BE-API-LOAN-020 | LOAN | POST | `/api/Kitonga/enc` |
| BE-API-LOAN-021 | LOAN | POST | `/api/Kitonga/dec` |
| BE-API-LOAN-024 | LOAN | POST | `/api/DeviceLoan/enc` |
| BE-API-SAVING-001 | SAVING | POST | `/api/Saving/SubscriptionStatus` |
| BE-API-SAVING-002 | SAVING | POST | `/api/Saving/enc` |
| BE-API-SAVING-008 | SAVING | POST | `/api/KibubuPlus/SavingHistory` |
| BE-API-GRPSAV-005 | GRPSAV | POST | `/api/Loan/ChangeGuaranteeMode` |
| BE-API-GRPSAV-007 | GRPSAV | POST | `/api/Loan/ChangeGuarantor` |
| BE-API-GRPSAV-008 | GRPSAV | POST | `/api/Loan/encrypt` |
| BE-API-GRPSAV-009 | GRPSAV | POST | `/api/Loan/decrypt` |
| BE-API-GRPSAV-010 | GRPSAV | POST | `/api/Loan/EncryptLoanRequest` |
| BE-API-GRPSAV-011 | GRPSAV | POST | `/api/Saving/SendContribution` |
| BE-API-GRPSAV-012 | GRPSAV | POST | `/api/Saving/BuyShares` |
| BE-API-GRPSAV-013 | GRPSAV | POST | `/api/Saving/Transfer` |
| BE-API-GRPSAV-014 | GRPSAV | POST | `/api/Saving/QueryMemberPanalPenalties` |
| BE-API-GRPSAV-015 | GRPSAV | POST | `/api/Saving/PayPanalty` |
| BE-API-GRPSAV-016 | GRPSAV | POST | `/api/Saving/PaySocialFund` |
| BE-API-GRPSAV-017 | GRPSAV | POST | `/api/Saving/GetBalanceFee` |
| BE-API-GRPSAV-018 | GRPSAV | POST | `/api/Saving/GetStatementFee` |
| BE-API-GRPSAV-019 | GRPSAV | POST | `/api/Saving/ChangeSharePrice` |
| BE-API-GRPSAV-020 | GRPSAV | POST | `/api/Saving/ChangeBankAccount` |
| BE-API-GRPSAV-021 | GRPSAV | POST | `/api/Saving/encrypt` |
| BE-API-GRPSAV-022 | GRPSAV | POST | `/api/Saving/decrypt` |
| BE-API-GRPSAV-023 | GRPSAV | POST | `/api/Saving/encSendContribution` |
| BE-API-GRPSAV-024 | GRPSAV | POST | `/api/Saving/encTransfer` |
| BE-API-GRPSAV-025 | GRPSAV | POST | `/api/Saving/encQueryMemberPanalties` |
| BE-API-GRPSAV-026 | GRPSAV | POST | `/api/Saving/encPayPanalty` |
| BE-API-GRPSAV-027 | GRPSAV | POST | `/api/Saving/encPaySocialFund` |
| BE-API-GRPSAV-028 | GRPSAV | POST | `/api/Saving/encGetBalanceFee` |
| BE-API-GRPSAV-029 | GRPSAV | POST | `/api/Saving/encGetStatementFee` |
| BE-API-GRPSAV-030 | GRPSAV | POST | `/api/Saving/encChangeSharePrice` |
| BE-API-GRPSAV-033 | GRPSAV | POST | `/api/Group/AddMember` |
| BE-API-GRPSAV-034 | GRPSAV | POST | `/api/Group/GetMembersWithRols` |
| BE-API-GRPSAV-035 | GRPSAV | POST | `/api/Group/GetMembers` |
| BE-API-GRPSAV-036 | GRPSAV | POST | `/api/Group/GetNotifications` |
| BE-API-GRPSAV-037 | GRPSAV | POST | `/api/Group/NotificationApproval` |
| BE-API-GRPSAV-038 | GRPSAV | POST | `/api/Group/RemoveMember` |
| BE-API-GRPSAV-039 | GRPSAV | POST | `/api/Group/UpdateRole` |
| BE-API-GRPSAV-041 | GRPSAV | POST | `/api/Group/ChangeApprover` |
| BE-API-GRPSAV-042 | GRPSAV | POST | `/api/Group/ChangeGroupName` |
| BE-API-GRPSAV-043 | GRPSAV | POST | `/api/Group/UploadGroupImage` |
| BE-API-GRPSAV-044 | GRPSAV | POST | `/api/Group/encrypt` |
| BE-API-GRPSAV-045 | GRPSAV | POST | `/api/Group/decrypt` |
| BE-API-GRPSAV-046 | GRPSAV | POST | `/api/Group/encCreateGroup` |
| BE-API-GRPSAV-047 | GRPSAV | POST | `/api/Group/encGetGroup` |
| BE-API-GRPSAV-048 | GRPSAV | POST | `/api/Group/encAddMember` |
| BE-API-GRPSAV-049 | GRPSAV | POST | `/api/Group/encGetMemberWithRols` |
| BE-API-GRPSAV-050 | GRPSAV | POST | `/api/Group/encGetMembers` |
| BE-API-GRPSAV-051 | GRPSAV | POST | `/api/Group/encGetNotifications` |
| BE-API-GRPSAV-052 | GRPSAV | POST | `/api/Group/encNotificationApproval` |
| BE-API-GRPSAV-053 | GRPSAV | POST | `/api/Group/encRemoveMember` |
| BE-API-GRPSAV-054 | GRPSAV | POST | `/api/Group/encUpdateRole` |
| BE-API-GRPSAV-055 | GRPSAV | POST | `/api/Group/encGetGroupSettings` |
| BE-API-GRPSAV-056 | GRPSAV | POST | `/api/Group/encChangeApprover` |
| BE-API-GRPSAV-062 | GRPSAV | POST | `/api/Loan/encrypt` |
| BE-API-GRPSAV-063 | GRPSAV | POST | `/api/Loan/decrypt` |
| BE-API-GRPSAV-064 | GRPSAV | POST | `/api/Loan/EncryptLoanRequest` |
| BE-API-GRPSAV-065 | GRPSAV | POST | `/api/Loan/EncryptChangeLoanInterestRequest` |
| BE-API-MCHANGO-001 | MCHANGO | POST | `/api/mobile/RTT/CreateRTT` |
| BE-API-MCHANGO-002 | MCHANGO | POST | `/api/mobile/Purpose/CreatePurpose` |
| BE-API-MCHANGO-003 | MCHANGO | POST | `/api/mobile/Purpose/GetPurpose` |
| BE-API-MCHANGO-004 | MCHANGO | POST | `/api/mobile/Purpose/GetAllPurposes` |
| BE-API-MCHANGO-005 | MCHANGO | POST | `/api/mobile/Purpose/UpdatePurpose` |
| BE-API-MCHANGO-006 | MCHANGO | POST | `/api/mobile/Purpose/DeletePurpose` |
| BE-API-MCHANGO-007 | MCHANGO | GET | `/api/web/ChangeAccountGroup/GetAllAccount` |
| BE-API-MCHANGO-008 | MCHANGO | GET | `/api/web/ChangeAccountGroup/ChangeGroup` |
| BE-API-MCHANGO-009 | MCHANGO | POST | `/api/web/ChangeAccountGroup/ChangeGroup` |
| BE-API-MCHANGO-010 | MCHANGO | POST | `/api/mobile/AccountDurationType/CreateAccountDurationType` |
| BE-API-MCHANGO-011 | MCHANGO | POST | `/api/mobile/AccountDurationType/GetAccountDurationType` |
| BE-API-MCHANGO-012 | MCHANGO | POST | `/api/mobile/AccountDurationType/GetAllAccountDurationTypes` |
| BE-API-MCHANGO-013 | MCHANGO | POST | `/api/mobile/AccountDurationType/UpdateAccountDurationType` |
| BE-API-MCHANGO-014 | MCHANGO | POST | `/api/mobile/AccountDurationType/DeleteAccountDurationType` |
| BE-API-MCHANGO-018 | MCHANGO | POST | `/api/mobile/Notification/SendMchangoNotfication` |
| BE-API-MCHANGO-019 | MCHANGO | POST | `/api/web/Encryption/encrypt` |
| BE-API-MCHANGO-020 | MCHANGO | POST | `/api/web/Encryption/decrypt` |
| BE-API-MCHANGO-029 | MCHANGO | POST | `/api/mobile/Transaction/MchangoFeeCheck` |
| BE-API-MCHANGO-035 | MCHANGO | POST | `/api/mobile/Transaction/MchangoCashoutFee` |
| BE-API-MCHANGO-037 | MCHANGO | POST | `/api/mobile/Invitation/CreateEvent` |
| BE-API-MCHANGO-038 | MCHANGO | POST | `/api/mobile/Invitation/UpdateEvent` |
| BE-API-MCHANGO-039 | MCHANGO | POST | `/api/mobile/Invitation/GetEventById` |
| BE-API-MCHANGO-040 | MCHANGO | POST | `/api/mobile/Invitation/GetAllEvents` |
| BE-API-MCHANGO-041 | MCHANGO | POST | `/api/mobile/Invitation/DeleteEventById` |
| BE-API-MCHANGO-043 | MCHANGO | POST | `/api/mobile/Invitation/ValidateInvitationCode` |
| BE-API-MCHANGO-047 | MCHANGO | POST | `/api/mobile/SelfCare/CheckPinStatus` |
| BE-API-MCHANGO-048 | MCHANGO | POST | `/api/mobile/SelfCare/ChangePIN` |
| BE-API-MCHANGO-058 | MCHANGO | GET | `/api/web/AccountReports/GetMyMchangoAccountReport` |
| BE-API-MCHANGO-059 | MCHANGO | GET | `/api/web/AccountReports/GetGroupBalanceReport` |
| BE-API-MCHANGO-060 | MCHANGO | GET | `/api/web/AccountReports/GetMyMchangoAccountStatementReport` |
| BE-API-MCHANGO-061 | MCHANGO | POST | `/api/web/Auth/login` |
| BE-API-MCHANGO-062 | MCHANGO | POST | `/api/web/Account/GetAllActiveAccounts` |
| BE-API-MCHANGO-063 | MCHANGO | POST | `/api/web/Account/ChangeAccountPaymentStatus` |
| BE-API-MCHANGO-064 | MCHANGO | POST | `/api/web/Account/SendMchangoNotfication` |
| BE-API-INSUR-004 | INSUR | POST | `/api/Insurance/GetQuote` |
| BE-API-INSUR-007 | INSUR | POST | `/api/Insurance/PaymentNotification` |
| BE-API-INSUR-008 | INSUR | POST | `/api/Conversion/encGetVehicleDetails` |
| BE-API-INSUR-009 | INSUR | POST | `/api/Conversion/encGetMotorVehicleDetails` |
| BE-API-INSUR-010 | INSUR | POST | `/api/Conversion/encConfirmVehicleRegistration` |
| BE-API-INSUR-011 | INSUR | POST | `/api/Conversion/encGetQuote` |
| BE-API-INSUR-012 | INSUR | POST | `/api/Conversion/encMTPGBillQuery` |
| BE-API-INSUR-013 | INSUR | POST | `/api/Conversion/encPaymentNotification` |
| BE-API-VCARD-002 | VCARD | POST | `/api/CardManagement/GetCardValidity` |
| BE-API-VCARD-007 | VCARD | POST | `/api/CardManagement/DeleteCard` |
| BE-API-VCARD-009 | VCARD | POST | `/api/CardManagement/enc` |
| BE-API-DSTV-004 | DSTV | POST | `/api/DSTV/SubmitPaymentBySmartcard` |
| BE-API-DSTV-005 | DSTV | POST | `/api/DSTV/PaymentConfirmation` |
| BE-API-DSTV-006 | DSTV | POST | `/api/DSTV/CustomerDetailenc` |
| BE-API-DSTV-007 | DSTV | POST | `/api/DSTV/DueAmountenc` |
| BE-API-GSM-006 | GSM | POST | `/api/SelfCare/enc` |
| BE-API-GSM-007 | GSM | POST | `/api/GSMBundles/CheckBalanceAirtimeSmsAndCall` |
| BE-API-GSM-009 | GSM | POST | `/api/GSMBundles/ProductProvision` |
| BE-API-GSM-012 | GSM | POST | `/api/GSMBundles/HomeInternetV2` |
| BE-API-GSM-014 | GSM | POST | `/api/GSMBundles/SuperAppGetSubscriberInfoV2` |
| BE-API-GSM-015 | GSM | POST | `/api/GSMBundles/encrypt` |
| BE-API-GSM-016 | GSM | POST | `/api/GSMBundles/decrypt` |
| BE-API-SELFC-006 | SELFC | POST | `/api/SelfCare/TransactionHistory` |
| BE-API-SELFC-013 | SELFC | POST | `/api/SelfCare/TransactionHistoryDetail` |
| BE-API-SELFC-025 | SELFC | POST | `/api/SelfCare/GetTransactionDetails` |
| BE-API-SELFC-026 | SELFC | POST | `/api/SelfCare/enc` |
| BE-API-SELFC-032 | SELFC | POST | `/api/SelfCare/GenerateQR` |
| BE-API-SELFC-035 | SELFC | POST | `/api/SelfCare/GetMonthlyStatementV1` |
| BE-API-SELFC-036 | SELFC | POST | `/api/Conversion/encUnblockAccount` |
| BE-API-SELFC-037 | SELFC | POST | `/api/Conversion/encTransactionHistory` |
| BE-API-SELFC-038 | SELFC | POST | `/api/Conversion/encPinResetStatus` |
| BE-API-SELFC-039 | SELFC | POST | `/api/Conversion/encPinReset` |
| BE-API-SELFC-040 | SELFC | POST | `/api/Conversion/encCancelPINReset` |
| BE-API-SELFC-041 | SELFC | POST | `/api/Conversion/encGetMonthlyStatement` |
| BE-API-SELFC-042 | SELFC | POST | `/api/Conversion/encInitiateReversal` |
| BE-API-SELFC-043 | SELFC | POST | `/api/Conversion/encPartialReversal` |
| BE-API-SELFC-044 | SELFC | POST | `/api/Conversion/encFetchPendingApproval` |
| BE-API-SELFC-045 | SELFC | POST | `/api/Conversion/encReversalApprove` |
| BE-API-SELFC-046 | SELFC | POST | `/api/Conversion/encMyNumber` |
| BE-API-SELFC-047 | SELFC | POST | `/api/Conversion/encChangePIN` |
| BE-API-SELFC-048 | SELFC | POST | `/api/Conversion/encRegistrationDetail` |
| BE-API-SELFC-049 | SELFC | POST | `/api/Conversion/encFetchTransactions` |
| BE-API-SELFC-050 | SELFC | POST | `/api/Conversion/encMyNumberandMerchantInfo` |
| BE-API-SELFC-051 | SELFC | POST | `/api/Conversion/encLukuToken` |
| BE-API-SELFC-052 | SELFC | POST | `/api/Conversion/decrypt` |
| BE-API-SELFC-055 | SELFC | POST | `/api/BlockNumber/BlockMyNumberRequest` |
| BE-API-SELFC-056 | SELFC | POST | `/api/BlockNumber/encrypt` |
| BE-API-SELFC-057 | SELFC | POST | `/api/BlockNumber/decrypt` |
| BE-API-REWARD-005 | REWARD | POST | `/api/RewardManagement/encGenrateReferrelCode` |
| BE-API-REWARD-006 | REWARD | POST | `/api/RewardManagement/decGenrateReferrelCode` |
| BE-API-REWARD-007 | REWARD | POST | `/api/RewardManagement/encRedeemReferrelCode` |
| BE-API-REWARD-008 | REWARD | POST | `/api/RewardManagement/decRedeemReferrelCode` |
| BE-API-REWARD-009 | REWARD | POST | `/api/RewardManagement/enc` |
| BE-API-REWARD-010 | REWARD | POST | `/api/RewardManagement/dec` |
| BE-API-REWARD-015 | REWARD | POST | `/api/MixxPoints/encGetPointsBalance` |
| BE-API-REWARD-016 | REWARD | POST | `/api/MixxPoints/decGetPointsBalance` |
| BE-API-REWARD-017 | REWARD | POST | `/api/MixxPoints/encGetRewardProducts` |
| BE-API-REWARD-018 | REWARD | POST | `/api/MixxPoints/decGetRewardProducts` |
| BE-API-REWARD-019 | REWARD | POST | `/api/MixxPoints/encRedeemPoints` |
| BE-API-REWARD-020 | REWARD | POST | `/api/MixxPoints/decRedeemPoints` |
| BE-API-REWARD-021 | REWARD | POST | `/api/MixxPoints/encGetRedemptionHistory` |
| BE-API-REWARD-022 | REWARD | POST | `/api/MixxPoints/decGetRedemptionHistory` |
| BE-API-NOTIF-001 | NOTIF | POST | `/api/FCMNotification/sendFCMMessage` |
| BE-API-NOTIF-005 | NOTIF | POST | `/api/Notifications/create` |
| BE-API-NOTIF-006 | NOTIF | POST | `/api/Notifications/CreatePushNotification` |
| BE-API-NOTIF-007 | NOTIF | POST | `/api/Notifications/update` |
| BE-API-NOTIF-008 | NOTIF | POST | `/api/Notifications/delete` |
| BE-API-NOTIF-009 | NOTIF | POST | `/api/Notifications/getNotificationHistory` |
| BE-API-NOTIF-010 | NOTIF | POST | `/api/Notifications/getall` |
| BE-API-NOTIF-011 | NOTIF | POST | `/api/Notifications/getbyid` |
| BE-API-NOTIF-012 | NOTIF | GET | `/api/Notifications/notification-delivery-report` |
| BE-API-NOTIF-013 | NOTIF | POST | `/api/FCMTemplate/GetFCMTemplate` |
| BE-API-NOTIF-014 | NOTIF | POST | `/api/NotificationTemplate/getAll` |
| BE-API-NOTIF-015 | NOTIF | POST | `/api/NotificationTemplate/create` |
| BE-API-NOTIF-016 | NOTIF | POST | `/api/NotificationTemplate/updateStatus` |
| BE-API-NOTIF-017 | NOTIF | POST | `/api/NotificationTemplate/delete` |
| BE-API-NOTIF-018 | NOTIF | POST | `/api/NotificationTemplate/updateDetails` |
| BE-API-NOTIF-019 | NOTIF | GET | `/api/NotificationTemplate/audit-logs` |
| BE-API-EXPENSE-005 | EXPENSE | POST | `/api/AdvanceSalary/GetSalaryAdvanceRequests` |
| BE-API-EXPENSE-015 | EXPENSE | POST | `/api/ExpenseManagement/enc` |

## URL constants not used by a live call

These `UrlConstants` still resolve to a path, but no live `callDioAPI` references them. Some belong to commented-out methods. They were not given API IDs.

| Constant | Path |
|---|---|
| `addTransferSchedule` | `merchant/api/Settlement/AddTransferSchedule` |
| `airTimeBundlesFetch` | `configuration/api/BundlesApp/GetBundles` |
| `contributeInitiateTransaction` | `mchango/api/mobile/Transaction/contributeInitiateTransaction` |
| `fiberGetReferenceNumberValidationChange` | `creditmgt/api/FiberProduct/GetReferenceNumberValidationForCapacityChange` |
| `getKitongaOutstandingLoan` | `loan/api/Kitonga/QueryOutstandingLoan` |
| `getMerchantUsers` | `configuration/api/MerchantManagementApp/GetByMsisdn` |
| `getMyContributions` | `mchango/api/mobile/Transaction/getMyContributions` |
| `getOrdersByDateRange` | `sendmoney/api/StandingOrder/GetOrdersByDateRange` |
| `getOtherInitiator` | `expenses/api/ExpenseManagement/GetOtherInitiator` |
| `getOutstandingLoan` | `loan/api/LoanManagement/GetLoanSummary` |
| `getPrvivligies` | `configuration/api/MerchantManagementApp/GetPrivileges` |
| `requestCheckAuth` | `accounts/api/Profile/CheckAuth` |
| `requestGetAppRating` | `configuration/api/AppRating` |
| `requestGetHorizontalMenuItemsMerchant` | `configuration/api/dashboard` |
| `requestGetbalanceAndProduct` | `loan/api/Kitonga/KitongaBalanceAndProducts` |
| `requestLoanForm` | `loan/1.0.0/api/LM/Loan/GetLoanForm` |
| `requestPostBillPayment` | `billpayment/1.0.0/api/Billing/PostBillPayment` |
| `smGetOrders` | `stock/api/Stock/GetOrders` |
| `superAppGetSubscriberInfo` | `gsm/api/GSMBundles/SuperAppGetSubscriberInfo` |
| `tanzaniaBankVerify` | `fundtransfer/1.0.0/api/Bank/verify` |
| `updateTransferSchedule` | `merchant/api/Settlement/UpdateTransferSchedule` |
| `welcomeBannerSportsEvent` | `configuration/api/test` |

