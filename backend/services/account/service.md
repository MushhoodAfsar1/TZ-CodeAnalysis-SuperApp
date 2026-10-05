---
kb_section: backend
type: service
ids: [BE-SVC-ACCOUNT]
service: ACCOUNT
repo: TZ-Tigo-SuperApp-Account
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 5c549d6
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-ACCOUNT TZ-Tigo-SuperApp-Account
**Repo:** `TZ-Tigo-SuperApp-Account` · **Type:** service · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `5c549d6`
**Purpose:** Accounts, profile, devices, OTP, QR, favourites

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-ACCOUNT-001 | POST /api/QR/DecodeQr | QRController.DecodeQr | — | none | confirmed |
| BE-API-ACCOUNT-002 | POST /api/QR/DecodeQrV1 | QRController.DecodeQrV1 | — | none | confirmed |
| BE-API-ACCOUNT-003 | POST /api/QR | QRController.GenerateQR | — | none | confirmed |
| BE-API-ACCOUNT-004 | POST /api/QR/enc | QRController.enc | — | none | confirmed |
| BE-API-ACCOUNT-005 | POST /api/QR/dec | QRController.dec | — | none | confirmed |
| BE-API-ACCOUNT-006 | POST /api/Profile | ProfileController.CheckAuth | — | none | confirmed |
| BE-API-ACCOUNT-007 | POST /api/Profile | ProfileController.LoginProfile | — | none | confirmed |
| BE-API-ACCOUNT-008 | POST /api/Profile | ProfileController.BannerMaintenance | — | none | confirmed |
| BE-API-ACCOUNT-009 | POST /api/Profile | ProfileController.MyDevices | — | none | confirmed |
| BE-API-ACCOUNT-010 | POST /api/Profile | ProfileController.DeleteDevice | — | none | confirmed |
| BE-API-ACCOUNT-011 | POST /api/Profile | ProfileController.AddEditEmail | — | none | confirmed |
| BE-API-ACCOUNT-012 | POST /api/Profile | ProfileController.Registration | — | none | confirmed |
| BE-API-ACCOUNT-013 | POST /api/Profile | ProfileController.UpdateProfileImage | — | none | confirmed |
| BE-API-ACCOUNT-014 | POST /api/Profile | ProfileController.BVS | — | none | confirmed |
| BE-API-ACCOUNT-015 | POST /api/Profile | ProfileController.CheckAuthV1 | — | none | confirmed |
| BE-API-ACCOUNT-016 | POST /api/Profile | ProfileController.CheckAuthV2 | — | none | confirmed |
| BE-API-ACCOUNT-017 | POST /api/Profile | ProfileController.CalculateFeeNIDA | — | none | confirmed |
| BE-API-ACCOUNT-018 | POST /api/Profile | ProfileController.HandleNIDAQuestion | — | none | confirmed |
| BE-API-ACCOUNT-019 | POST /api/Profile | ProfileController.RegisterAccount | — | none | confirmed |
| BE-API-ACCOUNT-020 | POST /api/Profile | ProfileController.DiasporaRegistration | — | none | confirmed |
| BE-API-ACCOUNT-021 | POST /api/Profile | ProfileController.UpdateLanguage | — | none | confirmed |
| BE-API-ACCOUNT-022 | POST /api/Profile/encCheckAuth | ProfileController.encVerify | — | none | confirmed |
| BE-API-ACCOUNT-023 | POST /api/Profile/encDeleteDevice | ProfileController.encDeleteDevice | — | none | confirmed |
| BE-API-ACCOUNT-024 | POST /api/Profile/encRegistration | ProfileController.encRegistration | — | none | confirmed |
| BE-API-ACCOUNT-025 | POST /api/Profile | ProfileController.encLoginProfile | — | none | confirmed |
| BE-API-ACCOUNT-026 | POST /api/Profile/encLoginProfile | ProfileController.encLoginProfile | — | none | confirmed |
| BE-API-ACCOUNT-027 | POST /api/Otp | OtpController.GenerateOtp | — | none | confirmed |
| BE-API-ACCOUNT-028 | POST /api/Otp | OtpController.VerifyOtp | — | none | confirmed |
| BE-API-ACCOUNT-029 | POST /api/Otp | OtpController.GenerateOtpV1 | — | none | confirmed |
| BE-API-ACCOUNT-030 | POST /api/Otp | OtpController.VerifyOtpV1 | — | none | confirmed |
| BE-API-ACCOUNT-031 | POST /api/Otp/encVerifyOtp | OtpController.encVerifyOtp | — | none | confirmed |
| BE-API-ACCOUNT-032 | POST /api/Otp/encGenerateOtp | OtpController.encGenerateOtp | — | none | confirmed |
| BE-API-ACCOUNT-033 | POST /api/Favourites/AddFavourite | FavouritesController.AddFavourite | — | none | confirmed |
| BE-API-ACCOUNT-034 | POST /api/Favourites/GetFavourite | FavouritesController.GetFavourites | — | none | confirmed |
| BE-API-ACCOUNT-035 | POST /api/Favourites/importcsvbillpayment | FavouritesController.ImportBillPayment | — | none | confirmed |
| BE-API-ACCOUNT-036 | POST /api/Favourites/importcsvbanktransfer | FavouritesController.ImportBankTransfer | — | none | confirmed |
| BE-API-ACCOUNT-037 | POST /api/Favourites/importcsvsendmoney | FavouritesController.ImportSendMoney | — | none | confirmed |
| BE-API-ACCOUNT-038 | POST /api/Favourites/importcsvtopup | FavouritesController.ImportFavouritesTopUp | — | none | confirmed |
| BE-API-ACCOUNT-039 | POST /api/Favourites/importcsvmerchantpayment | FavouritesController.ImportFavouritesMerchantPayment | — | none | confirmed |
| BE-API-ACCOUNT-040 | POST /api/Favourites/enc | FavouritesController.enc | — | none | confirmed |
| BE-API-ACCOUNT-041 | POST /api/Favourites/dec | FavouritesController.dec | — | none | confirmed |
| BE-API-ACCOUNT-042 | POST /api/Favourites/encGet | FavouritesController.encGet | — | none | confirmed |
| BE-API-ACCOUNT-043 | POST /api/Favourites/decGet | FavouritesController.decGet | — | none | confirmed |
| BE-API-ACCOUNT-044 | POST /api/Conversion/api/Conversion | ConversionController.Encrypt | — | none | confirmed |
| BE-API-ACCOUNT-045 | POST /api/Conversion/Encrypt | ConversionController.Decrypt | — | none | confirmed |
| BE-API-ACCOUNT-046 | POST /api/Region | RegionController.GetRegions | — | none | confirmed |
| BE-API-ACCOUNT-047 | POST /api/Region | RegionController.GetDistrict | — | none | confirmed |
| BE-API-ACCOUNT-048 | POST /api/Region | RegionController.GetCommunes | — | none | confirmed |
| BE-API-ACCOUNT-049 | POST /api/Region | RegionController.GetLocalites | — | none | confirmed |
| BE-API-ACCOUNT-050 | POST /api/Region/enc | RegionController.enc | — | none | confirmed |
| BE-API-ACCOUNT-051 | POST /api/Region/dec | RegionController.dec | — | none | confirmed |


## Dependencies
| Calls | Sync/Async | Why |
|---|---|---|
| Session / Account / Config (typical) | Sync HTTP | Token and profile checks |
| Called by | Sync/Async | Why |
| Mobile app / portal | Sync | User journeys |

## Data owned
| Entity / table | Purpose |
|---|---|
| See data-model.md | — |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`TokenKey`, `isEncrypted`/`is_encrypted`, `Encryption_Decryption_Key`, `IV`, `JwtExpiryMins`, `PostgresConnection` (name only)

## Open questions
Status this run: **deep-analyzed**
