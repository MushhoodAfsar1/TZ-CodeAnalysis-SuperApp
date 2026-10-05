---
kb_section: backend
type: service
ids: [BE-SVC-GSM]
service: GSM
repo: TZ-Tigo-SuperApp-GSM
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 13fe724
updated: 2026-10-05
confidence: partial
---

# Data model — GSM

| Entity | Table | Source |
|---|---|---|
| `AccountEFContext` | `—` | `TZTigoSuperAppGSM/Domain/DBContext/AccountEFContext.cs` |
| `RepositoryContext` | `—` | `TZTigoSuperAppGSM/Domain/DBContext/RepositoryContext.cs` |
| `ProductProvisionResponse` | `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/ProductProvisionResponse.cs` |
| `HomeInternetResponse` | `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/HomeInternetResponse.cs` |
| `CheckBalanceAirtimeSmsAndCallResponse` | `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/CheckBalanceAirtimeSmsAndCallResponse.cs` |
| `RootObject` | `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/RootObject.cs` |
| `SuperAppGetSubscriberInfoResponse` | `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SuperAppGetSubscriberInfoResponse.cs` |
| `RepositoryManager` | `—` | `TZTigoSuperAppGSM/Domain/Repositories/RepositoryManager.cs` |
| `ConfigurationManagementClient` | `—` | `TZTigoSuperAppGSM/Domain/Repositories/ConfigurationManagementClient.cs` |
| `Token` | `—` | `TZTigoSuperAppGSM/Domain/Models/Token.cs` |
| `BaseEntity` | `—` | `TZTigoSuperAppGSM/Domain/Models/BaseEntity.cs` |
| `HomeInternetRequest` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/HomeInternetRequest.cs` |
| `RequestModel` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/RequestModel.cs` |
| `SuperAppGetSubscriberInfoRequest` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/SuperAppGetSubscriberInfoRequest.cs` |
| `SMSPackageDetails` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/SMSPackageDetails.cs` |
| `SMSDetail` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/SMSPackageDetails.cs` |
| `VoicePackageDetails` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/VoicePackageDetails.cs` |
| `VoiceDetail` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/VoicePackageDetails.cs` |
| `CheckBalanceAirtimeSmsAndCallRequest` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/CheckBalanceAirtimeSmsAndCallRequest.cs` |
| `param` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/CheckBalanceAirtimeSmsAndCallRequest.cs` |
| `ApiRequest` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/ApiRequest.cs` |
| `DataPackageDetails` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/DataPackageDetails.cs` |
| `DataDetail` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/DataPackageDetails.cs` |
| `ProductProvisionRequest` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/ProductProvisionRequest.cs` |
| `ParameterType` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/ProductProvisionRequest.cs` |
| `ShareDataResponse` | `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/ShareDataResponse.cs` |
| `ShareDataset` | `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/ShareDataResponse.cs` |
| `ShareDataResParam` | `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/ShareDataResponse.cs` |
| `USSDDataMenuResponse` | `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/ShareDataResponse.cs` |
| `GetPukResponse` | `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/GetPukResponse.cs` |
| `InternetSettingResponse` | `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/InternetSettingResponse.cs` |
| `Result` | `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/InternetSettingResponse.cs` |
| `AvailableDataResponse` | `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/AvailableDataResponse.cs` |
| `TagSet` | `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/AvailableDataResponse.cs` |
| `Param` | `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/AvailableDataResponse.cs` |
| `Dataset` | `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/AvailableDataResponse.cs` |
| `USSDDynMenuResponse` | `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/AvailableDataResponse.cs` |
| `DataUsageResponse` | `—` | `TZTigoSuperAppGSM/Domain/ResponseModels/SelfcareResponseModels/DataUsageResponse.cs` |
| `AuditLogsRequest` | `—` | `TZTigoSuperAppGSM/Domain/Models/GenericModel/AuditLogsRequest.cs` |
| `productprovision` | `—` | `TZTigoSuperAppGSM/Domain/Models/Entities/productprovision.cs` |
| `Tokens` | `—` | `TZTigoSuperAppGSM/Domain/Models/Entities/Tokens.cs` |
| `ResponseCodeResponse` | `—` | `TZTigoSuperAppGSM/Domain/Models/ResponseCode/ResponseCodeResponse.cs` |
| `Parameter` | `—` | `TZTigoSuperAppGSM/Domain/Models/GenericModel/Request/Parameter.cs` |
| `BaseRequest` | `—` | `TZTigoSuperAppGSM/Domain/Models/GenericModel/Request/BaseRequest.cs` |
| `BaseResponse` | `—` | `TZTigoSuperAppGSM/Domain/Models/GenericModel/Response/BaseResponse.cs` |
| `ShareDataRequest` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/SelfcareRequestModels/ShareDataRequest.cs` |
| `ShareDataset` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/SelfcareRequestModels/ShareDataRequest.cs` |
| `ShareDataParam` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/SelfcareRequestModels/ShareDataRequest.cs` |
| `USSDDataMenuRequest` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/SelfcareRequestModels/ShareDataRequest.cs` |
| `AvailableDataRequest` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/SelfcareRequestModels/AvailableDataRequest.cs` |
| `Dataset` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/SelfcareRequestModels/AvailableDataRequest.cs` |
| `Param` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/SelfcareRequestModels/AvailableDataRequest.cs` |
| `USSDDynMenuRequest` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/SelfcareRequestModels/AvailableDataRequest.cs` |
| `DataUsageRequest` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/SelfcareRequestModels/DataUsageRequest.cs` |
| `BundleRequestDto` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/SelfcareRequestModels/DataUsageRequest.cs` |
| `BundleRequest` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/SelfcareRequestModels/DataUsageRequest.cs` |
| `DatasetDto` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/SelfcareRequestModels/DataUsageRequest.cs` |
| `ParamDto` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/SelfcareRequestModels/DataUsageRequest.cs` |
| `InternetSettingRequest` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/SelfcareRequestModels/InternetSettingRequest.cs` |
| `GetPukRequest` | `—` | `TZTigoSuperAppGSM/Domain/RequestModels/SelfcareRequestModels/GetPukRequest.cs` |
