---
kb_section: backend
type: service
ids: [BE-SVC-MCHRPT]
service: MCHRPT
repo: TZ-Tigo-SuperApp-MChangoReportScheduler
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 34ba77f
updated: 2026-10-05
confidence: partial
---

# Data model — MCHRPT

| Entity | Table | Source |
|---|---|---|
| `NotificationTemplates` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Enums/NotificationTemplates.cs` |
| `ReportRequestStatus` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Enums/ReportRequestStatus.cs` |
| `FCMTemplates` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Enums/FCMTemplates.cs` |
| `StringEnum` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Enums/FCMTemplates.cs` |
| `MobileReportType` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Enums/MobileReportType.cs` |
| `TimePeriodEnum` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Enums/TimePeriodEnum.cs` |
| `TransactionTypes` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Enums/TransactionTypes.cs` |
| `RestAPIRequest` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/GenericModel/RestAPIRequest.cs` |
| `PledgeTransactionEntityModel` | `PledgeTransaction` | `TZTigoSuperAppMChangoReportScheduler/Domain/Entities/PledgeTransactionEntityModel.cs` |
| `TransactionHistoryEntityModel` | `TransactionHistory` | `TZTigoSuperAppMChangoReportScheduler/Domain/Entities/TransactionHistoryEntityModel.cs` |
| `PermissionEntityModel` | `Permission` | `TZTigoSuperAppMChangoReportScheduler/Domain/Entities/PermissionEntityModel.cs` |
| `AccountInterestCalculationEntityModel` | `AccountInterestCalculation` | `TZTigoSuperAppMChangoReportScheduler/Domain/Entities/AccountInterestCalculationEntityModel.cs` |
| `RoleEntityModel` | `Role` | `TZTigoSuperAppMChangoReportScheduler/Domain/Entities/RoleEntityModel.cs` |
| `EventEntityModel` | `Event` | `TZTigoSuperAppMChangoReportScheduler/Domain/Entities/EventEntityModel.cs` |
| `AccountDurationTypeEntityModel` | `AccountDurationType` | `TZTigoSuperAppMChangoReportScheduler/Domain/Entities/AccountDurationTypeEntityModel.cs` |
| `InvitationEntityModel` | `Invitation` | `TZTigoSuperAppMChangoReportScheduler/Domain/Entities/InvitationEntityModel.cs` |
| `MChangoReportRequestsEntityModel` | `MchangoReportRequests` | `TZTigoSuperAppMChangoReportScheduler/Domain/Entities/MChangoReportRequestsEntityModel.cs` |
| `PurposeEntityModel` | `Purpose` | `TZTigoSuperAppMChangoReportScheduler/Domain/Entities/PurposeEntityModel.cs` |
| `AccountEntityModel` | `Account` | `TZTigoSuperAppMChangoReportScheduler/Domain/Entities/AccountEntityModel.cs` |
| `BaseEntity` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Entities/BaseEntity.cs` |
| `PrimaryKeyBaseEntity` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Entities/BaseEntity.cs` |
| `ActualTransactionEntityModel` | `ActualTransaction` | `TZTigoSuperAppMChangoReportScheduler/Domain/Entities/ActualTransactionEntityModel.cs` |
| `GrossInterestCalculationEntityModel` | `GrossInterestCalculation` | `TZTigoSuperAppMChangoReportScheduler/Domain/Entities/GrossInterestCalculationEntityModel.cs` |
| `Invitation` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Models/Invitation.cs` |
| `Permission` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Models/Permission.cs` |
| `Purpose` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Models/Purpose.cs` |
| `ActualTransaction` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Models/ActualTransaction.cs` |
| `Account` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Models/Account.cs` |
| `PledgeTransaction` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Models/PledgeTransaction.cs` |
| `TransactionHistory` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Models/TransactionHistory.cs` |
| `MChangoReportRequests` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Models/MChangoReportRequests.cs` |
| `Role` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Models/Role.cs` |
| `InterestCalculation` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Models/InterestCalculation.cs` |
| `LocalSessionManager` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Models/LocalSessionManager.cs` |
| `AccountDurationType` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Models/AccountDurationType.cs` |
| `Event` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Models/Event.cs` |
| `mchangointerestconfiguration` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Models/mchangointerestconfiguration.cs` |
| `TZConfigurationEFContext` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Contexts/TZConfigurationEFContext.cs` |
| `DataContext` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/Contexts/DataContext.cs` |
| `AccountInterestDetails` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/DTOs/Responses/AccountInterestDetails.cs` |
| `Envelope` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/DTOs/Responses/CashoutFeeResponseDTO.cs` |
| `Header` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/DTOs/Responses/CashoutFeeResponseDTO.cs` |
| `Body` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/DTOs/Responses/CashoutFeeResponseDTO.cs` |
| `CalculateFeeResponseDTO` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/DTOs/Responses/CashoutFeeResponseDTO.cs` |
| `ResponseHeader` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/DTOs/Responses/CashoutFeeResponseDTO.cs` |
| `GeneralResponse` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/DTOs/Responses/CashoutFeeResponseDTO.cs` |
| `ResponseBody` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/DTOs/Responses/CashoutFeeResponseDTO.cs` |
| `ParameterType` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/DTOs/Responses/CashoutFeeResponseDTO.cs` |
| `MTPGGetBalanceResponse` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/DTOs/Responses/GetBalanceResponseDTO.cs` |
| `ReportStatementResponseDTO` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/DTOs/Responses/ReportStatementResponseDTO.cs` |
| `ReportResponseDTO` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/DTOs/Responses/ReportResponseDTO.cs` |
| `GenericResponseModel` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/DTOs/BaseResponseModel/GenericResponseModel.cs` |
| `ErrorResponseDto` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/DTOs/BaseResponseModel/ErrorResponseDto.cs` |
| `BaseResponse` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/DTOs/BaseResponseModel/BaseResponse.cs` |
| `ResponseCode` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/DTOs/BaseResponseModel/ResponseCodeResponse.cs` |
| `MTPGGetBalanceRequestDto` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/DTOs/Requests/GetBalanceDto.cs` |
| `EmailRequestDTO` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/DTOs/Requests/EmailRequestDTO.cs` |
| `AttachedFile` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/DTOs/Requests/EmailRequestDTO.cs` |
| `CreateInvitationDto` | `—` | `TZTigoSuperAppMChangoReportScheduler/Domain/DTOs/Requests/CreateInvitationDto.cs` |
