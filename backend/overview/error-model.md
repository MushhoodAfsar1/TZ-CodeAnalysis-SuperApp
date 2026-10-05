---
kb_section: backend
type: overview
ids: [BE-OV-ERR]
service: ALL
repo: multi
repo_ref: checked-out
repo_sha: multi
updated: 2026-10-05
confidence: confirmed
---

# Error model

## Handler envelope (`BaseResponse<T>`)
`success`, `responseCode`, `responseMessage_en`, `responseMessage_fr`, `transactionStatus`, `errorDescription`, `appVersionInfo`, `responseData`.

## HTTP mapping (`ApiResponseHandler.CreateResponse`)
Looks up CONFIG `GET api/ResponseCodeApp/get-response-code-details/{code}/{lang}/{channel}[/{service}/{method}]`.
- success true → HTTP 200 if code `"200"` else 201; body omits errorDescription.
- success false → HTTP 500 if code `"500"` else 400; body uses `errorDescription`.

## Filters
| Source | HTTP | Body |
|---|---|---|
| SessionValidationFilter | 410 | `success`, `responseCode`, `errordescription`, `responseData` |
| DeviceFilter (ACCOUNT) | 423 | `errorDescription` |
| Action catch | 500 | `success=false`, `responseCode=500`, `errorDescription=Internal Server Error` |
| GlobalErrorHandlingMiddleware | swallows / logs | not a standard ProblemDetails envelope |

No `ProblemDetails` usage found.
