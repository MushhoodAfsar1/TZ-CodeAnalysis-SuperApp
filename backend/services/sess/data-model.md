---
kb_section: backend
type: service
ids: [BE-SVC-SESS]
service: SESS
repo: TZ-Tigo-SuperApp-Session
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 6f24061
updated: 2026-10-05
confidence: partial
---

# Data model — SESS

| Entity | Table | Source |
|---|---|---|
| `AppplicationContext` | `—` | `TZTigoSuperAppSession/Domain/AppplicationContext.cs` |
| `ConnectionStringOptions` | `—` | `TZTigoSuperAppSession/Domain/AppplicationContext.cs` |
| `DataContext` | `—` | `TZTigoSuperAppSession/Domain/DBContext/DataContext.cs` |
| `RepositoryContext` | `—` | `TZTigoSuperAppSession/Domain/DBContext/RepositoryContext.cs` |
| `TokenRepository` | `—` | `TZTigoSuperAppSession/Domain/Repositories/TokenRepository.cs` |
| `ProfileRepository` | `—` | `TZTigoSuperAppSession/Domain/Repositories/ProfileRepository.cs` |
| `RepositoryManager` | `—` | `TZTigoSuperAppSession/Domain/Repositories/RepositoryManager.cs` |
| `RepositoryBase` | `—` | `TZTigoSuperAppSession/Domain/Repositories/RepositoryBase.cs` |
| `BaseResponse` | `—` | `TZTigoSuperAppSession/Domain/Models/BaseResponse.cs` |
| `BaseResponseChannel` | `—` | `TZTigoSuperAppSession/Domain/Models/BaseResponse.cs` |
| `TokenResponse` | `—` | `TZTigoSuperAppSession/Domain/Models/BaseResponse.cs` |
| `BaseModel` | `—` | `TZTigoSuperAppSession/Domain/Models/BaseModel.cs` |
| `AuditLogsRequest` | `—` | `TZTigoSuperAppSession/Domain/Models/GenericModel/AuditLogsRequest.cs` |
| `Tokens` | `—` | `TZTigoSuperAppSession/Domain/Models/Entities/token.cs` |
| `Device` | `—` | `TZTigoSuperAppSession/Domain/Models/Entities/device.cs` |
| `RefreshTokenDto` | `—` | `TZTigoSuperAppSession/Domain/Models/Entities/RefreshTokenDto.cs` |
| `Profile` | `—` | `TZTigoSuperAppSession/Domain/Models/Entities/profile.cs` |
| `ResponseCodeRequest` | `—` | `TZTigoSuperAppSession/Domain/Models/ResponseCode/ResponseCodeRequest.cs` |
| `ResponseCodeResponse` | `—` | `TZTigoSuperAppSession/Domain/Models/ResponseCode/ResponseCodeResponse.cs` |
| `TokenDto` | `—` | `TZTigoSuperAppSession/Domain/Models/SessionManagementModel/TokenDto.cs` |
| `EncryptedRequest` | `—` | `TZTigoSuperAppSession/Domain/Models/GenericModel/Request/EncryptedRequest.cs` |
| `BaseRequest` | `—` | `TZTigoSuperAppSession/Domain/Models/GenericModel/Request/BaseRequest.cs` |
| `BaseResponse` | `—` | `TZTigoSuperAppSession/Domain/Models/GenericModel/Response/BaseResponse.cs` |
