---
kb_section: backend
type: service
ids: [BE-SVC-MCHANGO]
service: MCHANGO
repo: TZ-Tigo-SuperApp-MChango
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 7c288ab
updated: 2026-10-05
confidence: partial
---

# Data model — MCHANGO

| Entity | Table | Source |
|---|---|---|
| `EncryptionDTO` | `—` | `TZTigoMChangoService/Domain/EncryptionDTOs/EncryptionDTO.cs` |
| `NotificationTemplates` | `—` | `TZTigoMChangoService/Domain/Enums/NotificationTemplates.cs` |
| `ReportRequestStatus` | `—` | `TZTigoMChangoService/Domain/Enums/ReportRequestStatus.cs` |
| `FCMTemplates` | `—` | `TZTigoMChangoService/Domain/Enums/FCMTemplates.cs` |
| `StringEnum` | `—` | `TZTigoMChangoService/Domain/Enums/FCMTemplates.cs` |
| `MobileReportType` | `—` | `TZTigoMChangoService/Domain/Enums/MobileReportType.cs` |
| `TimePeriodEnum` | `—` | `TZTigoMChangoService/Domain/Enums/TimePeriodEnum.cs` |
| `TransactionTypes` | `—` | `TZTigoMChangoService/Domain/Enums/TransactionTypes.cs` |
| `AccountDurationTypeRepository` | `—` | `TZTigoMChangoService/Domain/Repository/AccountDurationTypeRepository.cs` |
| `AccountRepository` | `—` | `TZTigoMChangoService/Domain/Repository/AccountRepository.cs` |
| `RoleRepository` | `—` | `TZTigoMChangoService/Domain/Repository/RoleRepository.cs` |
| `EventRepository` | `—` | `TZTigoMChangoService/Domain/Repository/EventRepository.cs` |
| `PurposeRepository` | `—` | `TZTigoMChangoService/Domain/Repository/PurposeRepository.cs` |
| `BankTransactionHistoryRepository` | `—` | `TZTigoMChangoService/Domain/Repository/BankTransactionHistoryRepository.cs` |
| `PoolAccountRepository` | `—` | `TZTigoMChangoService/Domain/Repository/PoolAccountRepository.cs` |
| `CashoutTransactionHistoryRepository` | `—` | `TZTigoMChangoService/Domain/Repository/CashoutTransactionHistoryRepository.cs` |
| `PledgeTransactionRepository` | `—` | `TZTigoMChangoService/Domain/Repository/PledgeTransactionRepository.cs` |
| `NotificationRepository` | `—` | `TZTigoMChangoService/Domain/Repository/NotificationRepository.cs` |
| `ActualTransactionRepository` | `—` | `TZTigoMChangoService/Domain/Repository/ActualTransactionRepository.cs` |
| `PermissionRepository` | `—` | `TZTigoMChangoService/Domain/Repository/PermissionRepository.cs` |
| `Repository` | `—` | `TZTigoMChangoService/Domain/Repository/Repository.cs` |
| `ReportRequestRepository` | `—` | `TZTigoMChangoService/Domain/Repository/ReportRequestRepository.cs` |
| `MchangoTransactionHistoryRepository` | `—` | `TZTigoMChangoService/Domain/Repository/MchangoTransactionHistoryRepository.cs` |
| `MchangoQRRepository` | `—` | `TZTigoMChangoService/Domain/Repository/MchangoQRRepository.cs` |
| `MchangoAccountConfigurationRepository` | `—` | `TZTigoMChangoService/Domain/Repository/MchangoAccountConfigurationRepository.cs` |
| `ThirdPartyAPIHistoryRepository` | `—` | `TZTigoMChangoService/Domain/Repository/ThirdPartyAPIHistoryRepository.cs` |
| `InvitationRepository` | `—` | `TZTigoMChangoService/Domain/Repository/InvitationRepository.cs` |
| `TransactionHistoryRepository` | `—` | `TZTigoMChangoService/Domain/Repository/TransactionHistoryRepository.cs` |
| `MchangoInterestConfigurationRepository` | `—` | `TZTigoMChangoService/Domain/Repository/MchangoInterestConfigurationRepository.cs` |
| `AccountRoleRepository` | `—` | `TZTigoMChangoService/Domain/Repository/AccountRoleRepository.cs` |
| `TZSendMoneyEFContext` | `—` | `TZTigoMChangoService/Domain/Data/TZSendMoneyEFContext.cs` |
| `TZConfigurationEFContext` | `—` | `TZTigoMChangoService/Domain/Data/TZConfigurationEFContext.cs` |
| `DataContext` | `—` | `TZTigoMChangoService/Domain/Data/DataContext.cs` |
| `TZNotificationEFContext` | `—` | `TZTigoMChangoService/Domain/Data/TZNotificationEFContext.cs` |
| `FCMNotificationRequest` | `—` | `TZTigoMChangoService/Domain/GenericModel/FCMNotificationRequest.cs` |
| `NotificationTemplate` | `—` | `TZTigoMChangoService/Domain/GenericModel/FCMNotificationRequest.cs` |
| `Parameter` | `—` | `TZTigoMChangoService/Domain/GenericModel/Parameter.cs` |
| `RestAPIRequest` | `—` | `TZTigoMChangoService/Domain/GenericModel/RestAPIRequest.cs` |
| `RestAPINewRequest` | `—` | `TZTigoMChangoService/Domain/GenericModel/RestAPIRequest.cs` |
| `BankTransactionHistoryEntityModel` | `BankTransactionHistory` | `TZTigoMChangoService/Domain/Entities/BankTransactionHistoryEntityModel.cs` |
| `PledgeTransactionEntityModel` | `PledgeTransaction` | `TZTigoMChangoService/Domain/Entities/PledgeTransactionEntityModel.cs` |
| `CashoutTransactionHistoryEntityModel` | `CashoutransactionHistory` | `TZTigoMChangoService/Domain/Entities/CashoutTransactionHistoryEntityModel.cs` |
| `AddNotificationEntityModel` | `—` | `TZTigoMChangoService/Domain/Entities/AddNotificationEntityModel.cs` |
| `NotificationEntityModel` | `Notification` | `TZTigoMChangoService/Domain/Entities/NotificationEntityModel.cs` |
| `PoolAccountEntityModel` | `PoolAccount` | `TZTigoMChangoService/Domain/Entities/PoolAccountEntityModel.cs` |
| `TransactionHistoryEntityModel` | `TransactionHistory` | `TZTigoMChangoService/Domain/Entities/TransactionHistoryEntityModel.cs` |
| `AccountRoleEntityModel` | `AccountRole` | `TZTigoMChangoService/Domain/Entities/AccountRoleEntityModel.cs` |
| `templatetranslation` | `—` | `TZTigoMChangoService/Domain/Entities/NotificationTranslationEntityModel.cs` |
| `PermissionEntityModel` | `Permission` | `TZTigoMChangoService/Domain/Entities/PermissionEntityModel.cs` |
| `notificationtemplates` | `—` | `TZTigoMChangoService/Domain/Entities/NotificationTemplateEntityModel.cs` |
| `AccountInterestCalculationEntityModel` | `AccountInterestCalculation` | `TZTigoMChangoService/Domain/Entities/AccountInterestCalculationEntityModel.cs` |
| `RoleEntityModel` | `Role` | `TZTigoMChangoService/Domain/Entities/RoleEntityModel.cs` |
| `tanqrshortcode` | `—` | `TZTigoMChangoService/Domain/Entities/tanqrshortcode.cs` |
| `ThirdPartyAPIHistoryEntityModel` | `ThirdPartyAPIHistory` | `TZTigoMChangoService/Domain/Entities/ThirdPartyAPIHistoryEntityModel.cs` |
| `RolePermissionEntityModel` | `RolePermission` | `TZTigoMChangoService/Domain/Entities/RolePermissionEntityModel.cs` |
| `EventEntityModel` | `Event` | `TZTigoMChangoService/Domain/Entities/EventEntityModel.cs` |
| `AccountDurationTypeEntityModel` | `AccountDurationType` | `TZTigoMChangoService/Domain/Entities/AccountDurationTypeEntityModel.cs` |
| `MchangoTransactionHistoryEntityModel` | `MchangoTransactionHistory` | `TZTigoMChangoService/Domain/Entities/MchangoTransactionHistoryEntityModel.cs` |
| `InvitationEntityModel` | `Invitation` | `TZTigoMChangoService/Domain/Entities/InvitationEntityModel.cs` |
| `MChangoReportRequestsEntityModel` | `MchangoReportRequests` | `TZTigoMChangoService/Domain/Entities/MChangoReportRequestsEntityModel.cs` |
