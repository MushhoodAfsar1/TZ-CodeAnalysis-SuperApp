---
kb_section: backend
type: service
ids: [BE-SVC-PORTAL]
service: PORTAL
repo: TZ-Tigo-SuperApp-WebPortal
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: bb69e15
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-PORTAL Angular admin portal (atlantis)
**Repo:** `TZ-Tigo-SuperApp-WebPortal` · **Type:** other · **Stack:** unknown · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `bb69e15`
**Purpose:** Angular admin portal (atlantis)

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** none of the tracked set

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-PORTAL-001 | `POST {baseUrl}/getall` | `invoicefields.component.call001` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-002 | `POST {baseUrl}/delete?id=` | `invoicefields.component.call002` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-003 | `POST {literal}${this.baseUrl}/ContentPlacement/getall` | `content-placement.service.call003` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-004 | `POST {literal}${this.baseUrl}/ContentPlacement/getbyid` | `content-placement.service.call004` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-005 | `POST {literal}${this.baseUrl}/ContentPlacement/dropdown/sections` | `content-placement.service.call005` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-006 | `POST {literal}${this.baseUrl}/ContentPlacement/dropdown/sectionitems` | `content-placement.service.call006` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-007 | `POST {literal}${this.baseUrl}/ContentPlacement/dropdown/subsectionitems` | `content-placement.service.call007` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-008 | `POST {literal}${this.baseUrl}/ContentPlacement/dropdown/placements` | `content-placement.service.call008` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-009 | `POST {baseUrl}/Podcast/PodcastGetAll` | `podcast.service.call009` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-010 | `POST {baseUrl}/Podcast/PodcastCreate` | `podcast.service.call010` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-011 | `POST {baseUrl}/Podcast/PodcastUpdate` | `podcast.service.call011` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-012 | `POST {baseUrl}/Podcast/PodcastDelete?id=` | `podcast.service.call012` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-013 | `GET {literal}${this.baseUrl}/ChangeAccountGroup/ChangeGroup?${queryString}` | `mchangchangegroup.service.call013` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-014 | `POST {baseUrl}/TerrifSlab/getall` | `terrifslab.service.call014` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-015 | `POST {baseUrl}/TerrifSlab/create` | `terrifslab.service.call015` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-016 | `POST {baseUrl}/TerrifSlab/update` | `terrifslab.service.call016` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-017 | `POST {baseUrl}/TerrifSlab/delete?id=` | `terrifslab.service.call017` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-018 | `POST {baseUrl}/ManageFirebase/getall` | `managefirebase.service.call018` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-019 | `POST {baseUrl}/ManageFirebase/update` | `managefirebase.service.call019` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-020 | `POST {baseUrl}/ManageFirebase/refreshKey` | `managefirebase.service.call020` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-021 | `POST {baseUrl}/ManageFirebase/delete?id=` | `managefirebase.service.call021` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-022 | `POST {baseUrl}/HomeCards/getall` | `home-cards.service.call022` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-023 | `POST {baseUrl}/HomeCards/getbyid?id=` | `home-cards.service.call023` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-024 | `POST {baseUrl}/HomeCards/create` | `home-cards.service.call024` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-025 | `POST {baseUrl}/HomeCards/update` | `home-cards.service.call025` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-026 | `POST {baseUrl}/HomeCards/delete?id=` | `home-cards.service.call026` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-027 | `POST {baseUrl}/ResponseCode/importresponsecodes` | `transactionhistory.service.call027` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-028 | `GET {baseUrl}/TransactionHistory/getall` | `transactionhistory.service.call028` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-029 | `POST {baseUrl}/TransactionHistory/create` | `transactionhistory.service.call029` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-030 | `POST {baseUrl}/TransactionHistory/update` | `transactionhistory.service.call030` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-031 | `POST {baseUrl}/TransactionHistory/getbyid?id=` | `transactionhistory.service.call031` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-032 | `POST {baseUrl}/TransactionHistory/delete` | `transactionhistory.service.call032` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-033 | `GET {baseUrl}/AccountReports/GetMyMchangoAccountReport?accountNumber=` | `mchangoreport.service.call033` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-034 | `GET {baseUrl}/AccountReports/GetGroupBalanceReport?accountMsisdn=` | `mchangoreport.service.call034` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-035 | `GET {baseUrl}/AccountReports/GetMyMchangoAccountStatementReport?accountNumber=` | `mchangoreport.service.call035` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-036 | `POST {baseUrl}/BankBillers/importbanksbillers` | `banksbillers.service.call036` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-037 | `POST {baseUrl}/BankBillers/getall?type=` | `banksbillers.service.call037` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-038 | `POST {baseUrl}/BankBillers/create` | `banksbillers.service.call038` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-039 | `POST {baseUrl}/BankBillers/update` | `banksbillers.service.call039` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-040 | `POST {baseUrl}/BankBillers/delete?id=` | `banksbillers.service.call040` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-041 | `POST {baseUrl}/FileValidationRule/getall` | `filevalidationrule.service.call041` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-042 | `POST {baseUrl}/FileValidationRule/getbyid?id=` | `filevalidationrule.service.call042` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-043 | `POST {baseUrl}/FileValidationRule/getbycategory?category=` | `filevalidationrule.service.call043` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-044 | `POST {baseUrl}/FileValidationRule/create` | `filevalidationrule.service.call044` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-045 | `POST {baseUrl}/FileValidationRule/update` | `filevalidationrule.service.call045` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-046 | `POST {baseUrl}/FileValidationRule/delete?id=` | `filevalidationrule.service.call046` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-047 | `GET {baseUrl}/Cards/GetAllAppCards` | `appcard.service.call047` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-048 | `POST {baseUrl}/Cards/CreateAppCardAsync` | `appcard.service.call048` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-049 | `POST {baseUrl}/Cards/delete?id=` | `appcard.service.call049` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-050 | `POST {baseUrl}/Outage/getall` | `appmaintenancemessage.service.call050` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-051 | `POST {baseUrl}/Outage/create` | `appmaintenancemessage.service.call051` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-052 | `POST {baseUrl}/Outage/update` | `appmaintenancemessage.service.call052` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-053 | `POST {baseUrl}/Outage/delete` | `appmaintenancemessage.service.call053` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-054 | `POST {baseUrl}/MerchantReqToPay/GetConfigurations` | `merchantreqtopayservice.service.call054` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-055 | `POST {baseUrl}/MerchantReqToPay/Create` | `merchantreqtopayservice.service.call055` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-056 | `POST {baseUrl}/MerchantReqToPay/Update` | `merchantreqtopayservice.service.call056` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-057 | `POST {baseUrl}/MerchantReqToPay/Delete?id=` | `merchantreqtopayservice.service.call057` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-058 | `POST {baseUrl}/Permission/getall?menu_id=` | `submenupermission.service.call058` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-059 | `POST {baseUrl}/Permission/add` | `submenupermission.service.call059` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-060 | `POST {baseUrl}/Permission/update` | `submenupermission.service.call060` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-061 | `POST {baseUrl}/Permission/delete?id=` | `submenupermission.service.call061` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-062 | `POST {baseUrl}/Permission/get?menu_id=` | `submenupermission.service.call062` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-063 | `POST {baseUrl}/Permission/getrolebasedall?menu_id=` | `submenupermission.service.call063` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-064 | `POST {baseUrl}/UserJourney/getall` | `userjourney.service.call064` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-065 | `POST {baseUrl}/UserJourney/create` | `userjourney.service.call065` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-066 | `POST {baseUrl}/UserJourney/update` | `userjourney.service.call066` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-067 | `POST {baseUrl}/UserJourney/delete?id=` | `userjourney.service.call067` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-068 | `POST {baseUrl}/Banner/getall` | `banner.service.call068` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-069 | `POST {baseUrl}/Banner/GetFlowId` | `banner.service.call069` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-070 | `POST {baseUrl}/Banner/create` | `banner.service.call070` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-071 | `POST {baseUrl}/Banner/update` | `banner.service.call071` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-072 | `POST {baseUrl}/Banner/delete?id=` | `banner.service.call072` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-073 | `POST {baseUrl}/Banner/getbyid?id=` | `banner.service.call073` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-074 | `POST {baseUrl}/RemittanceLimits/getall` | `remittance.service.call074` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-075 | `POST {baseUrl}/RemittanceLimits/create` | `remittance.service.call075` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-076 | `POST {baseUrl}/RemittanceLimits/update` | `remittance.service.call076` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-077 | `POST {baseUrl}/RemittanceLimits/delete?id=` | `remittance.service.call077` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-078 | `POST {baseUrl}/AppChannelOs/getall?countryid=` | `appchannelos.service.call078` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-079 | `POST {baseUrl}/Country/getall` | `country.service.call079` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-080 | `POST {literal}${this.baseUrl}/loanprotect/get` | `loan-insurance.service.call080` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-081 | `POST {literal}${this.baseUrl}/loanprotect/save` | `loan-insurance.service.call081` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-082 | `POST {literal}${this.baseUrl}/category/getall` | `loan-insurance.service.call082` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-083 | `POST {literal}${this.baseUrl}/category/save` | `loan-insurance.service.call083` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-084 | `POST {literal}${this.baseUrl}/category/delete?id=${id}` | `loan-insurance.service.call084` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-085 | `POST {literal}${this.baseUrl}/product/getall` | `loan-insurance.service.call085` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-086 | `POST {literal}${this.baseUrl}/product/getbyid?id=${id}` | `loan-insurance.service.call086` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-087 | `POST {literal}${this.baseUrl}/product/save` | `loan-insurance.service.call087` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-088 | `POST {literal}${this.baseUrl}/product/delete?id=${id}` | `loan-insurance.service.call088` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-089 | `POST {literal}${this.baseUrl}/screentext/getall${query}` | `loan-insurance.service.call089` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-090 | `POST {literal}${this.baseUrl}/screentext/save` | `loan-insurance.service.call090` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-091 | `POST {literal}${this.baseUrl}/screentext/delete?id=${id}` | `loan-insurance.service.call091` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-092 | `POST {literal}${this.baseUrl}/claim/get` | `loan-insurance.service.call092` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-093 | `POST {literal}${this.baseUrl}/claim/save` | `loan-insurance.service.call093` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-094 | `POST {baseUrl}/MchangoQR/getall` | `mchangoqrconfig.service .call094` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-095 | `POST {baseUrl}/MchangoQR/create` | `mchangoqrconfig.service .call095` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-096 | `POST {baseUrl}/MchangoQR/update` | `mchangoqrconfig.service .call096` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-097 | `POST {baseUrl}/MchangoQR/delete?id=` | `mchangoqrconfig.service .call097` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-098 | `POST {baseUrl}/ConsumerQR/getall` | `consumerqrconfig.service.call098` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-099 | `POST {baseUrl}/ConsumerQR/create` | `consumerqrconfig.service.call099` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-100 | `POST {baseUrl}/ConsumerQR/update` | `consumerqrconfig.service.call100` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-101 | `POST {baseUrl}/ConsumerQR/delete?id=` | `consumerqrconfig.service.call101` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-102 | `POST {baseUrl}/SectionItem/getall` | `sectionitem.service.call102` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-103 | `POST {baseUrl}/SectionItem/getsectionitemsbysectionid?id=` | `sectionitem.service.call103` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-104 | `POST {baseUrl}/SectionItem/create` | `sectionitem.service.call104` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-105 | `POST {baseUrl}/SectionItem/update` | `sectionitem.service.call105` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-106 | `POST {baseUrl}/SectionItem/delete?id=` | `sectionitem.service.call106` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-107 | `POST {baseUrl}/TerrifTransferType/getall` | `terriftransfertype.service.call107` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-108 | `POST {baseUrl}/TerrifTransferType/create` | `terriftransfertype.service.call108` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-109 | `POST {baseUrl}/TerrifTransferType/update` | `terriftransfertype.service.call109` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-110 | `POST {baseUrl}/TerrifTransferType/delete?id=` | `terriftransfertype.service.call110` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-111 | `POST {baseUrl}/DeviceBlocking/importfile` | `deviceblocking.service.call111` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-112 | `POST {baseUrl}/DeviceBlocking/getall` | `deviceblocking.service.call112` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-113 | `POST {baseUrl}/DeviceBlocking/create` | `deviceblocking.service.call113` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-114 | `POST {baseUrl}/DeviceBlocking/update` | `deviceblocking.service.call114` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-115 | `POST {baseUrl}/DeviceBlocking/delete?id=` | `deviceblocking.service.call115` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-116 | `POST {baseUrl}/DeviceBlocking/getAllDevices?msisdn=` | `deviceblocking.service.call116` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-117 | `POST {baseUrl}/DeviceBlocking/updateBlocking` | `deviceblocking.service.call117` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-118 | `POST {baseUrl}/RegisteredDevices/getall` | `registereddevices.service.call118` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-119 | `POST {baseUrl}/RegisteredDevices/delete?id=` | `registereddevices.service.call119` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-120 | `POST {baseUrl}/MchangoInterest/getall` | `mchangointerestconfig.service.call120` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-121 | `POST {baseUrl}/MchangoInterest/create` | `mchangointerestconfig.service.call121` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-122 | `POST {baseUrl}/MchangoInterest/update` | `mchangointerestconfig.service.call122` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-123 | `POST {baseUrl}/MchangoInterest/delete?id=` | `mchangointerestconfig.service.call123` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-124 | `POST {baseUrl}/TvPressOffers/getall` | `tvpressoffers.service.call124` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-125 | `POST {baseUrl}/TvPressOffers/create` | `tvpressoffers.service.call125` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-126 | `POST {baseUrl}/TvPressOffers/update` | `tvpressoffers.service.call126` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-127 | `POST {baseUrl}/TvPressOffers/delete?id=` | `tvpressoffers.service.call127` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-128 | `POST {baseUrl}/Themes/getallthemecategories` | `giftthemecategories.service.call128` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-129 | `POST {baseUrl}/Themes/createthemecategory` | `giftthemecategories.service.call129` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-130 | `POST {baseUrl}/Themes/updatethemecategory` | `giftthemecategories.service.call130` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-131 | `POST {baseUrl}/Themes/deletethemecategory?id=` | `giftthemecategories.service.call131` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-132 | `POST {literal}${this.apiUrl}/FiberProduct/create` | `fiberproduct.service.call132` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-133 | `GET {literal}${this.apiUrl}/FiberProduct/getallBO` | `fiberproduct.service.call133` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-134 | `POST {literal}${this.apiUrl}/FiberProduct/update` | `fiberproduct.service.call134` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-135 | `POST {literal}${this.apiUrl}/FiberProduct/delete` | `fiberproduct.service.call135` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-136 | `POST {literal}${this.apiUrl}/FiberProduct/setenable` | `fiberproduct.service.call136` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-137 | `POST {baseUrl}/Notifications/getall` | `notifications.service.call137` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-138 | `POST {baseUrl}/Notifications/getbyid?notificationId=` | `notifications.service.call138` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-139 | `POST {baseUrl}/Notifications/create` | `notifications.service.call139` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-140 | `POST {baseUrl}/Notifications/update` | `notifications.service.call140` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-141 | `POST {baseUrl}/Notifications/importCSV?base64_CSV=` | `notifications.service.call141` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-142 | `POST {baseUrl}/Notifications/delete` | `notifications.service.call142` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-143 | `POST {baseUrl}/Notifications/getNotificationHistory` | `notifications.service.call143` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-144 | `POST {baseUrl}/Notifications/CreatePushNotification` | `notifications.service.call144` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-145 | `POST {baseUrl}/Language/getall` | `language.service.call145` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-146 | `POST {baseUrl}/Channel/getall` | `channel.service.call146` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-147 | `POST {baseUrl}/Channel/getallbycountryid?id=` | `channel.service.call147` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-148 | `POST {baseUrl}/Config/create` | `config.service.call148` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-149 | `POST {baseUrl}/Config/update` | `config.service.call149` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-150 | `POST {baseUrl}/Config/getall` | `config.service.call150` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-151 | `POST {baseUrl}/Config/getbyid?id=` | `config.service.call151` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-152 | `GET {baseUrl}/MixxPointsCategories/getall` | `mixxpointscategories.service.call152` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-153 | `POST {baseUrl}/MixxPointsCategories/create` | `mixxpointscategories.service.call153` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-154 | `POST {baseUrl}/MixxPointsCategories/update` | `mixxpointscategories.service.call154` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-155 | `POST {baseUrl}/MixxPointsCategories/getbyid?id=` | `mixxpointscategories.service.call155` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-156 | `POST {baseUrl}/MixxPointsCategories/delete` | `mixxpointscategories.service.call156` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-157 | `POST {baseUrl}/Merchant/getall` | `merchant.service.call157` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-158 | `POST {baseUrl}/Merchant/create` | `merchant.service.call158` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-159 | `POST {baseUrl}/Merchant/update` | `merchant.service.call159` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-160 | `POST {baseUrl}/Merchant/importCSV` | `merchant.service.call160` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-161 | `POST {baseUrl}/Merchant/delete?id=` | `merchant.service.call161` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-162 | `POST {baseUrl}/TerrifTransactionFee/getall` | `terriftransactionfee.service.call162` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-163 | `POST {baseUrl}/TerrifTransactionFee/create` | `terriftransactionfee.service.call163` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-164 | `POST {baseUrl}/TerrifTransactionFee/update` | `terriftransactionfee.service.call164` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-165 | `POST {baseUrl}/TerrifTransactionFee/delete?id=` | `terriftransactionfee.service.call165` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-166 | `POST {baseUrl}/Menu/getall` | `menupermission.service.call166` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-167 | `POST {baseUrl}/Menu/getsubmenuall?menu_id=` | `menupermission.service.call167` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-168 | `POST {baseUrl}/Menu/add` | `menupermission.service.call168` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-169 | `POST {baseUrl}/Menu/update` | `menupermission.service.call169` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-170 | `POST {baseUrl}/Menu/delete?id=` | `menupermission.service.call170` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-171 | `POST {baseUrl}/TerrifAmountType/getall` | `amounttype.service.call171` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-172 | `POST {baseUrl}/TerrifAmountType/create` | `amounttype.service.call172` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-173 | `POST {baseUrl}/TerrifAmountType/update` | `amounttype.service.call173` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-174 | `POST {baseUrl}/TerrifAmountType/delete?id=` | `amounttype.service.call174` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-175 | `POST {baseUrl}/RewardManagement/getallreferralcodes` | `rewardmanagement.service.call175` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-176 | `POST {baseUrl}/RewardManagement/getallreferrallimits` | `rewardmanagement.service.call176` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-177 | `POST {baseUrl}/RewardManagement/updatereferrallimits` | `rewardmanagement.service.call177` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-178 | `POST {baseUrl}/RewardManagement/createbonustype` | `rewardmanagement.service.call178` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-179 | `POST {baseUrl}/RewardManagement/deletebonustype?id=` | `rewardmanagement.service.call179` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-180 | `POST {baseUrl}/RewardManagement/getallbonustype` | `rewardmanagement.service.call180` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-181 | `POST {baseUrl}/RewardManagement/updatebonustype` | `rewardmanagement.service.call181` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-182 | `POST {baseUrl}/RewardManagement/createbonusproducts` | `rewardmanagement.service.call182` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-183 | `POST {baseUrl}/RewardManagement/deletebonusproducts?id=` | `rewardmanagement.service.call183` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-184 | `POST {baseUrl}/RewardManagement/getallbonusproducts` | `rewardmanagement.service.call184` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-185 | `POST {baseUrl}/RewardManagement/updatebonusproducts` | `rewardmanagement.service.call185` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-186 | `POST {baseUrl}/Bundles/importbundles` | `bundles.service.call186` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-187 | `POST {baseUrl}/Bundles/getall?type=` | `bundles.service.call187` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-188 | `POST {baseUrl}/Bundles/create` | `bundles.service.call188` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-189 | `POST {baseUrl}/Bundles/update` | `bundles.service.call189` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-190 | `POST {baseUrl}/Bundles/delete?id=` | `bundles.service.call190` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-191 | `POST {baseUrl}/Bundles/bulkDelete` | `bundles.service.call191` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-192 | `POST {baseUrl}/Bundles/getall` | `bundles.service.call192` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-193 | `POST {baseUrl}/Bundles/getallnetworkbundle` | `bundles.service.call193` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-194 | `POST {baseUrl}/Bundles/createnetworkbundle` | `bundles.service.call194` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-195 | `POST {baseUrl}/Bundles/updatenetworkbundle` | `bundles.service.call195` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-196 | `POST {baseUrl}/Bundles/deletenetworkbundle?id=` | `bundles.service.call196` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-197 | `POST {baseUrl}/Compalints/getall` | `complaints.service.call197` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-198 | `POST {baseUrl}/Compalints/getbyid?sectionid=` | `complaints.service.call198` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-199 | `POST {baseUrl}/DashboardLayout/getall` | `dashboard-layout.service.call199` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-200 | `POST {baseUrl}/DashboardLayout/getbyid?id=` | `dashboard-layout.service.call200` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-201 | `POST {baseUrl}/DashboardLayout/create` | `dashboard-layout.service.call201` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-202 | `POST {baseUrl}/DashboardLayout/update` | `dashboard-layout.service.call202` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-203 | `POST {baseUrl}/DashboardLayout/delete?id=` | `dashboard-layout.service.call203` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-204 | `POST {baseUrl}/Themes/getallthemes` | `giftthemes.service.call204` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-205 | `POST {baseUrl}/Themes/createtheme` | `giftthemes.service.call205` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-206 | `POST {baseUrl}/Themes/updatetheme` | `giftthemes.service.call206` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-207 | `POST {baseUrl}/Themes/deletetheme?id=` | `giftthemes.service.call207` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-208 | `POST {baseUrl}/NotificationTemplate/getAll` | `mchangonotificationtemplatesconfig.service.call208` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-209 | `POST {baseUrl}/NotificationTemplate/create` | `mchangonotificationtemplatesconfig.service.call209` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-210 | `POST {baseUrl}/NotificationTemplate/updateDetails` | `mchangonotificationtemplatesconfig.service.call210` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-211 | `POST {baseUrl}/NotificationTemplate/updateStatus` | `mchangonotificationtemplatesconfig.service.call211` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-212 | `GET {literal}${this.baseUrl}/AirtimeOperator/GetAll` | `airtimeoperator.service.call212` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-213 | `POST {literal}${this.baseUrl}/AirtimeOperator/Create` | `airtimeoperator.service.call213` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-214 | `POST {literal}${this.baseUrl}/AirtimeOperator/Update` | `airtimeoperator.service.call214` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-215 | `POST {literal}${this.baseUrl}/AirtimeOperator/Delete?id=` | `airtimeoperator.service.call215` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-216 | `POST {baseUrl}/DashboardConfig/getall` | `dashboard-config.service.call216` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-217 | `POST {baseUrl}/DashboardConfig/getbyid?id=` | `dashboard-config.service.call217` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-218 | `POST {baseUrl}/DashboardConfig/create` | `dashboard-config.service.call218` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-219 | `POST {baseUrl}/DashboardConfig/update` | `dashboard-config.service.call219` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-220 | `POST {baseUrl}/DashboardConfig/delete?id=` | `dashboard-config.service.call220` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-221 | `POST {baseUrl}/DashboardConfig/publish?id=` | `dashboard-config.service.call221` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-222 | `POST {baseUrl}/DashboardConfig/getpublished` | `dashboard-config.service.call222` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-223 | `POST {baseUrl}/AppVersions/getall` | `appversion.service.call223` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-224 | `POST {baseUrl}/getAuditLogs` | `auditlogs.service.call224` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-225 | `POST {literal}${this.baseUrl}/dashboard/selfonboarding/items` | `selfonboardingitem.service.call225` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-226 | `POST {baseUrl}/WhiteList/getall` | `whitelistinventory.service.call226` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-227 | `POST {baseUrl}/WhiteList/GetById?id=` | `whitelistinventory.service.call227` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-228 | `POST {baseUrl}/WhiteList/create` | `whitelistinventory.service.call228` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-229 | `POST {baseUrl}/WhiteList/update` | `whitelistinventory.service.call229` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-230 | `POST {baseUrl}/WhiteList/delete?id=` | `whitelistinventory.service.call230` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-231 | `POST {literal}${this.baseUrl}/HalalWalletSubscription/getall` | `halal-wallet-subscription.service.call231` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-232 | `POST {literal}${this.baseUrl}/HalalWalletSubscription/getbyid` | `halal-wallet-subscription.service.call232` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-233 | `POST {literal}${this.baseUrl}/HalalWalletSubscription/create` | `halal-wallet-subscription.service.call233` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-234 | `POST {literal}${this.baseUrl}/HalalWalletSubscription/update` | `halal-wallet-subscription.service.call234` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-235 | `POST {literal}${this.baseUrl}/HalalWalletSubscription/delete` | `halal-wallet-subscription.service.call235` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-236 | `POST {baseUrl}/HomeLayout/getall` | `home-layout.service.call236` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-237 | `POST {baseUrl}/HomeLayout/getbyid?id=` | `home-layout.service.call237` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-238 | `POST {baseUrl}/HomeLayout/create` | `home-layout.service.call238` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-239 | `POST {baseUrl}/HomeLayout/update` | `home-layout.service.call239` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-240 | `POST {baseUrl}/HomeLayout/delete?id=` | `home-layout.service.call240` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-241 | `GET {baseUrl}/ResponseCode/getall` | `responsecode.service.call241` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-242 | `POST {baseUrl}/ResponseCode/create` | `responsecode.service.call242` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-243 | `POST {baseUrl}/ResponseCode/update` | `responsecode.service.call243` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-244 | `POST {baseUrl}/ResponseCode/getbyid?id=` | `responsecode.service.call244` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-245 | `POST {baseUrl}/ResponseCode/delete?id=` | `responsecode.service.call245` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-246 | `POST {baseUrl}/TerrifSubscriber/getall` | `terrifsubscriber.service.call246` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-247 | `POST {baseUrl}/TerrifSubscriber/create` | `terrifsubscriber.service.call247` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-248 | `POST {baseUrl}/TerrifSubscriber/update` | `terrifsubscriber.service.call248` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-249 | `POST {baseUrl}/TerrifSubscriber/delete?id=` | `terrifsubscriber.service.call249` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-250 | `POST {baseUrl}/ImageSubCategories/getall` | `imagesubcategory.service.call250` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-251 | `POST {baseUrl}/ImageSubCategories/create` | `imagesubcategory.service.call251` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-252 | `POST {baseUrl}/ImageSubCategories/update` | `imagesubcategory.service.call252` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-253 | `POST {baseUrl}/ImageSubCategories/delete?id=` | `imagesubcategory.service.call253` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-254 | `POST {baseUrl}/ImageCategories/getall` | `imagecategory.service.call254` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-255 | `POST {baseUrl}/ImageCategories/create` | `imagecategory.service.call255` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-256 | `POST {baseUrl}/ImageCategories/update` | `imagecategory.service.call256` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-257 | `POST {baseUrl}/ImageCategories/delete?id=` | `imagecategory.service.call257` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-258 | `POST {literal}${this.baseUrl}/getall` | `loan-insurance-msisdn-whitelist.service.call258` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-259 | `POST {literal}${this.baseUrl}/getbyid?id=${id}` | `loan-insurance-msisdn-whitelist.service.call259` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-260 | `POST {literal}${this.baseUrl}/create` | `loan-insurance-msisdn-whitelist.service.call260` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-261 | `POST {literal}${this.baseUrl}/update` | `loan-insurance-msisdn-whitelist.service.call261` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-262 | `POST {literal}${this.baseUrl}/delete?id=${id}` | `loan-insurance-msisdn-whitelist.service.call262` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-263 | `POST {literal}${this.baseUrl}/importfile` | `loan-insurance-msisdn-whitelist.service.call263` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-264 | `POST {literal}${this.baseUrl}/downloadtemplate` | `loan-insurance-msisdn-whitelist.service.call264` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-265 | `POST {baseUrl}/MerchantQR/GetAll` | `merchantqrconfiguration.service.call265` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-266 | `POST {baseUrl}/MerchantQR/Create` | `merchantqrconfiguration.service.call266` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-267 | `POST {baseUrl}/MerchantQR/Update` | `merchantqrconfiguration.service.call267` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-268 | `POST {baseUrl}/MerchantQR/Delete?id=` | `merchantqrconfiguration.service.call268` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-269 | `POST {baseUrl}/TimeBasedIcon/gettimebasedsections` | `time-based-icon.service.call269` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-270 | `POST {baseUrl}/TimeBasedIcon/gettimebasedsubsections` | `time-based-icon.service.call270` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-271 | `POST {baseUrl}/TimeBasedIcon/getall` | `time-based-icon.service.call271` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-272 | `POST {baseUrl}/TimeBasedIcon/create` | `time-based-icon.service.call272` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-273 | `POST {baseUrl}/TimeBasedIcon/update` | `time-based-icon.service.call273` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-274 | `POST {baseUrl}/TimeBasedIcon/delete?id=` | `time-based-icon.service.call274` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-275 | `POST {baseUrl}/MchangoAccount/getall` | `mchangoaccountconfig.service.call275` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-276 | `POST {baseUrl}/MchangoAccount/create` | `mchangoaccountconfig.service.call276` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-277 | `POST {baseUrl}/MchangoAccount/update` | `mchangoaccountconfig.service.call277` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-278 | `POST {baseUrl}/MchangoAccount/delete?id=` | `mchangoaccountconfig.service.call278` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-279 | `POST {baseUrl}/login` | `auth.service.call279` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-280 | `POST {baseUrl}/loginwithad` | `auth.service.call280` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-281 | `POST {baseUrl}/login2fa` | `auth.service.call281` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-282 | `POST {baseUrl}/resendotp` | `auth.service.call282` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-283 | `POST {baseUrl}/register` | `auth.service.call283` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-284 | `POST {baseUrl}/update` | `auth.service.call284` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-285 | `POST {baseUrl}/delete` | `auth.service.call285` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-286 | `POST {baseUrl}/passwordchangeuser` | `auth.service.call286` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-287 | `POST {baseUrl}/passwordchange` | `auth.service.call287` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-288 | `POST {baseUrl}/userroles` | `auth.service.call288` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-289 | `POST {baseUrl}/adduserrole` | `auth.service.call289` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-290 | `POST {baseUrl}/removeuserrole` | `auth.service.call290` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-291 | `POST {baseUrl}/addroleclaim` | `auth.service.call291` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-292 | `POST {baseUrl}/removeroleclaim?roleid=` | `auth.service.call292` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-293 | `GET {baseUrl}/Acquirer/getall` | `acquirer.service.call293` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-294 | `POST {baseUrl}/Acquirer/create` | `acquirer.service.call294` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-295 | `POST {baseUrl}/Acquirer/update` | `acquirer.service.call295` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-296 | `POST {baseUrl}/Acquirer/getbyid?id=` | `acquirer.service.call296` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-297 | `POST {baseUrl}/Acquirer/delete` | `acquirer.service.call297` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-298 | `POST {literal}${this.appBaseUrl}/Dashboard/kikoba/items` | `kikobadashboarditem.service.call298` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-299 | `POST {baseUrl}/Section/getall` | `section.service.call299` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-300 | `POST {baseUrl}/Section/create` | `section.service.call300` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-301 | `POST {baseUrl}/Section/update` | `section.service.call301` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-302 | `POST {baseUrl}/Section/delete?id=` | `section.service.call302` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-303 | `POST {baseUrl}/TerrifUnit/getall` | `terrifunit.service.call303` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-304 | `POST {baseUrl}/TerrifUnit/create` | `terrifunit.service.call304` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-305 | `POST {baseUrl}/TerrifUnit/update` | `terrifunit.service.call305` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-306 | `POST {baseUrl}/TerrifUnit/delete?id=` | `terrifunit.service.call306` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-307 | `POST {baseUrl}/MenuItems/getall` | `menu-items.service.call307` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-308 | `POST {baseUrl}/MenuItems/getchildren` | `menu-items.service.call308` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-309 | `POST {baseUrl}/MenuItems/getbyid?id=` | `menu-items.service.call309` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-310 | `POST {baseUrl}/MenuItems/create` | `menu-items.service.call310` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-311 | `POST {baseUrl}/MenuItems/update` | `menu-items.service.call311` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-312 | `POST {baseUrl}/MenuItems/delete?id=` | `menu-items.service.call312` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-313 | `POST {baseUrl}/SubSectionItem/importfile` | `subsectionitem.service.call313` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-314 | `POST {baseUrl}/SubSectionItem/getall` | `subsectionitem.service.call314` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-315 | `POST {baseUrl}/SubSectionItem/create` | `subsectionitem.service.call315` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-316 | `POST {baseUrl}/SubSectionItem/update` | `subsectionitem.service.call316` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-317 | `POST {baseUrl}/SubSectionItem/delete?id=` | `subsectionitem.service.call317` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-318 | `GET {baseUrl}/Registration/get` | `applicationuser.service.call318` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-319 | `GET {baseUrl}/StandingOrderMapping/getall` | `standingordermapping.service.call319` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-320 | `POST {baseUrl}/StandingOrderMapping/create` | `standingordermapping.service.call320` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-321 | `POST {baseUrl}/StandingOrderMapping/update` | `standingordermapping.service.call321` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-322 | `POST {baseUrl}/StandingOrderMapping/getbyid?id=` | `standingordermapping.service.call322` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-323 | `POST {baseUrl}/StandingOrderMapping/delete` | `standingordermapping.service.call323` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-324 | `POST {baseUrl}/Faq/getall` | `faq.service.call324` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-325 | `POST {baseUrl}/Faq/getbyid?sectionid=` | `faq.service.call325` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-326 | `POST {baseUrl}/Faq/Create` | `faq.service.call326` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-327 | `POST {baseUrl}/Faq/update` | `faq.service.call327` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-328 | `POST {baseUrl}/Faq/delete?id=` | `faq.service.call328` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-329 | `POST {baseUrl}/Stocks/GetStocks` | `stock.service.call329` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-330 | `POST {baseUrl}/Stock/getbyid?id=` | `stock.service.call330` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-331 | `POST {baseUrl}/Stock/create` | `stock.service.call331` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-332 | `POST {baseUrl}/Stocks/UpdateStocks` | `stock.service.call332` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-333 | `POST {baseUrl}/Stocks/SyncStocks` | `stock.service.call333` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-334 | `POST {baseUrl}/Account/getusers` | `accountservice.service.call334` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-335 | `POST {baseUrl}/Account/logout` | `accountservice.service.call335` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-336 | `POST {baseUrl}/AFTTC/getall` | `aft-tc-bo.service.call336` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-337 | `POST {baseUrl}/AFTTC/getbyid?id=` | `aft-tc-bo.service.call337` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-338 | `POST {baseUrl}/AFTTC/create` | `aft-tc-bo.service.call338` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-339 | `POST {baseUrl}/AFTTC/update` | `aft-tc-bo.service.call339` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-340 | `POST {baseUrl}/AFTTC/delete?id=` | `aft-tc-bo.service.call340` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-341 | `POST {baseUrl}/Country/getlist` | `imt-bo.service.call341` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-342 | `POST {baseUrl}/Country/getbyid?id=` | `imt-bo.service.call342` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-343 | `POST {baseUrl}/Country/create` | `imt-bo.service.call343` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-344 | `POST {baseUrl}/Country/update` | `imt-bo.service.call344` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-345 | `POST {baseUrl}/Country/delete?id=` | `imt-bo.service.call345` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-346 | `POST {baseUrl}/BanksAndMnos/bank/getall` | `imt-bo.service.call346` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-347 | `POST {baseUrl}/BanksAndMnos/bank/getbyid?id=` | `imt-bo.service.call347` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-348 | `POST {baseUrl}/BanksAndMnos/bank/create` | `imt-bo.service.call348` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-349 | `POST {baseUrl}/BanksAndMnos/bank/update` | `imt-bo.service.call349` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-350 | `POST {baseUrl}/BanksAndMnos/bank/delete?id=` | `imt-bo.service.call350` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-351 | `POST {baseUrl}/BanksAndMnos/mno/getall` | `imt-bo.service.call351` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-352 | `POST {baseUrl}/BanksAndMnos/mno/getbyid?id=` | `imt-bo.service.call352` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-353 | `POST {baseUrl}/BanksAndMnos/mno/create` | `imt-bo.service.call353` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-354 | `POST {baseUrl}/BanksAndMnos/mno/update` | `imt-bo.service.call354` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-355 | `POST {baseUrl}/BanksAndMnos/mno/delete?id=` | `imt-bo.service.call355` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-356 | `POST {baseUrl}/ImtBankFields/getall` | `imt-bo.service.call356` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-357 | `POST {baseUrl}/ImtBankFields/getbyid?id=` | `imt-bo.service.call357` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-358 | `POST {baseUrl}/ImtBankFields/create` | `imt-bo.service.call358` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-359 | `POST {baseUrl}/ImtBankFields/update` | `imt-bo.service.call359` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-360 | `POST {baseUrl}/ImtBankFields/delete?id=` | `imt-bo.service.call360` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-361 | `GET {baseUrl}/Mmp/MmpCity/getall` | `mmp-bo.service.call361` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-362 | `POST {baseUrl}/Mmp/MmpCity/create` | `mmp-bo.service.call362` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-363 | `POST {baseUrl}/Mmp/MmpCity/update` | `mmp-bo.service.call363` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-364 | `POST {baseUrl}/Mmp/MmpCity/getbyid?id=` | `mmp-bo.service.call364` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-365 | `POST {baseUrl}/Mmp/MmpCity/delete` | `mmp-bo.service.call365` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-366 | `GET {baseUrl}/Mmp/MmpRegion/getall` | `mmp-bo.service.call366` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-367 | `POST {baseUrl}/Mmp/MmpRegion/create` | `mmp-bo.service.call367` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-368 | `POST {baseUrl}/Mmp/MmpRegion/update` | `mmp-bo.service.call368` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-369 | `POST {baseUrl}/Mmp/MmpRegion/delete` | `mmp-bo.service.call369` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-370 | `GET {baseUrl}/Mmp/MmpDistrict/getall` | `mmp-bo.service.call370` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-371 | `POST {baseUrl}/Mmp/MmpDistrict/create` | `mmp-bo.service.call371` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-372 | `POST {baseUrl}/Mmp/MmpDistrict/update` | `mmp-bo.service.call372` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-373 | `POST {baseUrl}/Mmp/MmpDistrict/delete` | `mmp-bo.service.call373` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-374 | `GET {baseUrl}/Mmp/MmpWard/getall` | `mmp-bo.service.call374` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-375 | `POST {baseUrl}/Mmp/MmpWard/create` | `mmp-bo.service.call375` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-376 | `POST {baseUrl}/Mmp/MmpWard/update` | `mmp-bo.service.call376` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-377 | `POST {baseUrl}/Mmp/MmpWard/delete` | `mmp-bo.service.call377` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-378 | `GET {baseUrl}/Mmp/MmpCategory/getall` | `mmp-bo.service.call378` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-379 | `POST {baseUrl}/Mmp/MmpCategory/create` | `mmp-bo.service.call379` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-380 | `POST {baseUrl}/Mmp/MmpCategory/update` | `mmp-bo.service.call380` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-381 | `POST {baseUrl}/Mmp/MmpCategory/getbyid?id=` | `mmp-bo.service.call381` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-382 | `POST {baseUrl}/Mmp/MmpCategory/delete` | `mmp-bo.service.call382` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-383 | `GET {baseUrl}/Mmp/MmpSubCategory/getall` | `mmp-bo.service.call383` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-384 | `POST {baseUrl}/Mmp/MmpSubCategory/create` | `mmp-bo.service.call384` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-385 | `POST {baseUrl}/Mmp/MmpSubCategory/update` | `mmp-bo.service.call385` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-386 | `POST {baseUrl}/Mmp/MmpSubCategory/getbyid?id=` | `mmp-bo.service.call386` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-387 | `POST {baseUrl}/Mmp/MmpSubCategory/delete` | `mmp-bo.service.call387` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-388 | `GET {baseUrl}/Mmp/MmpMccSubCategory/getall` | `mmp-bo.service.call388` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-389 | `POST {baseUrl}/Mmp/MmpMccSubCategory/create` | `mmp-bo.service.call389` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-390 | `POST {baseUrl}/Mmp/MmpMccSubCategory/update` | `mmp-bo.service.call390` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-391 | `POST {baseUrl}/Mmp/MmpMccSubCategory/getbyid?id=` | `mmp-bo.service.call391` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-392 | `POST {baseUrl}/Mmp/MmpMccSubCategory/delete` | `mmp-bo.service.call392` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-393 | `GET {baseUrl}/Mmp/MmpAuthorities/getall` | `mmp-bo.service.call393` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-394 | `POST {baseUrl}/Mmp/MmpAuthorities/create` | `mmp-bo.service.call394` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-395 | `POST {baseUrl}/Mmp/MmpAuthorities/update` | `mmp-bo.service.call395` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-396 | `POST {baseUrl}/Mmp/MmpAuthorities/delete` | `mmp-bo.service.call396` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-397 | `GET {baseUrl}/Mmp/MmpAuthorities/getmmpoptions` | `mmp-bo.service.call397` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-398 | `GET {baseUrl}/Lks/LksBank/getall` | `mmp-bo.service.call398` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-399 | `POST {baseUrl}/Lks/LksBank/sync` | `mmp-bo.service.call399` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-400 | `POST {baseUrl}/Lks/LksBank/create` | `mmp-bo.service.call400` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-401 | `POST {baseUrl}/Lks/LksBank/update` | `mmp-bo.service.call401` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-402 | `POST {baseUrl}/Lks/LksBank/delete` | `mmp-bo.service.call402` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-403 | `POST {baseUrl}/Lks/LksBiller/sync` | `mmp-bo.service.call403` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-404 | `GET {baseUrl}/Lks/LksBiller/sections/getall` | `mmp-bo.service.call404` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-405 | `POST {baseUrl}/Lks/LksBiller/sections/create` | `mmp-bo.service.call405` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-406 | `POST {baseUrl}/Lks/LksBiller/sections/update` | `mmp-bo.service.call406` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-407 | `POST {baseUrl}/Lks/LksBiller/sections/delete` | `mmp-bo.service.call407` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-408 | `GET {baseUrl}/Lks/LksBiller/groups/getall` | `mmp-bo.service.call408` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-409 | `POST {baseUrl}/Lks/LksBiller/groups/create` | `mmp-bo.service.call409` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-410 | `POST {baseUrl}/Lks/LksBiller/groups/update` | `mmp-bo.service.call410` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-411 | `POST {baseUrl}/Lks/LksBiller/groups/delete` | `mmp-bo.service.call411` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-412 | `GET {baseUrl}/Lks/LksBiller/billers/getall` | `mmp-bo.service.call412` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-413 | `POST {baseUrl}/Lks/LksBiller/billers/create` | `mmp-bo.service.call413` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-414 | `POST {baseUrl}/Lks/LksBiller/billers/update` | `mmp-bo.service.call414` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-415 | `POST {baseUrl}/Lks/LksBiller/billers/delete` | `mmp-bo.service.call415` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-416 | `GET {baseUrl}/Lks/LksMomo/getall` | `mmp-bo.service.call416` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-417 | `POST {baseUrl}/Lks/LksMomo/sync` | `mmp-bo.service.call417` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-418 | `POST {baseUrl}/Lks/LksMomo/create` | `mmp-bo.service.call418` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-419 | `POST {baseUrl}/Lks/LksMomo/update` | `mmp-bo.service.call419` | portal client | X-User-Session | confirmed |
| BE-API-PORTAL-420 | `POST {baseUrl}/Lks/LksMomo/delete` | `mmp-bo.service.call420` | portal client | X-User-Session | confirmed |

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
| — | no EF sets parsed |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
—

## Open questions
- Gateway public URLs not in-repo.
