---
kb_section: backend
type: service
ids: [BE-SVC-GSM]
service: GSM
repo: TZ-Tigo-SuperApp-GSM
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 13fe724
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-GSM GSM bundles and SIM self-care
**Repo:** `TZ-Tigo-SuperApp-GSM` · **Type:** service · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `13fe724`
**Purpose:** GSM bundles and SIM self-care

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** MassTransit.RabbitMQ, Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-GSM-001 | `POST /api/SelfCare/InternetSetting` | `SelfCareController.InternetSetting` | SelfCareController.InternetSetting | see contract | confirmed |
| BE-API-GSM-002 | `POST /api/SelfCare/GetPuk` | `SelfCareController.GetPuk` | SelfCareController.GetPuk | see contract | confirmed |
| BE-API-GSM-003 | `POST /api/SelfCare/GetDataUsage` | `SelfCareController.GetDataUsage` | SelfCareController.GetDataUsage | see contract | confirmed |
| BE-API-GSM-004 | `POST /api/SelfCare/GetAvailableData` | `SelfCareController.GetAvailableData` | SelfCareController.GetAvailableData | see contract | confirmed |
| BE-API-GSM-005 | `POST /api/SelfCare/ShareData` | `SelfCareController.ShareData` | SelfCareController.ShareData | see contract | confirmed |
| BE-API-GSM-006 | `POST /api/SelfCare/enc` | `SelfCareController.enc` | SelfCareController.enc | see contract | confirmed |
| BE-API-GSM-007 | `POST /api/GSMBundles/CheckBalanceAirtimeSmsAndCall` | `GSMBundlesController.CheckBalanceAirtimeSmsAndCall` | GSMBundlesController.CheckBalanceAirtimeSmsAndCall | see contract | confirmed |
| BE-API-GSM-008 | `POST /api/GSMBundles/HomeInternet` | `GSMBundlesController.HomeInternet` | GSMBundlesController.HomeInternet | see contract | confirmed |
| BE-API-GSM-009 | `POST /api/GSMBundles/ProductProvision` | `GSMBundlesController.ProductProvision` | GSMBundlesController.ProductProvision | see contract | confirmed |
| BE-API-GSM-010 | `POST /api/GSMBundles/SuperAppGetSubscriberInfo` | `GSMBundlesController.SuperAppGetSubscriberInfo` | GSMBundlesController.SuperAppGetSubscriberInfo | see contract | confirmed |
| BE-API-GSM-011 | `POST /api/GSMBundles/CheckBalanceAirtimeSmsAndCallV2` | `GSMBundlesController.CheckBalanceAirtimeSmsAndCallV2` | GSMBundlesController.CheckBalanceAirtimeSmsAndCallV2 | see contract | confirmed |
| BE-API-GSM-012 | `POST /api/GSMBundles/HomeInternetV2` | `GSMBundlesController.HomeInternetV2` | GSMBundlesController.HomeInternetV2 | see contract | confirmed |
| BE-API-GSM-013 | `POST /api/GSMBundles/ProductProvisionV2` | `GSMBundlesController.ProductProvisionV2` | GSMBundlesController.ProductProvisionV2 | see contract | confirmed |
| BE-API-GSM-014 | `POST /api/GSMBundles/SuperAppGetSubscriberInfoV2` | `GSMBundlesController.SuperAppGetSubscriberInfoV2` | GSMBundlesController.SuperAppGetSubscriberInfoV2 | see contract | confirmed |
| BE-API-GSM-015 | `POST /api/GSMBundles/encrypt` | `GSMBundlesController.Encrypt` | GSMBundlesController.Encrypt | see contract | confirmed |
| BE-API-GSM-016 | `POST /api/GSMBundles/decrypt` | `GSMBundlesController.Decrypt` | GSMBundlesController.Decrypt | see contract | confirmed |

## Dependencies
| Calls | Sync/Async | Why |
|---|---|---|
| CONFIG `CMM` / `ConfigAPIUrl` | Sync | response-code mapping, catalogues |

| Called by | Sync/Async | Why |
|---|---|---|
| Mobile app (direct or via external gateway) | Sync | product APIs |
| WebPortal | Sync | admin screens (IDENT/CONFIG mainly) |

## Data owned
| Entity / table | Purpose |
|---|---|
| `AccountEFContext` / `—` | `TZTigoSuperAppGSM/Domain/DBContext/AccountEFContext.cs` |
| `RepositoryContext` / `—` | `TZTigoSuperAppGSM/Domain/DBContext/RepositoryContext.cs` |
| `ProductProvisionResponse` / `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/ProductProvisionResponse.cs` |
| `HomeInternetResponse` / `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/HomeInternetResponse.cs` |
| `CheckBalanceAirtimeSmsAndCallResponse` / `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/CheckBalanceAirtimeSmsAndCallResponse.cs` |
| `RootObject` / `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/RootObject.cs` |
| `SuperAppGetSubscriberInfoResponse` / `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SuperAppGetSubscriberInfoResponse.cs` |
| `RepositoryManager` / `—` | `TZTigoSuperAppGSM/Domain/Repositories/RepositoryManager.cs` |
| `ConfigurationManagementClient` / `—` | `TZTigoSuperAppGSM/Domain/Repositories/ConfigurationManagementClient.cs` |
| `Token` / `—` | `TZTigoSuperAppGSM/Domain/Models/Token.cs` |
| `BaseEntity` / `—` | `TZTigoSuperAppGSM/Domain/Models/BaseEntity.cs` |
| `HomeInternetRequest` / `—` | `TZTigoSuperAppGSM/Domain/RequestModels/HomeInternetRequest.cs` |
| `RequestModel` / `—` | `TZTigoSuperAppGSM/Domain/RequestModels/RequestModel.cs` |
| `SuperAppGetSubscriberInfoRequest` / `—` | `TZTigoSuperAppGSM/Domain/RequestModels/SuperAppGetSubscriberInfoRequest.cs` |
| `SMSPackageDetails` / `—` | `TZTigoSuperAppGSM/Domain/RequestModels/SMSPackageDetails.cs` |
| `SMSDetail` / `—` | `TZTigoSuperAppGSM/Domain/RequestModels/SMSPackageDetails.cs` |
| `VoicePackageDetails` / `—` | `TZTigoSuperAppGSM/Domain/RequestModels/VoicePackageDetails.cs` |
| `VoiceDetail` / `—` | `TZTigoSuperAppGSM/Domain/RequestModels/VoicePackageDetails.cs` |
| `CheckBalanceAirtimeSmsAndCallRequest` / `—` | `TZTigoSuperAppGSM/Domain/RequestModels/CheckBalanceAirtimeSmsAndCallRequest.cs` |
| `param` / `—` | `TZTigoSuperAppGSM/Domain/RequestModels/CheckBalanceAirtimeSmsAndCallRequest.cs` |
| `ApiRequest` / `—` | `TZTigoSuperAppGSM/Domain/RequestModels/ApiRequest.cs` |
| `DataPackageDetails` / `—` | `TZTigoSuperAppGSM/Domain/RequestModels/DataPackageDetails.cs` |
| `DataDetail` / `—` | `TZTigoSuperAppGSM/Domain/RequestModels/DataPackageDetails.cs` |
| `ProductProvisionRequest` / `—` | `TZTigoSuperAppGSM/Domain/RequestModels/ProductProvisionRequest.cs` |
| `ParameterType` / `—` | `TZTigoSuperAppGSM/Domain/RequestModels/ProductProvisionRequest.cs` |
| `ShareDataResponse` / `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/ShareDataResponse.cs` |
| `ShareDataset` / `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/ShareDataResponse.cs` |
| `ShareDataResParam` / `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/ShareDataResponse.cs` |
| `USSDDataMenuResponse` / `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/ShareDataResponse.cs` |
| `GetPukResponse` / `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/GetPukResponse.cs` |
| `InternetSettingResponse` / `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/InternetSettingResponse.cs` |
| `Result` / `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/InternetSettingResponse.cs` |
| `AvailableDataResponse` / `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/AvailableDataResponse.cs` |
| `TagSet` / `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/AvailableDataResponse.cs` |
| `Param` / `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/AvailableDataResponse.cs` |
| `Dataset` / `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/AvailableDataResponse.cs` |
| `USSDDynMenuResponse` / `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/AvailableDataResponse.cs` |
| `DataUsageResponse` / `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/DataUsageResponse.cs` |
| `AuditLogsRequest` / `—` | `TZTigoSuperAppGSM/Domain/Models/GenericModel/AuditLogsRequest.cs` |
| `productprovision` / `—` | `TZTigoSuperAppGSM/Domain/Models/Entities/productprovision.cs` |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`CacheExpiry`, `CheckBalanceAirtimeSmsAndCall`, `ConfigAPIUrl`, `ConsumerId`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `Encryption_Decryption_Key`, `GSMBundlesURL`, `HomeInternet`, `IV`, `IsRedisCluster`, `MobileSelfCare`, `Origins`, `Password (key name)<redacted-purpose>`, `ProductProvision`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:IsHttpsRabbitMQ`, `RabbitMQ:LogQueueName`, `RabbitMQ:Port`, `RabbitMQ:URL`, `RabbitMQ:Username`, `RedisPassword (key name)<redacted-purpose>`, `RedisURL`, `SaveLogs`, `SendAuditLogsViaService`, `SuperAppDataSharingPackageList`, `SuperAppDataSharingProductProvision`, `SuperAppGetDataUsage`, `SuperAppGetSubscriberInfo`, `SuperAppInternetSettings`, `SuperAppPUK`, `TokenKey`, `Username`, `isEncrypted`, `responseChanel`, `serviceName`

## Open questions
- Gateway public URLs not in-repo.
