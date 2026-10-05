---
kb_section: backend
type: service
ids: [BE-SVC-MERCH]
service: MERCH
repo: TZ-Tigo-SuperApp-Merchant
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 2367767
updated: 2026-10-05
confidence: partial
---

# Data model — MERCH

| Entity | Table | Source |
|---|---|---|
| `BaseEntity` | `—` | `TZTigoSuperAppMerchant/Domain/BaseEntity.cs` |
| `EntityDetailRequest` | `—` | `TZTigoSuperAppMerchant/Data/RequestModel/EntityDetailRequest.cs` |
| `CreateEntityUserRequest` | `—` | `TZTigoSuperAppMerchant/Data/RequestModel/CreateEntityUserRequest.cs` |
| `EntityContactDetail` | `—` | `TZTigoSuperAppMerchant/Data/RequestModel/CreateEntityUserRequest.cs` |
| `CreatePrivilegesList` | `—` | `TZTigoSuperAppMerchant/Data/RequestModel/CreateEntityUserRequest.cs` |
| `EntityDetailResponse` | `—` | `TZTigoSuperAppMerchant/Data/ResponseModel/EntityDetailResponse.cs` |
| `ResponseMapEntity` | `—` | `TZTigoSuperAppMerchant/Data/ResponseModel/EntityDetailResponse.cs` |
| `ResponseData` | `—` | `TZTigoSuperAppMerchant/Data/ResponseModel/EntityDetailResponse.cs` |
| `ResData` | `—` | `TZTigoSuperAppMerchant/Data/ResponseModel/EntityDetailResponse.cs` |
| `EntityOfficerDetails` | `—` | `TZTigoSuperAppMerchant/Data/ResponseModel/EntityDetailResponse.cs` |
| `EntityDocumentDetails` | `—` | `TZTigoSuperAppMerchant/Data/ResponseModel/EntityDetailResponse.cs` |
| `EntityDetail` | `—` | `TZTigoSuperAppMerchant/Data/ResponseModel/EntityDetailResponse.cs` |
| `OtherDetails` | `—` | `TZTigoSuperAppMerchant/Data/ResponseModel/EntityDetailResponse.cs` |
| `EntityAddressDetails` | `—` | `TZTigoSuperAppMerchant/Data/ResponseModel/EntityDetailResponse.cs` |
| `EntityContactDetails` | `—` | `TZTigoSuperAppMerchant/Data/ResponseModel/EntityDetailResponse.cs` |
| `TZAccountEFContext` | `—` | `TZTigoSuperAppMerchant/Domain/DBContext/TZAccountEFContext.cs` |
| `TZSendMoneyEFContext` | `—` | `TZTigoSuperAppMerchant/Domain/DBContext/TZSendMoneyEFContext.cs` |
| `TZMerchantContext` | `—` | `TZTigoSuperAppMerchant/Domain/DBContext/TZMerchantContext.cs` |
| `TZConfigurationEFContext` | `—` | `TZTigoSuperAppMerchant/Domain/DBContext/TZConfigurationEFContext.cs` |
| `cashout` | `—` | `TZTigoSuperAppMerchant/Domain/Entities/Cashout.cs` |
| `scheduleSubscriber` | `—` | `TZTigoSuperAppMerchant/Domain/Entities/ScheduleSubscriber.cs` |
| `transaction` | `—` | `TZTigoSuperAppMerchant/Domain/Entities/Transaction.cs` |
| `MerchantQRConfiguration` | `—` | `TZTigoSuperAppMerchant/Domain/Entities/MerchantQRConfiguration.cs` |
| `schedule` | `—` | `TZTigoSuperAppMerchant/Domain/Entities/Schedule.cs` |
| `DynamicQRRecord` | `—` | `TZTigoSuperAppMerchant/Domain/Entities/DynamicQRRecord.cs` |
| `BillPayment` | `—` | `TZTigoSuperAppMerchant/Domain/Entities/BillPayment.cs` |
| `RequestToPay` | `—` | `TZTigoSuperAppMerchant/Domain/Entities/RequestToPay.cs` |
| `TransferSchedule` | `—` | `TZTigoSuperAppMerchant/Domain/Entities/TransferSchedule.cs` |
| `MerchantTransactionMapping` | `—` | `TZTigoSuperAppMerchant/Domain/Entities/MerchantTransactionMapping.cs` |
| `settlementtc` | `—` | `TZTigoSuperAppMerchant/Domain/Entities/SettlementTC.cs` |
| `ReqToPayTransfer` | `—` | `TZTigoSuperAppMerchant/Domain/Entities/ReqToPayTransfer.cs` |
| `PaymentMethod` | `—` | `TZTigoSuperAppMerchant/Domain/Enum/PaymentMethod.cs` |
| `FCMTemplates` | `—` | `TZTigoSuperAppMerchant/Domain/Enum/FCMTemplates.cs` |
| `StringEnum` | `—` | `TZTigoSuperAppMerchant/Domain/Enum/FCMTemplates.cs` |
| `RequestStatus` | `—` | `TZTigoSuperAppMerchant/Domain/Enum/RequestStatus.cs` |
| `AccountRepository` | `—` | `TZTigoSuperAppMerchant/Domain/Repositories/AccountRepository.cs` |
| `SettlementRepository` | `—` | `TZTigoSuperAppMerchant/Domain/Repositories/SettlementRepository.cs` |
| `NotificationRepository` | `—` | `TZTigoSuperAppMerchant/Domain/Repositories/NotificationRepository.cs` |
| `SendMoneyRepository` | `—` | `TZTigoSuperAppMerchant/Domain/Repositories/SendMoneyRepository.cs` |
| `SchedularRepository` | `—` | `TZTigoSuperAppMerchant/Domain/Repositories/SchedularRepository.cs` |
| `CashoutRepository` | `—` | `TZTigoSuperAppMerchant/Domain/Repositories/CashoutRepository.cs` |
| `RequestToPayRepositroy` | `—` | `TZTigoSuperAppMerchant/Domain/Repositories/RequestToPayRepository.cs` |
| `TanQRshortCode` | `—` | `TZTigoSuperAppMerchant/Domain/Entities/SendMoneyDb/TanQRshortCode.cs` |
| `Profile` | `—` | `TZTigoSuperAppMerchant/Domain/Entities/AccountDb/Profile.cs` |
| `Device` | `—` | `TZTigoSuperAppMerchant/Domain/Entities/AccountDb/Device.cs` |
| `Tokens` | `—` | `TZTigoSuperAppMerchant/Domain/Entities/AccountDb/Tokens.cs` |
