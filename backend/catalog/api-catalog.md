---
kb_section: backend
type: catalog
ids: [BE-CAT-API]
service: ALL
repo: multi
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: multi
updated: 2026-10-05
confidence: confirmed
---
# API catalog

| ID | Service | Method | Path | Action | Conf. |
|---|---|---|---|---|---|
| BE-API-IDENT-001 | IDENT | POST | /api/Permission/getall | PermissionController.getAll | confirmed |
| BE-API-IDENT-002 | IDENT | POST | /api/Permission/add | PermissionController.add | confirmed |
| BE-API-IDENT-003 | IDENT | POST | /api/Permission/update | PermissionController.update | confirmed |
| BE-API-IDENT-004 | IDENT | POST | /api/Permission/get | PermissionController.get | confirmed |
| BE-API-IDENT-005 | IDENT | POST | /api/Permission/delete | PermissionController.delete | confirmed |
| BE-API-IDENT-006 | IDENT | POST | /api/Permission/getrolebasedall | PermissionController.getrolebasedall | confirmed |
| BE-API-IDENT-007 | IDENT | POST | /api/Menu/getall | MenuController.getAll | confirmed |
| BE-API-IDENT-008 | IDENT | POST | /api/Menu/add | MenuController.add | confirmed |
| BE-API-IDENT-009 | IDENT | POST | /api/Menu/update | MenuController.update | confirmed |
| BE-API-IDENT-010 | IDENT | POST | /api/Menu/get | MenuController.get | confirmed |
| BE-API-IDENT-011 | IDENT | POST | /api/Menu/getsubmenuall | MenuController.getsubmenuall | confirmed |
| BE-API-IDENT-012 | IDENT | POST | /api/Menu/delete | MenuController.delete | confirmed |
| BE-API-IDENT-013 | IDENT | POST | /api/Account/register | AccountController.register | confirmed |
| BE-API-IDENT-014 | IDENT | POST | /api/Account/update | AccountController.update | confirmed |
| BE-API-IDENT-015 | IDENT | POST | /api/Account/delete | AccountController.delete | confirmed |
| BE-API-IDENT-016 | IDENT | POST | /api/Account/login | AccountController.Login | confirmed |
| BE-API-IDENT-017 | IDENT | POST | /api/Account/loginwithad | AccountController.LoginWithAD | confirmed |
| BE-API-IDENT-018 | IDENT | GET | /api/Account/getaduserdetail | AccountController.GetADUserDetail | confirmed |
| BE-API-IDENT-019 | IDENT | POST | /api/Account/login2fa | AccountController.LoginWithOTP | confirmed |
| BE-API-IDENT-020 | IDENT | POST | /api/Account/resendotp | AccountController.ResendOtp | confirmed |
| BE-API-IDENT-021 | IDENT | POST | /api/Account/getusers | AccountController.GetUsers | confirmed |
| BE-API-IDENT-022 | IDENT | POST | /api/Account/logout | AccountController.LogOut | confirmed |
| BE-API-IDENT-023 | IDENT | POST | /api/Account/passwordchangeuser | AccountController.passwordchangeuser | confirmed |
| BE-API-IDENT-024 | IDENT | POST | /api/Account/passwordchange | AccountController.passwordchange | confirmed |
| BE-API-IDENT-025 | IDENT | POST | /api/Account/getroles | AccountController.getroles | confirmed |
| BE-API-IDENT-026 | IDENT | POST | /api/Account/addrole | AccountController.addrole | confirmed |
| BE-API-IDENT-027 | IDENT | POST | /api/Account/updaterole | AccountController.updaterole | confirmed |
| BE-API-IDENT-028 | IDENT | POST | /api/Account/userroles | AccountController.userroles | confirmed |
| BE-API-IDENT-029 | IDENT | POST | /api/Account/adduserrole | AccountController.adduserrole | confirmed |
| BE-API-IDENT-030 | IDENT | POST | /api/Account/removeuserrole | AccountController.removeuserrole | confirmed |
| BE-API-IDENT-031 | IDENT | POST | /api/Account/addroleclaim | AccountController.addroleclaim | confirmed |
| BE-API-IDENT-032 | IDENT | POST | /api/Account/removeroleclaim | AccountController.removeroleclaim | confirmed |
| BE-API-IDENT-033 | IDENT | POST | /api/Account/getAuditLogs | AccountController.getAuditLogs | confirmed |
| BE-API-IDENT-034 | IDENT | GET | /Welcome/Index | WelcomeController.Index | confirmed |
| BE-API-SESS-001 | SESS | POST | /api/Account | AccountController.Auth | confirmed |
| BE-API-SESS-002 | SESS | POST | /api/Account | AccountController.Refresh | confirmed |
| BE-API-SESS-003 | SESS | POST | /api/Account/enc | AccountController.enc_payment | confirmed |
| BE-API-SESS-004 | SESS | POST | /api/Account/decreq | AccountController.dec_req | confirmed |
| BE-API-ACCOUNT-001 | ACCOUNT | POST | /api/QR/DecodeQr | QRController.DecodeQr | confirmed |
| BE-API-ACCOUNT-002 | ACCOUNT | POST | /api/QR/DecodeQrV1 | QRController.DecodeQrV1 | confirmed |
| BE-API-ACCOUNT-003 | ACCOUNT | POST | /api/QR | QRController.GenerateQR | confirmed |
| BE-API-ACCOUNT-004 | ACCOUNT | POST | /api/QR/enc | QRController.enc | confirmed |
| BE-API-ACCOUNT-005 | ACCOUNT | POST | /api/QR/dec | QRController.dec | confirmed |
| BE-API-ACCOUNT-006 | ACCOUNT | POST | /api/Profile | ProfileController.CheckAuth | confirmed |
| BE-API-ACCOUNT-007 | ACCOUNT | POST | /api/Profile | ProfileController.LoginProfile | confirmed |
| BE-API-ACCOUNT-008 | ACCOUNT | POST | /api/Profile | ProfileController.BannerMaintenance | confirmed |
| BE-API-ACCOUNT-009 | ACCOUNT | POST | /api/Profile | ProfileController.MyDevices | confirmed |
| BE-API-ACCOUNT-010 | ACCOUNT | POST | /api/Profile | ProfileController.DeleteDevice | confirmed |
| BE-API-ACCOUNT-011 | ACCOUNT | POST | /api/Profile | ProfileController.AddEditEmail | confirmed |
| BE-API-ACCOUNT-012 | ACCOUNT | POST | /api/Profile | ProfileController.Registration | confirmed |
| BE-API-ACCOUNT-013 | ACCOUNT | POST | /api/Profile | ProfileController.UpdateProfileImage | confirmed |
| BE-API-ACCOUNT-014 | ACCOUNT | POST | /api/Profile | ProfileController.BVS | confirmed |
| BE-API-ACCOUNT-015 | ACCOUNT | POST | /api/Profile | ProfileController.CheckAuthV1 | confirmed |
| BE-API-ACCOUNT-016 | ACCOUNT | POST | /api/Profile | ProfileController.CheckAuthV2 | confirmed |
| BE-API-ACCOUNT-017 | ACCOUNT | POST | /api/Profile | ProfileController.CalculateFeeNIDA | confirmed |
| BE-API-ACCOUNT-018 | ACCOUNT | POST | /api/Profile | ProfileController.HandleNIDAQuestion | confirmed |
| BE-API-ACCOUNT-019 | ACCOUNT | POST | /api/Profile | ProfileController.RegisterAccount | confirmed |
| BE-API-ACCOUNT-020 | ACCOUNT | POST | /api/Profile | ProfileController.DiasporaRegistration | confirmed |
| BE-API-ACCOUNT-021 | ACCOUNT | POST | /api/Profile | ProfileController.UpdateLanguage | confirmed |
| BE-API-ACCOUNT-022 | ACCOUNT | POST | /api/Profile/encCheckAuth | ProfileController.encVerify | confirmed |
| BE-API-ACCOUNT-023 | ACCOUNT | POST | /api/Profile/encDeleteDevice | ProfileController.encDeleteDevice | confirmed |
| BE-API-ACCOUNT-024 | ACCOUNT | POST | /api/Profile/encRegistration | ProfileController.encRegistration | confirmed |
| BE-API-ACCOUNT-025 | ACCOUNT | POST | /api/Profile | ProfileController.encLoginProfile | confirmed |
| BE-API-ACCOUNT-026 | ACCOUNT | POST | /api/Profile/encLoginProfile | ProfileController.encLoginProfile | confirmed |
| BE-API-ACCOUNT-027 | ACCOUNT | POST | /api/Otp | OtpController.GenerateOtp | confirmed |
| BE-API-ACCOUNT-028 | ACCOUNT | POST | /api/Otp | OtpController.VerifyOtp | confirmed |
| BE-API-ACCOUNT-029 | ACCOUNT | POST | /api/Otp | OtpController.GenerateOtpV1 | confirmed |
| BE-API-ACCOUNT-030 | ACCOUNT | POST | /api/Otp | OtpController.VerifyOtpV1 | confirmed |
| BE-API-ACCOUNT-031 | ACCOUNT | POST | /api/Otp/encVerifyOtp | OtpController.encVerifyOtp | confirmed |
| BE-API-ACCOUNT-032 | ACCOUNT | POST | /api/Otp/encGenerateOtp | OtpController.encGenerateOtp | confirmed |
| BE-API-ACCOUNT-033 | ACCOUNT | POST | /api/Favourites/AddFavourite | FavouritesController.AddFavourite | confirmed |
| BE-API-ACCOUNT-034 | ACCOUNT | POST | /api/Favourites/GetFavourite | FavouritesController.GetFavourites | confirmed |
| BE-API-ACCOUNT-035 | ACCOUNT | POST | /api/Favourites/importcsvbillpayment | FavouritesController.ImportBillPayment | confirmed |
| BE-API-ACCOUNT-036 | ACCOUNT | POST | /api/Favourites/importcsvbanktransfer | FavouritesController.ImportBankTransfer | confirmed |
| BE-API-ACCOUNT-037 | ACCOUNT | POST | /api/Favourites/importcsvsendmoney | FavouritesController.ImportSendMoney | confirmed |
| BE-API-ACCOUNT-038 | ACCOUNT | POST | /api/Favourites/importcsvtopup | FavouritesController.ImportFavouritesTopUp | confirmed |
| BE-API-ACCOUNT-039 | ACCOUNT | POST | /api/Favourites/importcsvmerchantpayment | FavouritesController.ImportFavouritesMerchantPayment | confirmed |
| BE-API-ACCOUNT-040 | ACCOUNT | POST | /api/Favourites/enc | FavouritesController.enc | confirmed |
| BE-API-ACCOUNT-041 | ACCOUNT | POST | /api/Favourites/dec | FavouritesController.dec | confirmed |
| BE-API-ACCOUNT-042 | ACCOUNT | POST | /api/Favourites/encGet | FavouritesController.encGet | confirmed |
| BE-API-ACCOUNT-043 | ACCOUNT | POST | /api/Favourites/decGet | FavouritesController.decGet | confirmed |
| BE-API-ACCOUNT-044 | ACCOUNT | POST | /api/Conversion/api/Conversion | ConversionController.Encrypt | confirmed |
| BE-API-ACCOUNT-045 | ACCOUNT | POST | /api/Conversion/Encrypt | ConversionController.Decrypt | confirmed |
| BE-API-ACCOUNT-046 | ACCOUNT | POST | /api/Region | RegionController.GetRegions | confirmed |
| BE-API-ACCOUNT-047 | ACCOUNT | POST | /api/Region | RegionController.GetDistrict | confirmed |
| BE-API-ACCOUNT-048 | ACCOUNT | POST | /api/Region | RegionController.GetCommunes | confirmed |
| BE-API-ACCOUNT-049 | ACCOUNT | POST | /api/Region | RegionController.GetLocalites | confirmed |
| BE-API-ACCOUNT-050 | ACCOUNT | POST | /api/Region/enc | RegionController.enc | confirmed |
| BE-API-ACCOUNT-051 | ACCOUNT | POST | /api/Region/dec | RegionController.dec | confirmed |
| BE-API-WALLET-001 | WALLET | POST | /api/CashOut/cashOutFee | CashOutController.CashOutFee | confirmed |
| BE-API-WALLET-002 | WALLET | POST | /api/CashOut/cashOutPaymentV1 | CashOutController.CashOutPaymentV1 | confirmed |
| BE-API-WALLET-003 | WALLET | POST | /api/CashOut/cashOutPayment | CashOutController.CashOutPayment | confirmed |
| BE-API-WALLET-004 | WALLET | POST | /api/CashOut/encrypt | CashOutController.Encrypt | confirmed |
| BE-API-WALLET-005 | WALLET | POST | /api/CashOut/decrypt | CashOutController.Decrypt | confirmed |
| BE-API-WALLET-006 | WALLET | POST | /api/WalletBalance | WalletBalanceController.GetBalance | confirmed |
| BE-API-WALLET-007 | WALLET | POST | /api/WalletBalance/enc | WalletBalanceController.enc | confirmed |
| BE-API-SEND-001 | SEND | POST | /api/SendMoney | SendMoneyController.VerifySendMoney | confirmed |
| BE-API-SEND-002 | SEND | POST | /api/SendMoney | SendMoneyController.TransferSendMoney | confirmed |
| BE-API-SEND-003 | SEND | POST | /api/SendMoney | SendMoneyController.GetTopFiveGiftTransaction | confirmed |
| BE-API-SEND-004 | SEND | POST | /api/SendMoney | SendMoneyController.GetGift | confirmed |
| BE-API-SEND-005 | SEND | POST | /api/SendMoney/encVerify | SendMoneyController.encVerify | confirmed |
| BE-API-SEND-006 | SEND | POST | /api/SendMoney/encTransfer | SendMoneyController.encTransfer | confirmed |
| BE-API-SEND-007 | SEND | POST | /api/StandingOrder | StandingOrderController.ScheduleOrder | confirmed |
| BE-API-SEND-008 | SEND | POST | /api/StandingOrder | StandingOrderController.GetOrderList | confirmed |
| BE-API-SEND-009 | SEND | POST | /api/StandingOrder | StandingOrderController.GetOrderHistory | confirmed |
| BE-API-SEND-010 | SEND | POST | /api/StandingOrder | StandingOrderController.DeleteOrder | confirmed |
| BE-API-SEND-011 | SEND | POST | /api/StandingOrder | StandingOrderController.GetOrdersByDateRange | confirmed |
| BE-API-SEND-012 | SEND | POST | /api/StandingOrder | StandingOrderController.PauseOrder | confirmed |
| BE-API-SEND-013 | SEND | POST | /api/StandingOrder | StandingOrderController.ResumeOrder | confirmed |
| BE-API-SEND-014 | SEND | POST | /api/ATMCashout | ATMCashoutController.ATMCashoutBankList | confirmed |
| BE-API-SEND-015 | SEND | POST | /api/ATMCashout | ATMCashoutController.ATMCashoutGenerateOtp | confirmed |
