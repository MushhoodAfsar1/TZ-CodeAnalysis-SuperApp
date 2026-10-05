---
kb_section: backend
type: service
ids: [BE-SVC-WALLET]
service: WALLET
repo: TZ-Tigo-SuperApp-Wallet
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 27737b1
updated: 2026-10-05
confidence: partial
---

# Data model — WALLET

| Entity | Table | Source |
|---|---|---|
| `AppplicationContext` | `—` | `TZTigoSuperAppWallet/Domain/AppplicationContext.cs` |
| `ConnectionStringOptions` | `—` | `TZTigoSuperAppWallet/Domain/AppplicationContext.cs` |
| `FTContext` | `—` | `TZTigoSuperAppWallet/Domain/DBContext/FTContext.cs` |
| `AccountEFContext` | `—` | `TZTigoSuperAppWallet/Domain/DBContext/AccountEFContext.cs` |
| `RepositoryContext` | `—` | `TZTigoSuperAppWallet/Domain/DBContext/RepositoryContext.cs` |
| `ConfigurationManagementClient` | `—` | `TZTigoSuperAppWallet/Domain/Repositories/ConfigurationManagementClient.cs` |
| `WalletBalanceRepository` | `—` | `TZTigoSuperAppWallet/Domain/Repositories/WalletBalanceRepository.cs` |
| `Token` | `—` | `TZTigoSuperAppWallet/Domain/RequestModels/Token.cs` |
| `RequestModel` | `—` | `TZTigoSuperAppWallet/Domain/RequestModels/RequestModel.cs` |
| `RestAPIRequest` | `—` | `TZTigoSuperAppWallet/Domain/Models/GenericModel/RestAPIRequest.cs` |
| `AuditLogsRequest` | `—` | `TZTigoSuperAppWallet/Domain/Models/GenericModel/AuditLogsRequest.cs` |
| `cashoutpayment` | `—` | `TZTigoSuperAppWallet/Domain/Models/Entities/cashoutpayment.cs` |
| `Tokens` | `—` | `TZTigoSuperAppWallet/Domain/Models/Entities/Tokens.cs` |
| `BaseEntity` | `—` | `TZTigoSuperAppWallet/Domain/Models/Entities/BaseEntity.cs` |
| `ResponseCodeRequest` | `—` | `TZTigoSuperAppWallet/Domain/Models/ResponseCode/ResponseCodeRequest.cs` |
| `ResponseCodeResponse` | `—` | `TZTigoSuperAppWallet/Domain/Models/ResponseCode/ResponseCodeResponse.cs` |
| `MTPGGetBalanceResponse` | `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/GetBalance/MTPGGetBalanceResponse.cs` |
| `WalletApiResponse` | `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/GetBalance/MTPGGetBalanceResponse.cs` |
| `GetBalanceRequest` | `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/GetBalance/GetBalanceRequest.cs` |
| `CashOutFeeResponseDto` | `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/CashOutFee/CashOutFeeResponseDto.cs` |
| `ParameterType` | `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/CashOutFee/CashOutFeeResponseDto.cs` |
| `CashOutFeeRequestDto` | `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/CashOutFee/CashOutFeeRequestDto.cs` |
| `creditParty` | `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/CashOutFee/CashOutFeeRequestDto.cs` |
| `FCMTemplates` | `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/Enum/FCMTemplates.cs` |
| `StringEnum` | `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/Enum/FCMTemplates.cs` |
| `CashOutPaymentRequestDto` | `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/CashOutPayment/CashOutPaymentRequestDto.cs` |
| `CashOutPaymentResponseDto` | `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/CashOutPayment/CashOutPaymentResponseDto.cs` |
| `FCMNotificationRequest` | `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/FCMNotification/FCMNotificationRequest.cs` |
| `NotificationTemplate` | `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/FCMNotification/FCMNotificationRequest.cs` |
| `EncryptedRequest` | `—` | `TZTigoSuperAppWallet/Domain/Models/GenericModel/Request/EncryptedRequest.cs` |
| `BaseRequest` | `—` | `TZTigoSuperAppWallet/Domain/Models/GenericModel/Request/BaseRequest.cs` |
| `BaseResponse` | `—` | `TZTigoSuperAppWallet/Domain/Models/GenericModel/Response/BaseResponse.cs` |
