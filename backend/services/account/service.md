---
kb_section: backend
type: service
ids: [BE-SVC-ACCOUNT]
service: ACCOUNT
repo: TZ-Tigo-SuperApp-Account
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 5c549d6
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-ACCOUNT Profile, registration, OTP, devices, QR, favourites
**Repo:** `TZ-Tigo-SuperApp-Account` · **Type:** service · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `5c549d6`
**Purpose:** Profile, registration, OTP, devices, QR, favourites

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** MassTransit.RabbitMQ, Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-ACCOUNT-001 | `POST /api/Profile/CheckAuth` | `ProfileController.CheckAuth` | ProfileController.CheckAuth | see contract | confirmed |
| BE-API-ACCOUNT-002 | `POST /api/Profile/LoginProfile` | `ProfileController.LoginProfile` | ProfileController.LoginProfile | see contract | confirmed |
| BE-API-ACCOUNT-003 | `POST /api/Profile/BannerMaintenance` | `ProfileController.BannerMaintenance` | ProfileController.BannerMaintenance | see contract | confirmed |
| BE-API-ACCOUNT-004 | `POST /api/Profile/MyDevices` | `ProfileController.MyDevices` | ProfileController.MyDevices | see contract | confirmed |
| BE-API-ACCOUNT-005 | `POST /api/Profile/DeleteDevice` | `ProfileController.DeleteDevice` | ProfileController.DeleteDevice | see contract | confirmed |
| BE-API-ACCOUNT-006 | `POST /api/Profile/AddEditEmail` | `ProfileController.AddEditEmail` | ProfileController.AddEditEmail | see contract | confirmed |
| BE-API-ACCOUNT-007 | `POST /api/Profile/Registration` | `ProfileController.Registration` | ProfileController.Registration | see contract | confirmed |
| BE-API-ACCOUNT-008 | `POST /api/Profile/UpdateProfileImage` | `ProfileController.UpdateProfileImage` | ProfileController.UpdateProfileImage | see contract | confirmed |
| BE-API-ACCOUNT-009 | `POST /api/Profile/BVS` | `ProfileController.BVS` | ProfileController.BVS | see contract | confirmed |
| BE-API-ACCOUNT-010 | `POST /api/Profile/CheckAuthV1` | `ProfileController.CheckAuthV1` | ProfileController.CheckAuthV1 | see contract | confirmed |
| BE-API-ACCOUNT-011 | `POST /api/Profile/CheckAuthV2` | `ProfileController.CheckAuthV2` | ProfileController.CheckAuthV2 | see contract | confirmed |
| BE-API-ACCOUNT-012 | `POST /api/Profile/CalculateFeeNIDA` | `ProfileController.CalculateFeeNIDA` | ProfileController.CalculateFeeNIDA | see contract | confirmed |
| BE-API-ACCOUNT-013 | `POST /api/Profile/HandleNIDAQuestion` | `ProfileController.HandleNIDAQuestion` | ProfileController.HandleNIDAQuestion | see contract | confirmed |
| BE-API-ACCOUNT-014 | `POST /api/Profile/RegisterAccount` | `ProfileController.RegisterAccount` | ProfileController.RegisterAccount | see contract | confirmed |
| BE-API-ACCOUNT-015 | `POST /api/Profile/DiasporaRegistration` | `ProfileController.DiasporaRegistration` | ProfileController.DiasporaRegistration | see contract | confirmed |
| BE-API-ACCOUNT-016 | `POST /api/Profile/UpdateLanguage` | `ProfileController.UpdateLanguage` | ProfileController.UpdateLanguage | see contract | confirmed |
| BE-API-ACCOUNT-017 | `POST /api/Profile/encCheckAuth` | `ProfileController.encVerify` | ProfileController.encVerify | see contract | confirmed |
| BE-API-ACCOUNT-018 | `POST /api/Profile/encDeleteDevice` | `ProfileController.encDeleteDevice` | ProfileController.encDeleteDevice | see contract | confirmed |
| BE-API-ACCOUNT-019 | `POST /api/Profile/encRegistration` | `ProfileController.encRegistration` | ProfileController.encRegistration | see contract | confirmed |
| BE-API-ACCOUNT-020 | `POST /api/Profile/encLoginProfile` | `ProfileController.encLoginProfile` | ProfileController.encLoginProfile | see contract | confirmed |
| BE-API-ACCOUNT-021 | `POST /api/Profile/encUpdateProfileImage` | `ProfileController.encLoginProfile` | ProfileController.encLoginProfile | see contract | confirmed |
| BE-API-ACCOUNT-022 | `POST /api/QR/DecodeQr` | `QRController.DecodeQr` | QRController.DecodeQr | see contract | confirmed |
| BE-API-ACCOUNT-023 | `POST /api/QR/DecodeQrV1` | `QRController.DecodeQrV1` | QRController.DecodeQrV1 | see contract | confirmed |
| BE-API-ACCOUNT-024 | `POST /api/QR/GenerateQR` | `QRController.GenerateQR` | QRController.GenerateQR | see contract | confirmed |
| BE-API-ACCOUNT-025 | `POST /api/QR/enc` | `QRController.enc` | QRController.enc | see contract | confirmed |
| BE-API-ACCOUNT-026 | `POST /api/QR/dec` | `QRController.dec` | QRController.dec | see contract | partial |
| BE-API-ACCOUNT-027 | `POST /api/Favourites/AddFavourite` | `FavouritesController.AddFavourite` | FavouritesController.AddFavourite | see contract | confirmed |
| BE-API-ACCOUNT-028 | `POST /api/Favourites/GetFavourite` | `FavouritesController.GetFavourites` | FavouritesController.GetFavourites | see contract | confirmed |
| BE-API-ACCOUNT-029 | `POST /api/Favourites/importcsvbillpayment` | `FavouritesController.ImportBillPayment` | FavouritesController.ImportBillPayment | see contract | confirmed |
| BE-API-ACCOUNT-030 | `POST /api/Favourites/importcsvbanktransfer` | `FavouritesController.ImportBankTransfer` | FavouritesController.ImportBankTransfer | see contract | confirmed |
| BE-API-ACCOUNT-031 | `POST /api/Favourites/importcsvsendmoney` | `FavouritesController.ImportSendMoney` | FavouritesController.ImportSendMoney | see contract | confirmed |
| BE-API-ACCOUNT-032 | `POST /api/Favourites/importcsvtopup` | `FavouritesController.ImportFavouritesTopUp` | FavouritesController.ImportFavouritesTopUp | see contract | confirmed |
| BE-API-ACCOUNT-033 | `POST /api/Favourites/importcsvmerchantpayment` | `FavouritesController.ImportFavouritesMerchantPayment` | FavouritesController.ImportFavouritesMerchantPayment | see contract | confirmed |
| BE-API-ACCOUNT-034 | `POST /api/Favourites/enc` | `FavouritesController.enc` | FavouritesController.enc | see contract | confirmed |
| BE-API-ACCOUNT-035 | `POST /api/Favourites/dec` | `FavouritesController.dec` | FavouritesController.dec | see contract | partial |
| BE-API-ACCOUNT-036 | `POST /api/Favourites/encGet` | `FavouritesController.encGet` | FavouritesController.encGet | see contract | confirmed |
| BE-API-ACCOUNT-037 | `POST /api/Favourites/decGet` | `FavouritesController.decGet` | FavouritesController.decGet | see contract | partial |
| BE-API-ACCOUNT-038 | `POST /api/Conversion/Encrypt` | `ConversionController.Encrypt` | ConversionController.Encrypt | see contract | confirmed |
| BE-API-ACCOUNT-039 | `POST /api/Conversion/Decrypt` | `ConversionController.Decrypt` | ConversionController.Decrypt | see contract | partial |
| BE-API-ACCOUNT-040 | `POST /api/Region/GetRegions` | `RegionController.GetRegions` | RegionController.GetRegions | see contract | confirmed |
| BE-API-ACCOUNT-041 | `POST /api/Region/GetDistrict` | `RegionController.GetDistrict` | RegionController.GetDistrict | see contract | confirmed |
| BE-API-ACCOUNT-042 | `POST /api/Region/GetCommunes` | `RegionController.GetCommunes` | RegionController.GetCommunes | see contract | confirmed |
| BE-API-ACCOUNT-043 | `POST /api/Region/GetLocalites` | `RegionController.GetLocalites` | RegionController.GetLocalites | see contract | confirmed |
| BE-API-ACCOUNT-044 | `POST /api/Region/enc` | `RegionController.enc` | RegionController.enc | see contract | confirmed |
| BE-API-ACCOUNT-045 | `POST /api/Region/dec` | `RegionController.dec` | RegionController.dec | see contract | partial |
| BE-API-ACCOUNT-046 | `POST /api/Otp/GenerateOtp` | `OtpController.GenerateOtp` | OtpController.GenerateOtp | see contract | confirmed |
| BE-API-ACCOUNT-047 | `POST /api/Otp/VerifyOtp` | `OtpController.VerifyOtp` | OtpController.VerifyOtp | see contract | confirmed |
| BE-API-ACCOUNT-048 | `POST /api/Otp/GenerateOtpV1` | `OtpController.GenerateOtpV1` | OtpController.GenerateOtpV1 | see contract | confirmed |
| BE-API-ACCOUNT-049 | `POST /api/Otp/VerifyOtpV1` | `OtpController.VerifyOtpV1` | OtpController.VerifyOtpV1 | see contract | confirmed |
| BE-API-ACCOUNT-050 | `POST /api/Otp/encVerifyOtp` | `OtpController.encVerifyOtp` | OtpController.encVerifyOtp | see contract | confirmed |
| BE-API-ACCOUNT-051 | `POST /api/Otp/encGenerateOtp` | `OtpController.encGenerateOtp` | OtpController.encGenerateOtp | see contract | confirmed |

## Dependencies
| Calls | Sync/Async | Why |
|---|---|---|
| CONFIG `CMM` / `ConfigAPIUrl` | Sync | response-code mapping, catalogues |
| Session `SMM` | Sync | establish session |

| Called by | Sync/Async | Why |
|---|---|---|
| Mobile app (direct or via external gateway) | Sync | product APIs |
| WebPortal | Sync | admin screens (IDENT/CONFIG mainly) |

## Data owned
| Entity / table | Purpose |
|---|---|
| `msisdninventory` / `msisdninventory` | EF set |
| `InternationalUserRequest` / `InternationalUserRequests` | EF set |
| `InternationalUserDocument` / `InternationalUserDocuments` | EF set |
| `bannerpromotion` / `bannerpromotions` | EF set |
| `ConsumerQRConfiguration` / `consumerqrconfiguration` | EF set |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`AzureBlobStorage:<redacted-purpose>`, `AzureBlobStorage:DiasporaContainer`, `AzureBlobStorage:ProfileContainer`, `BVSAPI`, `CalculateFeeNIDA`, `ChangePin`, `ConfigAPIUrl`, `DBServerUrl`, `DeviceDetails`, `DeviceRegisterLimit:Limit`, `DeviceRegisterLimit:PeriodInDays`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `Encryption_Decryption_Key`, `FCMNotify`, `FirebaseClient:<redacted-purpose>`, `FirebaseClient:BasePath`, `GetUserDetailURL`, `IV`, `IsRedisCluster`, `LoginURL`, `MFSAccountType`, `MFSUserDetails`, `MFSUserDetailsV2`, `NIDAQuestionAPI`, `OTPSource`, `OtpExpiryInSec`, `OtpLength`, `OtpSMSKeyforAutoFetch`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:IsHttpsRabbitMQ`, `RabbitMQ:LogQueueName`, `RabbitMQ:LogURL`, `RabbitMQ:Port`, `RabbitMQ:QueueName`, `RabbitMQ:Username`, `RedisPassword (key name)<redacted-purpose>`, `RedisURL`, `RegisterAccountAPI`

## Open questions
- Gateway public URLs not in-repo.
