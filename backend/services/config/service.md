---
kb_section: backend
type: service
ids: [BE-SVC-CONFIG]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-CONFIG Configuration / BO / app CMS APIs
**Repo:** `TZ-Tigo-SuperApp-Configuration` · **Type:** config/infra · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `9c00072`
**Purpose:** Configuration / BO / app CMS APIs

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** Dapper, MassTransit.RabbitMQ, Microsoft.AspNetCore.Authentication.JwtBearer, Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, Serilog, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-CONFIG-001 | `POST /api/FiberProduct/create` | `FiberProductController.Create` | FiberProductController.Create | see contract | confirmed |
| BE-API-CONFIG-002 | `GET /api/FiberProduct/getallBO` | `FiberProductController.GetAll` | FiberProductController.GetAll | see contract | partial |
| BE-API-CONFIG-003 | `POST /api/FiberProduct/getall` | `FiberProductController.GetAll` | FiberProductController.GetAll | see contract | confirmed |
| BE-API-CONFIG-004 | `POST /api/FiberProduct/update` | `FiberProductController.Update` | FiberProductController.Update | see contract | confirmed |
| BE-API-CONFIG-005 | `POST /api/FiberProduct/delete` | `FiberProductController.DeleteSoft` | FiberProductController.DeleteSoft | see contract | partial |
| BE-API-CONFIG-006 | `POST /api/FiberProduct/setenable` | `FiberProductController.SetEnable` | FiberProductController.SetEnable | see contract | confirmed |
| BE-API-CONFIG-007 | `POST /api/MerchantQR/Create` | `MerchantQRController.Create` | MerchantQRController.Create | see contract | confirmed |
| BE-API-CONFIG-008 | `POST /api/MerchantQR/Update` | `MerchantQRController.Update` | MerchantQRController.Update | see contract | confirmed |
| BE-API-CONFIG-009 | `POST /api/MerchantQR/GetAll` | `MerchantQRController.GetAll` | MerchantQRController.GetAll | see contract | partial |
| BE-API-CONFIG-010 | `POST /api/MerchantQR/Delete` | `MerchantQRController.Delete` | MerchantQRController.Delete | see contract | partial |
| BE-API-CONFIG-011 | `GET /api/Registration/get` | `RegistrationController.GetAll` | RegistrationController.GetAll | see contract | partial |
| BE-API-CONFIG-012 | `POST /api/Banner/getall` | `BannerController.GetAll` | BannerController.GetAll | see contract | partial |
| BE-API-CONFIG-013 | `POST /api/Banner/GetFlowId` | `BannerController.GetFlowId` | BannerController.GetFlowId | see contract | partial |
| BE-API-CONFIG-014 | `POST /api/Banner/getbyid` | `BannerController.GetById` | BannerController.GetById | see contract | partial |
| BE-API-CONFIG-015 | `POST /api/Banner/delete` | `BannerController.delete` | BannerController.delete | see contract | partial |
| BE-API-CONFIG-016 | `POST /api/InviteIcon/getall` | `InviteIconController.GetAll` | InviteIconController.GetAll | see contract | partial |
| BE-API-CONFIG-017 | `POST /api/InviteIcon/getbyid` | `InviteIconController.GetById` | InviteIconController.GetById | see contract | partial |
| BE-API-CONFIG-018 | `POST /api/InviteIcon/getbygroupid` | `InviteIconController.GetByGroupId` | InviteIconController.GetByGroupId | see contract | partial |
| BE-API-CONFIG-019 | `POST /api/InviteIcon/create` | `InviteIconController.Create` | InviteIconController.Create | see contract | confirmed |
| BE-API-CONFIG-020 | `POST /api/InviteIcon/update` | `InviteIconController.Update` | InviteIconController.Update | see contract | confirmed |
| BE-API-CONFIG-021 | `POST /api/InviteIcon/delete` | `InviteIconController.Delete` | InviteIconController.Delete | see contract | partial |
| BE-API-CONFIG-022 | `POST /api/MchangoInterest/create` | `MchangoInterestController.Create` | MchangoInterestController.Create | see contract | confirmed |
| BE-API-CONFIG-023 | `POST /api/MchangoInterest/update` | `MchangoInterestController.Update` | MchangoInterestController.Update | see contract | confirmed |
| BE-API-CONFIG-024 | `POST /api/MchangoInterest/getall` | `MchangoInterestController.GetAll` | MchangoInterestController.GetAll | see contract | partial |
| BE-API-CONFIG-025 | `POST /api/MchangoInterest/delete` | `MchangoInterestController.delete` | MchangoInterestController.delete | see contract | partial |
| BE-API-CONFIG-026 | `POST /api/MixxTip/merchant/create` | `MixxTipController.CreateMerchant` | MixxTipController.CreateMerchant | see contract | confirmed |
| BE-API-CONFIG-027 | `POST /api/MixxTip/merchant/update` | `MixxTipController.UpdateMerchant` | MixxTipController.UpdateMerchant | see contract | confirmed |
| BE-API-CONFIG-028 | `POST /api/MixxTip/merchant/getall` | `MixxTipController.GetAllMerchants` | MixxTipController.GetAllMerchants | see contract | confirmed |
| BE-API-CONFIG-029 | `POST /api/MixxTip/merchant/getbyid` | `MixxTipController.GetMerchantById` | MixxTipController.GetMerchantById | see contract | partial |
| BE-API-CONFIG-030 | `POST /api/MixxTip/merchant/delete` | `MixxTipController.SoftDeleteMerchant` | MixxTipController.SoftDeleteMerchant | see contract | partial |
| BE-API-CONFIG-031 | `POST /api/MixxTip/merchant/isdelete` | `MixxTipController.HardDeleteMerchant` | MixxTipController.HardDeleteMerchant | see contract | partial |
| BE-API-CONFIG-032 | `POST /api/MixxTip/config/get` | `MixxTipController.GetConfig` | MixxTipController.GetConfig | see contract | partial |
| BE-API-CONFIG-033 | `POST /api/MixxTip/config/update` | `MixxTipController.UpdateConfig` | MixxTipController.UpdateConfig | see contract | confirmed |
| BE-API-CONFIG-034 | `POST /api/MixxTip/banner/upload` | `MixxTipController.UploadBanner` | MixxTipController.UploadBanner | see contract | confirmed |
| BE-API-CONFIG-035 | `POST /api/MixxTip/banner/get` | `MixxTipController.GetBanner` | MixxTipController.GetBanner | see contract | partial |
| BE-API-CONFIG-036 | `POST /api/MixxTip/banner/delete` | `MixxTipController.DeleteBanner` | MixxTipController.DeleteBanner | see contract | partial |
| BE-API-CONFIG-037 | `POST /api/MixxTip/importfile` | `MixxTipController.ImportFile` | MixxTipController.ImportFile | see contract | confirmed |
| BE-API-CONFIG-038 | `GET /api/MixxTip/template/download` | `MixxTipController.DownloadTemplate` | MixxTipController.DownloadTemplate | see contract | partial |
| BE-API-CONFIG-039 | `POST /api/MchangoQR/create` | `MchangoQRController.Create` | MchangoQRController.Create | see contract | confirmed |
| BE-API-CONFIG-040 | `POST /api/MchangoQR/update` | `MchangoQRController.Update` | MchangoQRController.Update | see contract | confirmed |
| BE-API-CONFIG-041 | `POST /api/MchangoQR/getall` | `MchangoQRController.GetAll` | MchangoQRController.GetAll | see contract | partial |
| BE-API-CONFIG-042 | `POST /api/MchangoQR/delete` | `MchangoQRController.delete` | MchangoQRController.delete | see contract | partial |
| BE-API-CONFIG-043 | `GET /api/InternationalUserRequest/GetAll` | `InternationalUserRequestController.GetAll` | InternationalUserRequestController.GetAll | see contract | partial |
| BE-API-CONFIG-044 | `GET /api/InternationalUserRequest/GetById/{id}` | `InternationalUserRequestController.GetById` | InternationalUserRequestController.GetById | see contract | partial |
| BE-API-CONFIG-045 | `POST /api/InternationalUserRequest/UpdateUserFields` | `InternationalUserRequestController.UpdateUserFields` | InternationalUserRequestController.UpdateUserFields | see contract | confirmed |
| BE-API-CONFIG-046 | `POST /api/InternationalUserRequest/ApproveOrRejectRequest` | `InternationalUserRequestController.ApproveOrRejectRequest` | InternationalUserRequestController.ApproveOrRejectRequest | see contract | confirmed |
| BE-API-CONFIG-047 | `POST /api/InternationalUserRequest/Delete` | `InternationalUserRequestController.Delete` | InternationalUserRequestController.Delete | see contract | partial |
| BE-API-CONFIG-048 | `POST /api/TerrifTransactionFee/create` | `TerrifTransactionFeeController.CreateTerrifTransactionFee` | TerrifTransactionFeeController.CreateTerrifTransactionFee | see contract | confirmed |
| BE-API-CONFIG-049 | `POST /api/TerrifTransactionFee/delete` | `TerrifTransactionFeeController.DeleteSoft` | TerrifTransactionFeeController.DeleteSoft | see contract | partial |
| BE-API-CONFIG-050 | `POST /api/TerrifTransactionFee/getall` | `TerrifTransactionFeeController.GetAll` | TerrifTransactionFeeController.GetAll | see contract | partial |
| BE-API-CONFIG-051 | `POST /api/TerrifTransactionFee/update` | `TerrifTransactionFeeController.Update` | TerrifTransactionFeeController.Update | see contract | confirmed |
| BE-API-CONFIG-052 | `POST /api/DashboardConfig/getall` | `DashboardConfigController.GetAll` | DashboardConfigController.GetAll | see contract | partial |
| BE-API-CONFIG-053 | `POST /api/DashboardConfig/getbyid` | `DashboardConfigController.GetById` | DashboardConfigController.GetById | see contract | partial |
| BE-API-CONFIG-054 | `POST /api/DashboardConfig/create` | `DashboardConfigController.Create` | DashboardConfigController.Create | see contract | confirmed |
| BE-API-CONFIG-055 | `POST /api/DashboardConfig/update` | `DashboardConfigController.Update` | DashboardConfigController.Update | see contract | confirmed |
| BE-API-CONFIG-056 | `POST /api/DashboardConfig/delete` | `DashboardConfigController.Delete` | DashboardConfigController.Delete | see contract | partial |
| BE-API-CONFIG-057 | `POST /api/DashboardConfig/publish` | `DashboardConfigController.Publish` | DashboardConfigController.Publish | see contract | partial |
| BE-API-CONFIG-058 | `POST /api/DashboardConfig/getpublished` | `DashboardConfigController.GetPublished` | DashboardConfigController.GetPublished | see contract | partial |
| BE-API-CONFIG-059 | `POST /api/PersonalizedForYouItem/getall` | `PersonalizedForYouItemController.GetAll` | PersonalizedForYouItemController.GetAll | see contract | partial |
| BE-API-CONFIG-060 | `POST /api/PersonalizedForYouItem/getbyid` | `PersonalizedForYouItemController.GetById` | PersonalizedForYouItemController.GetById | see contract | partial |
| BE-API-CONFIG-061 | `POST /api/PersonalizedForYouItem/create` | `PersonalizedForYouItemController.Create` | PersonalizedForYouItemController.Create | see contract | confirmed |
| BE-API-CONFIG-062 | `POST /api/PersonalizedForYouItem/update` | `PersonalizedForYouItemController.Update` | PersonalizedForYouItemController.Update | see contract | confirmed |
| BE-API-CONFIG-063 | `POST /api/PersonalizedForYouItem/delete` | `PersonalizedForYouItemController.Delete` | PersonalizedForYouItemController.Delete | see contract | partial |
| BE-API-CONFIG-064 | `POST /api/TerrifSubscriber/create` | `TerrifSubscriberController.CreateTerrifSubscriber` | TerrifSubscriberController.CreateTerrifSubscriber | see contract | confirmed |
| BE-API-CONFIG-065 | `POST /api/TerrifSubscriber/delete` | `TerrifSubscriberController.DeleteSoft` | TerrifSubscriberController.DeleteSoft | see contract | partial |
| BE-API-CONFIG-066 | `POST /api/TerrifSubscriber/getall` | `TerrifSubscriberController.GetAll` | TerrifSubscriberController.GetAll | see contract | partial |
| BE-API-CONFIG-067 | `POST /api/TerrifSubscriber/update` | `TerrifSubscriberController.Update` | TerrifSubscriberController.Update | see contract | confirmed |
| BE-API-CONFIG-068 | `POST /api/ContentPlacement/getall` | `ContentPlacementController.GetAll` | ContentPlacementController.GetAll | see contract | partial |
| BE-API-CONFIG-069 | `POST /api/ContentPlacement/getbyid` | `ContentPlacementController.GetById` | ContentPlacementController.GetById | see contract | confirmed |
| BE-API-CONFIG-070 | `POST /api/ContentPlacement/create` | `ContentPlacementController.Create` | ContentPlacementController.Create | see contract | confirmed |
| BE-API-CONFIG-071 | `POST /api/ContentPlacement/update` | `ContentPlacementController.Update` | ContentPlacementController.Update | see contract | confirmed |
| BE-API-CONFIG-072 | `POST /api/ContentPlacement/delete` | `ContentPlacementController.Delete` | ContentPlacementController.Delete | see contract | confirmed |
| BE-API-CONFIG-073 | `POST /api/ContentPlacement/dropdown/sections` | `ContentPlacementController.DropdownSections` | ContentPlacementController.DropdownSections | see contract | partial |
| BE-API-CONFIG-074 | `POST /api/ContentPlacement/dropdown/sectionitems` | `ContentPlacementController.DropdownSectionItems` | ContentPlacementController.DropdownSectionItems | see contract | partial |
| BE-API-CONFIG-075 | `POST /api/ContentPlacement/dropdown/subsectionitems` | `ContentPlacementController.DropdownSubsectionItems` | ContentPlacementController.DropdownSubsectionItems | see contract | partial |
| BE-API-CONFIG-076 | `POST /api/ContentPlacement/dropdown/placements` | `ContentPlacementController.DropdownPlacements` | ContentPlacementController.DropdownPlacements | see contract | partial |
| BE-API-CONFIG-077 | `POST /api/Games/buttons/getall` | `GamesController.GetAllButtons` | GamesController.GetAllButtons | see contract | partial |
| BE-API-CONFIG-078 | `POST /api/Games/buttons/create` | `GamesController.CreateButtonAsync` | GamesController.CreateButtonAsync | see contract | confirmed |
| BE-API-CONFIG-079 | `POST /api/Games/buttons/update` | `GamesController.UpdateButtonAsync` | GamesController.UpdateButtonAsync | see contract | confirmed |
| BE-API-CONFIG-080 | `POST /api/Games/buttons/delete` | `GamesController.DeleteButtonAsync` | GamesController.DeleteButtonAsync | see contract | partial |
| BE-API-CONFIG-081 | `POST /api/Games/screens/getall` | `GamesController.GetAllScreens` | GamesController.GetAllScreens | see contract | partial |
| BE-API-CONFIG-082 | `POST /api/Games/screens/create` | `GamesController.CreateScreenAsync` | GamesController.CreateScreenAsync | see contract | confirmed |
| BE-API-CONFIG-083 | `POST /api/Games/screens/update` | `GamesController.UpdateScreenAsync` | GamesController.UpdateScreenAsync | see contract | confirmed |
| BE-API-CONFIG-084 | `POST /api/Games/screens/delete` | `GamesController.DeleteScreenAsync` | GamesController.DeleteScreenAsync | see contract | partial |
| BE-API-CONFIG-085 | `POST /api/RemittanceLimits/getall` | `RemittanceLimitsController.GetAll` | RemittanceLimitsController.GetAll | see contract | partial |
| BE-API-CONFIG-086 | `POST /api/RemittanceLimits/update` | `RemittanceLimitsController.Update` | RemittanceLimitsController.Update | see contract | confirmed |
| BE-API-CONFIG-087 | `POST /api/Acquirer/create` | `AcquirerController.Create` | AcquirerController.Create | see contract | confirmed |
| BE-API-CONFIG-088 | `POST /api/Acquirer/update` | `AcquirerController.Update` | AcquirerController.Update | see contract | confirmed |
| BE-API-CONFIG-089 | `POST /api/Acquirer/getbyid` | `AcquirerController.GetById` | AcquirerController.GetById | see contract | partial |
| BE-API-CONFIG-090 | `GET /api/Acquirer/getall` | `AcquirerController.GetAll` | AcquirerController.GetAll | see contract | partial |
| BE-API-CONFIG-091 | `POST /api/Acquirer/delete` | `AcquirerController.Delete` | AcquirerController.Delete | see contract | confirmed |
| BE-API-CONFIG-092 | `POST /api/TransactionHistory/create` | `TransactionHistoryController.Create` | TransactionHistoryController.Create | see contract | confirmed |
| BE-API-CONFIG-093 | `POST /api/TransactionHistory/update` | `TransactionHistoryController.Update` | TransactionHistoryController.Update | see contract | confirmed |
| BE-API-CONFIG-094 | `POST /api/TransactionHistory/getbyid` | `TransactionHistoryController.GetById` | TransactionHistoryController.GetById | see contract | partial |
| BE-API-CONFIG-095 | `GET /api/TransactionHistory/getall` | `TransactionHistoryController.GetAll` | TransactionHistoryController.GetAll | see contract | partial |
| BE-API-CONFIG-096 | `POST /api/TransactionHistory/delete` | `TransactionHistoryController.Delete` | TransactionHistoryController.Delete | see contract | confirmed |
| BE-API-CONFIG-097 | `GET /api/Cards/GetAllAppCards` | `CardsController.GetAllAppCards` | CardsController.GetAllAppCards | see contract | partial |
| BE-API-CONFIG-098 | `GET /api/Cards/{id}` | `CardsController.GetAppCardByIdAsync` | CardsController.GetAppCardByIdAsync | see contract | partial |
| BE-API-CONFIG-099 | `POST /api/Cards/CreateAppCardAsync` | `CardsController.CreateAppCardAsync` | CardsController.CreateAppCardAsync | see contract | confirmed |
| BE-API-CONFIG-100 | `POST /api/Cards/delete` | `CardsController.DeleteAppCardAsync` | CardsController.DeleteAppCardAsync | see contract | partial |
| BE-API-CONFIG-101 | `GET /api/AirtimeOperator/GetAll` | `AirtimeOperatorController.GetAll` | AirtimeOperatorController.GetAll | see contract | partial |
| BE-API-CONFIG-102 | `POST /api/AirtimeOperator/Create` | `AirtimeOperatorController.Create` | AirtimeOperatorController.Create | see contract | confirmed |
| BE-API-CONFIG-103 | `POST /api/AirtimeOperator/Update` | `AirtimeOperatorController.Update` | AirtimeOperatorController.Update | see contract | confirmed |
| BE-API-CONFIG-104 | `POST /api/AirtimeOperator/Delete` | `AirtimeOperatorController.Delete` | AirtimeOperatorController.Delete | see contract | partial |
| BE-API-CONFIG-105 | `GET /api/AirtimeOperator/GetOperatorByMsisdn` | `AirtimeOperatorController.GetOperatorByMsisdn` | AirtimeOperatorController.GetOperatorByMsisdn | see contract | partial |
| BE-API-CONFIG-106 | `POST /api/MenuItems/getall` | `MenuItemsController.GetAll` | MenuItemsController.GetAll | see contract | partial |
| BE-API-CONFIG-107 | `POST /api/MenuItems/getbyid` | `MenuItemsController.GetById` | MenuItemsController.GetById | see contract | partial |
| BE-API-CONFIG-108 | `POST /api/MenuItems/getchildren` | `MenuItemsController.GetChildren` | MenuItemsController.GetChildren | see contract | partial |
| BE-API-CONFIG-109 | `POST /api/MenuItems/create` | `MenuItemsController.Create` | MenuItemsController.Create | see contract | confirmed |
| BE-API-CONFIG-110 | `POST /api/MenuItems/update` | `MenuItemsController.Update` | MenuItemsController.Update | see contract | confirmed |
| BE-API-CONFIG-111 | `POST /api/MenuItems/delete` | `MenuItemsController.Delete` | MenuItemsController.Delete | see contract | partial |
| BE-API-CONFIG-112 | `POST /api/SubSectionItem/importfile` | `SubSectionItemController.ImportFile` | SubSectionItemController.ImportFile | see contract | confirmed |
| BE-API-CONFIG-113 | `POST /api/SubSectionItem/getall` | `SubSectionItemController.GetAllSubSectionItems` | SubSectionItemController.GetAllSubSectionItems | see contract | partial |
| BE-API-CONFIG-114 | `POST /api/SubSectionItem/update` | `SubSectionItemController.SaveSubSectionItemAsync` | SubSectionItemController.SaveSubSectionItemAsync | see contract | confirmed |
| BE-API-CONFIG-115 | `POST /api/SubSectionItem/create` | `SubSectionItemController.CreateSubSectionItemAsync` | SubSectionItemController.CreateSubSectionItemAsync | see contract | confirmed |
| BE-API-CONFIG-116 | `POST /api/SubSectionItem/delete` | `SubSectionItemController.DeleteSubSectionItemAsync` | SubSectionItemController.DeleteSubSectionItemAsync | see contract | partial |
| BE-API-CONFIG-117 | `POST /api/CustomerMsisdn/create` | `CustomerMsisdnController.Create` | CustomerMsisdnController.Create | see contract | confirmed |
| BE-API-CONFIG-118 | `POST /api/CustomerMsisdn/update` | `CustomerMsisdnController.Update` | CustomerMsisdnController.Update | see contract | confirmed |
| BE-API-CONFIG-119 | `POST /api/CustomerMsisdn/delete` | `CustomerMsisdnController.DeleteSoft` | CustomerMsisdnController.DeleteSoft | see contract | partial |
| BE-API-CONFIG-120 | `POST /api/CustomerMsisdn/getall` | `CustomerMsisdnController.GetAll` | CustomerMsisdnController.GetAll | see contract | partial |
| BE-API-CONFIG-121 | `POST /api/CustomerMsisdn/getbyid` | `CustomerMsisdnController.GetById` | CustomerMsisdnController.GetById | see contract | partial |
| BE-API-CONFIG-122 | `POST /api/TerrifTransferType/create` | `TerrifTransferTypeController.CreateTerrifTransferType` | TerrifTransferTypeController.CreateTerrifTransferType | see contract | confirmed |
| BE-API-CONFIG-123 | `POST /api/TerrifTransferType/delete` | `TerrifTransferTypeController.DeleteSoft` | TerrifTransferTypeController.DeleteSoft | see contract | partial |
| BE-API-CONFIG-124 | `POST /api/TerrifTransferType/getall` | `TerrifTransferTypeController.GetAll` | TerrifTransferTypeController.GetAll | see contract | partial |
| BE-API-CONFIG-125 | `POST /api/TerrifTransferType/update` | `TerrifTransferTypeController.Update` | TerrifTransferTypeController.Update | see contract | confirmed |
| BE-API-CONFIG-126 | `POST /api/Section/getall` | `SectionController.GetAll` | SectionController.GetAll | see contract | partial |
| BE-API-CONFIG-127 | `POST /api/Section/update` | `SectionController.SaveAsync` | SectionController.SaveAsync | see contract | confirmed |
| BE-API-CONFIG-128 | `POST /api/Section/create` | `SectionController.CreateAsync` | SectionController.CreateAsync | see contract | confirmed |
| BE-API-CONFIG-129 | `POST /api/Section/delete` | `SectionController.DeleteAsync` | SectionController.DeleteAsync | see contract | partial |
| BE-API-CONFIG-130 | `POST /api/MixxPointsCategories/create` | `MixxPointsCategoriesController.Create` | MixxPointsCategoriesController.Create | see contract | confirmed |
| BE-API-CONFIG-131 | `POST /api/MixxPointsCategories/update` | `MixxPointsCategoriesController.Update` | MixxPointsCategoriesController.Update | see contract | confirmed |
| BE-API-CONFIG-132 | `POST /api/MixxPointsCategories/getbyid` | `MixxPointsCategoriesController.GetById` | MixxPointsCategoriesController.GetById | see contract | partial |
| BE-API-CONFIG-133 | `GET /api/MixxPointsCategories/getall` | `MixxPointsCategoriesController.GetAll` | MixxPointsCategoriesController.GetAll | see contract | partial |
| BE-API-CONFIG-134 | `POST /api/MixxPointsCategories/delete` | `MixxPointsCategoriesController.Delete` | MixxPointsCategoriesController.Delete | see contract | confirmed |
| BE-API-CONFIG-135 | `POST /api/WhiteList/create` | `WhiteListController.Create` | WhiteListController.Create | see contract | confirmed |
| BE-API-CONFIG-136 | `POST /api/WhiteList/update` | `WhiteListController.Update` | WhiteListController.Update | see contract | confirmed |
| BE-API-CONFIG-137 | `POST /api/WhiteList/delete` | `WhiteListController.Delete` | WhiteListController.Delete | see contract | partial |
| BE-API-CONFIG-138 | `POST /api/WhiteList/GetById` | `WhiteListController.GetById` | WhiteListController.GetById | see contract | partial |
| BE-API-CONFIG-139 | `POST /api/WhiteList/getall` | `WhiteListController.GetAll` | WhiteListController.GetAll | see contract | partial |
| BE-API-CONFIG-140 | `POST /api/Leaderboard/campaignstatus/get` | `LeaderboardController.GetCampaignStatus` | LeaderboardController.GetCampaignStatus | see contract | partial |
| BE-API-CONFIG-141 | `POST /api/Leaderboard/campaignstatus/save` | `LeaderboardController.SaveCampaignStatus` | LeaderboardController.SaveCampaignStatus | see contract | confirmed |
| BE-API-CONFIG-142 | `POST /api/Leaderboard/settings/get` | `LeaderboardController.GetSettings` | LeaderboardController.GetSettings | see contract | partial |
| BE-API-CONFIG-143 | `POST /api/Leaderboard/settings/save` | `LeaderboardController.SaveSettings` | LeaderboardController.SaveSettings | see contract | confirmed |
| BE-API-CONFIG-144 | `POST /api/Leaderboard/carousel/getall` | `LeaderboardController.GetCarousel` | LeaderboardController.GetCarousel | see contract | partial |
| BE-API-CONFIG-145 | `POST /api/Leaderboard/carousel/save` | `LeaderboardController.SaveCarousel` | LeaderboardController.SaveCarousel | see contract | confirmed |
| BE-API-CONFIG-146 | `POST /api/Leaderboard/carousel/delete` | `LeaderboardController.DeleteCarousel` | LeaderboardController.DeleteCarousel | see contract | partial |
| BE-API-CONFIG-147 | `POST /api/Leaderboard/howtowin/get` | `LeaderboardController.GetHowToWin` | LeaderboardController.GetHowToWin | see contract | partial |
| BE-API-CONFIG-148 | `POST /api/Leaderboard/howtowin/save` | `LeaderboardController.SaveHowToWin` | LeaderboardController.SaveHowToWin | see contract | confirmed |
| BE-API-CONFIG-149 | `POST /api/Leaderboard/winners/getall` | `LeaderboardController.GetWinners` | LeaderboardController.GetWinners | see contract | confirmed |
| BE-API-CONFIG-150 | `POST /api/Leaderboard/winners/importfile` | `LeaderboardController.ImportWinners` | LeaderboardController.ImportWinners | see contract | confirmed |
| BE-API-CONFIG-151 | `POST /api/Leaderboard/winners/create` | `LeaderboardController.CreateWinner` | LeaderboardController.CreateWinner | see contract | confirmed |
| BE-API-CONFIG-152 | `POST /api/Leaderboard/winners/update` | `LeaderboardController.UpdateWinner` | LeaderboardController.UpdateWinner | see contract | confirmed |
| BE-API-CONFIG-153 | `POST /api/Leaderboard/winners/delete` | `LeaderboardController.DeleteWinner` | LeaderboardController.DeleteWinner | see contract | partial |
| BE-API-CONFIG-154 | `POST /api/Leaderboard/importfile` | `LeaderboardController.ImportFileLegacy` | LeaderboardController.ImportFileLegacy | see contract | confirmed |
| BE-API-CONFIG-155 | `POST /api/Leaderboard/getall` | `LeaderboardController.GetAllLegacy` | LeaderboardController.GetAllLegacy | see contract | partial |
| BE-API-CONFIG-156 | `POST /api/Leaderboard/create` | `LeaderboardController.CreateLegacy` | LeaderboardController.CreateLegacy | see contract | confirmed |
| BE-API-CONFIG-157 | `POST /api/Leaderboard/update` | `LeaderboardController.UpdateLegacy` | LeaderboardController.UpdateLegacy | see contract | confirmed |
| BE-API-CONFIG-158 | `POST /api/Leaderboard/delete` | `LeaderboardController.DeleteLegacy` | LeaderboardController.DeleteLegacy | see contract | partial |
| BE-API-CONFIG-159 | `POST /api/FileValidationRule/create` | `FileValidationRuleController.Create` | FileValidationRuleController.Create | see contract | confirmed |
| BE-API-CONFIG-160 | `POST /api/FileValidationRule/getall` | `FileValidationRuleController.GetAll` | FileValidationRuleController.GetAll | see contract | partial |
| BE-API-CONFIG-161 | `POST /api/FileValidationRule/getbyid` | `FileValidationRuleController.GetById` | FileValidationRuleController.GetById | see contract | partial |
| BE-API-CONFIG-162 | `POST /api/FileValidationRule/getbycategory` | `FileValidationRuleController.GetByCategory` | FileValidationRuleController.GetByCategory | see contract | partial |
| BE-API-CONFIG-163 | `POST /api/FileValidationRule/update` | `FileValidationRuleController.Update` | FileValidationRuleController.Update | see contract | confirmed |
| BE-API-CONFIG-164 | `POST /api/FileValidationRule/delete` | `FileValidationRuleController.Delete` | FileValidationRuleController.Delete | see contract | partial |
| BE-API-CONFIG-165 | `POST /api/MchangoAccount/create` | `MchangoAccountController.Create` | MchangoAccountController.Create | see contract | confirmed |
| BE-API-CONFIG-166 | `POST /api/MchangoAccount/update` | `MchangoAccountController.Update` | MchangoAccountController.Update | see contract | confirmed |
| BE-API-CONFIG-167 | `POST /api/MchangoAccount/getall` | `MchangoAccountController.GetAll` | MchangoAccountController.GetAll | see contract | partial |
| BE-API-CONFIG-168 | `POST /api/MchangoAccount/delete` | `MchangoAccountController.delete` | MchangoAccountController.delete | see contract | partial |
| BE-API-CONFIG-169 | `POST /api/StandingOrderMapping/create` | `StandingOrderMappingController.Create` | StandingOrderMappingController.Create | see contract | confirmed |
| BE-API-CONFIG-170 | `POST /api/StandingOrderMapping/update` | `StandingOrderMappingController.Update` | StandingOrderMappingController.Update | see contract | confirmed |
| BE-API-CONFIG-171 | `POST /api/StandingOrderMapping/getbyid` | `StandingOrderMappingController.GetById` | StandingOrderMappingController.GetById | see contract | partial |
| BE-API-CONFIG-172 | `GET /api/StandingOrderMapping/getall` | `StandingOrderMappingController.GetAll` | StandingOrderMappingController.GetAll | see contract | partial |
| BE-API-CONFIG-173 | `POST /api/StandingOrderMapping/delete` | `StandingOrderMappingController.Delete` | StandingOrderMappingController.Delete | see contract | confirmed |
| BE-API-CONFIG-174 | `POST /api/MerchantReqToPay/Create` | `MerchantReqToPayController.Create` | MerchantReqToPayController.Create | see contract | confirmed |
| BE-API-CONFIG-175 | `POST /api/MerchantReqToPay/Update` | `MerchantReqToPayController.Update` | MerchantReqToPayController.Update | see contract | confirmed |
| BE-API-CONFIG-176 | `POST /api/MerchantReqToPay/GetConfigurations` | `MerchantReqToPayController.GetConfigurations` | MerchantReqToPayController.GetConfigurations | see contract | partial |
| BE-API-CONFIG-177 | `POST /api/MerchantReqToPay/Delete` | `MerchantReqToPayController.Delete` | MerchantReqToPayController.Delete | see contract | partial |
| BE-API-CONFIG-178 | `POST /api/Config/create` | `ConfigController.Create` | ConfigController.Create | see contract | confirmed |
| BE-API-CONFIG-179 | `POST /api/Config/getall` | `ConfigController.Get` | ConfigController.Get | see contract | partial |
| BE-API-CONFIG-180 | `POST /api/Config/getbyid` | `ConfigController.GetById` | ConfigController.GetById | see contract | partial |
| BE-API-CONFIG-181 | `POST /api/Config/update` | `ConfigController.Update` | ConfigController.Update | see contract | confirmed |
| BE-API-CONFIG-182 | `POST /api/TerrifAmountType/create` | `TerrifAmountTypeController.CreateTerrifAmountType` | TerrifAmountTypeController.CreateTerrifAmountType | see contract | confirmed |
| BE-API-CONFIG-183 | `POST /api/TerrifAmountType/delete` | `TerrifAmountTypeController.DeleteSoft` | TerrifAmountTypeController.DeleteSoft | see contract | partial |
| BE-API-CONFIG-184 | `POST /api/TerrifAmountType/getall` | `TerrifAmountTypeController.GetAll` | TerrifAmountTypeController.GetAll | see contract | partial |
| BE-API-CONFIG-185 | `POST /api/TerrifAmountType/update` | `TerrifAmountTypeController.Update` | TerrifAmountTypeController.Update | see contract | confirmed |
| BE-API-CONFIG-186 | `POST /api/Themes/createthemecategory` | `ThemesController.CreateThemeCategory` | ThemesController.CreateThemeCategory | see contract | confirmed |
| BE-API-CONFIG-187 | `POST /api/Themes/deletethemecategory` | `ThemesController.DeleteSoftThemeCategory` | ThemesController.DeleteSoftThemeCategory | see contract | partial |
| BE-API-CONFIG-188 | `POST /api/Themes/getallthemecategories` | `ThemesController.GetAlThemeCategoriesl` | ThemesController.GetAlThemeCategoriesl | see contract | partial |
| BE-API-CONFIG-189 | `POST /api/Themes/updatethemecategory` | `ThemesController.UpdateThemeCategory` | ThemesController.UpdateThemeCategory | see contract | confirmed |
| BE-API-CONFIG-190 | `POST /api/Themes/createtheme` | `ThemesController.CreateTheme` | ThemesController.CreateTheme | see contract | confirmed |
| BE-API-CONFIG-191 | `POST /api/Themes/deletetheme` | `ThemesController.DeleteSoftTheme` | ThemesController.DeleteSoftTheme | see contract | partial |
| BE-API-CONFIG-192 | `POST /api/Themes/getallthemes` | `ThemesController.GetAllThemes` | ThemesController.GetAllThemes | see contract | partial |
| BE-API-CONFIG-193 | `POST /api/Themes/updatetheme` | `ThemesController.UpdateTheme` | ThemesController.UpdateTheme | see contract | confirmed |
| BE-API-CONFIG-194 | `POST /api/Language/getall` | `LanguageController.GetAll` | LanguageController.GetAll | see contract | partial |
| BE-API-CONFIG-195 | `POST /api/Stocks/GetStocks` | `StocksController.GetStocks` | StocksController.GetStocks | see contract | partial |
| BE-API-CONFIG-196 | `POST /api/Stocks/SyncStocks` | `StocksController.SyncStocks` | StocksController.SyncStocks | see contract | partial |
| BE-API-CONFIG-197 | `POST /api/Stocks/UpdateStocks` | `StocksController.UpdateStocks` | StocksController.UpdateStocks | see contract | confirmed |
| BE-API-CONFIG-198 | `POST /api/HomeCards/getall` | `HomeCardsController.GetAll` | HomeCardsController.GetAll | see contract | partial |
| BE-API-CONFIG-199 | `POST /api/HomeCards/getbyid` | `HomeCardsController.GetById` | HomeCardsController.GetById | see contract | partial |
| BE-API-CONFIG-200 | `POST /api/HomeCards/create` | `HomeCardsController.Create` | HomeCardsController.Create | see contract | confirmed |
| BE-API-CONFIG-201 | `POST /api/HomeCards/update` | `HomeCardsController.Update` | HomeCardsController.Update | see contract | confirmed |
| BE-API-CONFIG-202 | `POST /api/HomeCards/delete` | `HomeCardsController.Delete` | HomeCardsController.Delete | see contract | partial |
| BE-API-CONFIG-203 | `POST /api/AppChannelOs/getall` | `AppChannelOsController.GetAll` | AppChannelOsController.GetAll | see contract | partial |
| BE-API-CONFIG-204 | `POST /api/Bundles/importbundles` | `BundlesController.ImportBundles` | BundlesController.ImportBundles | see contract | confirmed |
| BE-API-CONFIG-205 | `POST /api/Bundles/create` | `BundlesController.Create` | BundlesController.Create | see contract | confirmed |
| BE-API-CONFIG-206 | `POST /api/Bundles/delete` | `BundlesController.DeleteSoft` | BundlesController.DeleteSoft | see contract | partial |
| BE-API-CONFIG-207 | `POST /api/Bundles/bulkDelete` | `BundlesController.DeleteBulkSoft` | BundlesController.DeleteBulkSoft | see contract | partial |
| BE-API-CONFIG-208 | `POST /api/Bundles/getall` | `BundlesController.GetAll` | BundlesController.GetAll | see contract | partial |
| BE-API-CONFIG-209 | `POST /api/Bundles/update` | `BundlesController.Update` | BundlesController.Update | see contract | confirmed |
| BE-API-CONFIG-210 | `POST /api/RegisteredDevices/getall` | `RegisteredDevicesController.GetAll` | RegisteredDevicesController.GetAll | see contract | confirmed |
| BE-API-CONFIG-211 | `POST /api/ConsumerQR/create` | `ConsumerQRController.Create` | ConsumerQRController.Create | see contract | confirmed |
| BE-API-CONFIG-212 | `POST /api/ConsumerQR/update` | `ConsumerQRController.Update` | ConsumerQRController.Update | see contract | confirmed |
| BE-API-CONFIG-213 | `POST /api/ConsumerQR/getall` | `ConsumerQRController.GetAll` | ConsumerQRController.GetAll | see contract | partial |
| BE-API-CONFIG-214 | `POST /api/ConsumerQR/delete` | `ConsumerQRController.delete` | ConsumerQRController.delete | see contract | partial |
| BE-API-CONFIG-215 | `POST /api/TerrifUnit/create` | `TerrifUnitController.CreateTerrifUnit` | TerrifUnitController.CreateTerrifUnit | see contract | confirmed |
| BE-API-CONFIG-216 | `POST /api/TerrifUnit/delete` | `TerrifUnitController.DeleteSoft` | TerrifUnitController.DeleteSoft | see contract | partial |
| BE-API-CONFIG-217 | `POST /api/TerrifUnit/getall` | `TerrifUnitController.GetAll` | TerrifUnitController.GetAll | see contract | partial |
| BE-API-CONFIG-218 | `POST /api/TerrifUnit/update` | `TerrifUnitController.Update` | TerrifUnitController.Update | see contract | confirmed |
| BE-API-CONFIG-219 | `POST /api/DashboardLayout/getall` | `DashboardLayoutController.GetAll` | DashboardLayoutController.GetAll | see contract | partial |
| BE-API-CONFIG-220 | `POST /api/DashboardLayout/getbyid` | `DashboardLayoutController.GetById` | DashboardLayoutController.GetById | see contract | partial |
| BE-API-CONFIG-221 | `POST /api/DashboardLayout/create` | `DashboardLayoutController.Create` | DashboardLayoutController.Create | see contract | confirmed |
| BE-API-CONFIG-222 | `POST /api/DashboardLayout/update` | `DashboardLayoutController.Update` | DashboardLayoutController.Update | see contract | confirmed |
| BE-API-CONFIG-223 | `POST /api/DashboardLayout/delete` | `DashboardLayoutController.Delete` | DashboardLayoutController.Delete | see contract | partial |
| BE-API-CONFIG-224 | `POST /api/Channel/getall` | `ChannelController.GetAll` | ChannelController.GetAll | see contract | partial |
| BE-API-CONFIG-225 | `POST /api/Channel/getallbycountryid` | `ChannelController.getallbycountryid` | ChannelController.getallbycountryid | see contract | partial |
| BE-API-CONFIG-226 | `POST /api/RewardManagement/createbonustype` | `RewardManagementController.CreateBonusType` | RewardManagementController.CreateBonusType | see contract | confirmed |
| BE-API-CONFIG-227 | `POST /api/RewardManagement/deletebonustype` | `RewardManagementController.DeleteSoftBonusType` | RewardManagementController.DeleteSoftBonusType | see contract | partial |
| BE-API-CONFIG-228 | `POST /api/RewardManagement/getallbonustype` | `RewardManagementController.GetAllBonusType` | RewardManagementController.GetAllBonusType | see contract | partial |
| BE-API-CONFIG-229 | `POST /api/RewardManagement/updatebonustype` | `RewardManagementController.UpdateBonusType` | RewardManagementController.UpdateBonusType | see contract | confirmed |
| BE-API-CONFIG-230 | `POST /api/RewardManagement/createbonusproducts` | `RewardManagementController.CreateBonusProducts` | RewardManagementController.CreateBonusProducts | see contract | confirmed |
| BE-API-CONFIG-231 | `POST /api/RewardManagement/deletebonusproducts` | `RewardManagementController.DeleteSoftBonusProducts` | RewardManagementController.DeleteSoftBonusProducts | see contract | partial |
| BE-API-CONFIG-232 | `POST /api/RewardManagement/getallbonusproducts` | `RewardManagementController.GetAllBonusProducts` | RewardManagementController.GetAllBonusProducts | see contract | partial |
| BE-API-CONFIG-233 | `POST /api/RewardManagement/updatebonusproducts` | `RewardManagementController.UpdateBonusProducts` | RewardManagementController.UpdateBonusProducts | see contract | confirmed |
| BE-API-CONFIG-234 | `POST /api/RewardManagement/updatereferrallimits` | `RewardManagementController.UpdateReferralLimits` | RewardManagementController.UpdateReferralLimits | see contract | confirmed |
| BE-API-CONFIG-235 | `POST /api/RewardManagement/getallreferrallimits` | `RewardManagementController.GetAllReferralLimits` | RewardManagementController.GetAllReferralLimits | see contract | partial |
| BE-API-CONFIG-236 | `POST /api/RewardManagement/getallreferralcodes` | `RewardManagementController.GetAllReferralCodes` | RewardManagementController.GetAllReferralCodes | see contract | partial |
| BE-API-CONFIG-237 | `POST /api/Podcast/PodcastCreate` | `PodcastController.PodcastCreate` | PodcastController.PodcastCreate | see contract | partial |
| BE-API-CONFIG-238 | `POST /api/Podcast/PodcastUpdate` | `PodcastController.PodcastUpdate` | PodcastController.PodcastUpdate | see contract | partial |
| BE-API-CONFIG-239 | `POST /api/Podcast/PodcastGetAll` | `PodcastController.PodcastGetAll` | PodcastController.PodcastGetAll | see contract | partial |
| BE-API-CONFIG-240 | `POST /api/Podcast/PodcastDelete` | `PodcastController.PodcastDelete` | PodcastController.PodcastDelete | see contract | partial |
| BE-API-CONFIG-241 | `POST /api/SectionItem/getsectionitemsbysectionid` | `SectionItemController.GetSectionItemsBySectionId` | SectionItemController.GetSectionItemsBySectionId | see contract | partial |
| BE-API-CONFIG-242 | `POST /api/SectionItem/getall` | `SectionItemController.GetAllSectionItems` | SectionItemController.GetAllSectionItems | see contract | partial |
| BE-API-CONFIG-243 | `POST /api/SectionItem/update` | `SectionItemController.SaveSectionItemAsync` | SectionItemController.SaveSectionItemAsync | see contract | confirmed |
| BE-API-CONFIG-244 | `POST /api/SectionItem/create` | `SectionItemController.CreateItemAsync` | SectionItemController.CreateItemAsync | see contract | confirmed |
| BE-API-CONFIG-245 | `POST /api/SectionItem/delete` | `SectionItemController.DeleteSectionItemAsync` | SectionItemController.DeleteSectionItemAsync | see contract | partial |
| BE-API-CONFIG-246 | `POST /api/HomeLayout/getall` | `HomeLayoutController.GetAll` | HomeLayoutController.GetAll | see contract | partial |
| BE-API-CONFIG-247 | `POST /api/HomeLayout/getbyid` | `HomeLayoutController.GetById` | HomeLayoutController.GetById | see contract | partial |
| BE-API-CONFIG-248 | `POST /api/HomeLayout/create` | `HomeLayoutController.Create` | HomeLayoutController.Create | see contract | confirmed |
| BE-API-CONFIG-249 | `POST /api/HomeLayout/update` | `HomeLayoutController.Update` | HomeLayoutController.Update | see contract | confirmed |
| BE-API-CONFIG-250 | `POST /api/HomeLayout/delete` | `HomeLayoutController.Delete` | HomeLayoutController.Delete | see contract | partial |
| BE-API-CONFIG-251 | `POST /api/YasService/getall` | `YasServiceController.GetAll` | YasServiceController.GetAll | see contract | partial |
| BE-API-CONFIG-252 | `POST /api/YasService/update` | `YasServiceController.SaveAsync` | YasServiceController.SaveAsync | see contract | confirmed |
| BE-API-CONFIG-253 | `POST /api/YasService/create` | `YasServiceController.CreateAsync` | YasServiceController.CreateAsync | see contract | confirmed |
| BE-API-CONFIG-254 | `POST /api/YasService/delete` | `YasServiceController.DeleteAsync` | YasServiceController.DeleteAsync | see contract | partial |
| BE-API-CONFIG-255 | `POST /api/Outage/getall` | `OutageController.GetAll` | OutageController.GetAll | see contract | partial |
| BE-API-CONFIG-256 | `POST /api/Outage/create` | `OutageController.CreateAsync` | OutageController.CreateAsync | see contract | confirmed |
| BE-API-CONFIG-257 | `POST /api/Outage/update` | `OutageController.UpdateAsync` | OutageController.UpdateAsync | see contract | confirmed |
| BE-API-CONFIG-258 | `POST /api/TvPressOffers/create` | `TvPressOffersController.CreateTvPressOffers` | TvPressOffersController.CreateTvPressOffers | see contract | confirmed |
| BE-API-CONFIG-259 | `POST /api/TvPressOffers/delete` | `TvPressOffersController.DeleteSoft` | TvPressOffersController.DeleteSoft | see contract | partial |
| BE-API-CONFIG-260 | `POST /api/TvPressOffers/getall` | `TvPressOffersController.GetAll` | TvPressOffersController.GetAll | see contract | partial |
| BE-API-CONFIG-261 | `POST /api/TvPressOffers/update` | `TvPressOffersController.Update` | TvPressOffersController.Update | see contract | confirmed |
| BE-API-CONFIG-262 | `POST /api/Merchant/getall` | `MerchantController.GetAll` | MerchantController.GetAll | see contract | partial |
| BE-API-CONFIG-263 | `POST /api/Merchant/create` | `MerchantController.CreateAsync` | MerchantController.CreateAsync | see contract | confirmed |
| BE-API-CONFIG-264 | `POST /api/Merchant/update` | `MerchantController.UpdateAsync` | MerchantController.UpdateAsync | see contract | confirmed |
| BE-API-CONFIG-265 | `POST /api/Merchant/delete` | `MerchantController.DeleteAsync` | MerchantController.DeleteAsync | see contract | partial |
| BE-API-CONFIG-266 | `POST /api/Merchant/importCSV` | `MerchantController.SaveAllAsync` | MerchantController.SaveAllAsync | see contract | confirmed |
| BE-API-CONFIG-267 | `POST /api/ResponseCode/importresponsecodes` | `ResponseCodeController.ImportResponseCodes` | ResponseCodeController.ImportResponseCodes | see contract | confirmed |
| BE-API-CONFIG-268 | `POST /api/ResponseCode/create` | `ResponseCodeController.Create` | ResponseCodeController.Create | see contract | confirmed |
| BE-API-CONFIG-269 | `POST /api/ResponseCode/update` | `ResponseCodeController.Update` | ResponseCodeController.Update | see contract | confirmed |
| BE-API-CONFIG-270 | `GET /api/ResponseCode/get` | `ResponseCodeController.Get` | ResponseCodeController.Get | see contract | partial |
| BE-API-CONFIG-271 | `POST /api/ResponseCode/getbyid` | `ResponseCodeController.GetById` | ResponseCodeController.GetById | see contract | partial |
| BE-API-CONFIG-272 | `GET /api/ResponseCode/getall` | `ResponseCodeController.GetAll` | ResponseCodeController.GetAll | see contract | partial |
| BE-API-CONFIG-273 | `POST /api/ResponseCode/delete` | `ResponseCodeController.Delete` | ResponseCodeController.Delete | see contract | partial |
| BE-API-CONFIG-274 | `POST /api/AppVersions/create-app-version` | `AppVersionsController.CreateAppVersion` | AppVersionsController.CreateAppVersion | see contract | confirmed |
| BE-API-CONFIG-275 | `POST /api/AppVersions/update-app-version` | `AppVersionsController.UpdateAppVersion` | AppVersionsController.UpdateAppVersion | see contract | confirmed |
| BE-API-CONFIG-276 | `DELETE /api/AppVersions/delete-app-version/{versionId}` | `AppVersionsController.UpdateAppVersion` | AppVersionsController.UpdateAppVersion | see contract | partial |
| BE-API-CONFIG-277 | `GET /api/AppVersions/get-app-versions` | `AppVersionsController.GetAppVersions` | AppVersionsController.GetAppVersions | see contract | partial |
| BE-API-CONFIG-278 | `GET /api/AppVersions/get-app-versions-by-id/{versionId}` | `AppVersionsController.GetAppVersions` | AppVersionsController.GetAppVersions | see contract | partial |
| BE-API-CONFIG-279 | `POST /api/AppVersions/getall` | `AppVersionsController.GetAll` | AppVersionsController.GetAll | see contract | partial |
| BE-API-CONFIG-280 | `POST /api/DeviceBlocking/importfile` | `DeviceBlockingController.ImportFile` | DeviceBlockingController.ImportFile | see contract | confirmed |
| BE-API-CONFIG-281 | `POST /api/DeviceBlocking/create` | `DeviceBlockingController.Create` | DeviceBlockingController.Create | see contract | confirmed |
| BE-API-CONFIG-282 | `POST /api/DeviceBlocking/update` | `DeviceBlockingController.Update` | DeviceBlockingController.Update | see contract | confirmed |
| BE-API-CONFIG-283 | `POST /api/DeviceBlocking/getall` | `DeviceBlockingController.GetAll` | DeviceBlockingController.GetAll | see contract | partial |
| BE-API-CONFIG-284 | `POST /api/DeviceBlocking/getbyid` | `DeviceBlockingController.GetById` | DeviceBlockingController.GetById | see contract | partial |
| BE-API-CONFIG-285 | `POST /api/DeviceBlocking/isdelete` | `DeviceBlockingController.DeleteHard` | DeviceBlockingController.DeleteHard | see contract | partial |
| BE-API-CONFIG-286 | `POST /api/DeviceBlocking/delete` | `DeviceBlockingController.DeleteSoft` | DeviceBlockingController.DeleteSoft | see contract | partial |
| BE-API-CONFIG-287 | `POST /api/DeviceBlocking/getAllDevices` | `DeviceBlockingController.getAllDevices` | DeviceBlockingController.getAllDevices | see contract | partial |
| BE-API-CONFIG-288 | `POST /api/DeviceBlocking/updateBlocking` | `DeviceBlockingController.updateBlocking` | DeviceBlockingController.updateBlocking | see contract | confirmed |
| BE-API-CONFIG-289 | `POST /api/Translations/create` | `TranslationsController.CreateTranslation` | TranslationsController.CreateTranslation | see contract | confirmed |
| BE-API-CONFIG-290 | `POST /api/Translations/delete` | `TranslationsController.DeleteSoft` | TranslationsController.DeleteSoft | see contract | partial |
| BE-API-CONFIG-291 | `POST /api/Translations/getall` | `TranslationsController.GetAll` | TranslationsController.GetAll | see contract | partial |
| BE-API-CONFIG-292 | `POST /api/Translations/update` | `TranslationsController.Update` | TranslationsController.Update | see contract | confirmed |
| BE-API-CONFIG-293 | `POST /api/KikobaDashboardItem/getall` | `KikobaDashboardItemController.GetAll` | KikobaDashboardItemController.GetAll | see contract | partial |
| BE-API-CONFIG-294 | `POST /api/KikobaDashboardItem/getbyid` | `KikobaDashboardItemController.GetById` | KikobaDashboardItemController.GetById | see contract | partial |
| BE-API-CONFIG-295 | `POST /api/KikobaDashboardItem/create` | `KikobaDashboardItemController.Create` | KikobaDashboardItemController.Create | see contract | confirmed |
| BE-API-CONFIG-296 | `POST /api/KikobaDashboardItem/update` | `KikobaDashboardItemController.Update` | KikobaDashboardItemController.Update | see contract | confirmed |
| BE-API-CONFIG-297 | `POST /api/KikobaDashboardItem/delete` | `KikobaDashboardItemController.Delete` | KikobaDashboardItemController.Delete | see contract | partial |
| BE-API-CONFIG-298 | `POST /api/KikobaDashboardItem/reorder` | `KikobaDashboardItemController.Reorder` | KikobaDashboardItemController.Reorder | see contract | confirmed |
| BE-API-CONFIG-299 | `POST /api/TerrifSlab/create` | `TerrifSlabController.CreateTerrifSlab` | TerrifSlabController.CreateTerrifSlab | see contract | confirmed |
| BE-API-CONFIG-300 | `POST /api/TerrifSlab/delete` | `TerrifSlabController.DeleteSoft` | TerrifSlabController.DeleteSoft | see contract | partial |
| BE-API-CONFIG-301 | `POST /api/TerrifSlab/getall` | `TerrifSlabController.GetAll` | TerrifSlabController.GetAll | see contract | partial |
| BE-API-CONFIG-302 | `POST /api/TerrifSlab/update` | `TerrifSlabController.Update` | TerrifSlabController.Update | see contract | confirmed |
| BE-API-CONFIG-303 | `POST /api/BankBillers/importbanksbillers` | `BankBillersController.ImportBanksBillers` | BankBillersController.ImportBanksBillers | see contract | confirmed |
| BE-API-CONFIG-304 | `POST /api/BankBillers/create` | `BankBillersController.Create` | BankBillersController.Create | see contract | confirmed |
| BE-API-CONFIG-305 | `POST /api/BankBillers/delete` | `BankBillersController.DeleteSoft` | BankBillersController.DeleteSoft | see contract | partial |
| BE-API-CONFIG-306 | `POST /api/BankBillers/getall` | `BankBillersController.GetAll` | BankBillersController.GetAll | see contract | partial |
| BE-API-CONFIG-307 | `POST /api/BankBillers/update` | `BankBillersController.Update` | BankBillersController.Update | see contract | confirmed |
| BE-API-CONFIG-308 | `POST /api/UserJourney/create` | `UserJourneyController.Create` | UserJourneyController.Create | see contract | confirmed |
| BE-API-CONFIG-309 | `POST /api/UserJourney/delete` | `UserJourneyController.DeleteSoft` | UserJourneyController.DeleteSoft | see contract | partial |
| BE-API-CONFIG-310 | `POST /api/UserJourney/getall` | `UserJourneyController.GetAll` | UserJourneyController.GetAll | see contract | partial |
| BE-API-CONFIG-311 | `POST /api/UserJourney/update` | `UserJourneyController.Update` | UserJourneyController.Update | see contract | confirmed |
| BE-API-CONFIG-312 | `POST /api/ImageSubCategories/create` | `ImageSubCategoriesController.CreateSubCategory` | ImageSubCategoriesController.CreateSubCategory | see contract | confirmed |
| BE-API-CONFIG-313 | `POST /api/ImageSubCategories/delete` | `ImageSubCategoriesController.DeleteSoft` | ImageSubCategoriesController.DeleteSoft | see contract | partial |
| BE-API-CONFIG-314 | `POST /api/ImageSubCategories/getall` | `ImageSubCategoriesController.GetAll` | ImageSubCategoriesController.GetAll | see contract | partial |
| BE-API-CONFIG-315 | `POST /api/ImageSubCategories/update` | `ImageSubCategoriesController.Update` | ImageSubCategoriesController.Update | see contract | confirmed |
| BE-API-CONFIG-316 | `POST /api/SelfOnboardingItem/getall` | `SelfOnboardingItemController.GetAll` | SelfOnboardingItemController.GetAll | see contract | partial |
| BE-API-CONFIG-317 | `POST /api/SelfOnboardingItem/getbyid` | `SelfOnboardingItemController.GetById` | SelfOnboardingItemController.GetById | see contract | partial |
| BE-API-CONFIG-318 | `POST /api/SelfOnboardingItem/create` | `SelfOnboardingItemController.Create` | SelfOnboardingItemController.Create | see contract | confirmed |
| BE-API-CONFIG-319 | `POST /api/SelfOnboardingItem/update` | `SelfOnboardingItemController.Update` | SelfOnboardingItemController.Update | see contract | confirmed |
| BE-API-CONFIG-320 | `POST /api/SelfOnboardingItem/delete` | `SelfOnboardingItemController.Delete` | SelfOnboardingItemController.Delete | see contract | partial |
| BE-API-CONFIG-321 | `POST /api/Faq/create` | `FaqController.Create` | FaqController.Create | see contract | confirmed |
| BE-API-CONFIG-322 | `POST /api/Faq/update` | `FaqController.Update` | FaqController.Update | see contract | confirmed |
| BE-API-CONFIG-323 | `POST /api/Faq/getall` | `FaqController.GetAll` | FaqController.GetAll | see contract | partial |
| BE-API-CONFIG-324 | `POST /api/Faq/getbyid` | `FaqController.GetById` | FaqController.GetById | see contract | partial |
| BE-API-CONFIG-325 | `POST /api/Faq/delete` | `FaqController.delete` | FaqController.delete | see contract | partial |
| BE-API-CONFIG-326 | `POST /api/ImageCategories/create` | `ImageCategoriesController.CreateCategory` | ImageCategoriesController.CreateCategory | see contract | confirmed |
| BE-API-CONFIG-327 | `POST /api/ImageCategories/getall` | `ImageCategoriesController.GetAll` | ImageCategoriesController.GetAll | see contract | partial |
| BE-API-CONFIG-328 | `POST /api/ImageCategories/update` | `ImageCategoriesController.Update` | ImageCategoriesController.Update | see contract | confirmed |
| BE-API-CONFIG-329 | `POST /api/ImageCategories/delete` | `ImageCategoriesController.DeleteSoft` | ImageCategoriesController.DeleteSoft | see contract | partial |
| BE-API-CONFIG-330 | `POST /api/Footer/getall` | `FooterController.GetAll` | FooterController.GetAll | see contract | partial |
| BE-API-CONFIG-331 | `POST /api/Footer/getbyid` | `FooterController.GetById` | FooterController.GetById | see contract | partial |
| BE-API-CONFIG-332 | `POST /api/Footer/create` | `FooterController.Create` | FooterController.Create | see contract | confirmed |
| BE-API-CONFIG-333 | `POST /api/Footer/update` | `FooterController.Update` | FooterController.Update | see contract | confirmed |
| BE-API-CONFIG-334 | `POST /api/Footer/delete` | `FooterController.Delete` | FooterController.Delete | see contract | partial |
| BE-API-CONFIG-335 | `POST /api/Country/getall` | `CountryController.GetAll` | CountryController.GetAll | see contract | partial |
| BE-API-CONFIG-336 | `POST /api/internal/mixxtip/staff/getmsisdn` | `MixxTipInternalController.GetStaffMsisdn` | MixxTipInternalController.GetStaffMsisdn | see contract | confirmed |
| BE-API-CONFIG-337 | `POST /api/dashboard` | `DashboardController.GetAll` | DashboardController.GetAll | see contract | confirmed |
| BE-API-CONFIG-338 | `POST /api/dashboard/GetDashboardData` | `DashboardController.GetDashboardData` | DashboardController.GetDashboardData | see contract | confirmed |
| BE-API-CONFIG-339 | `POST /api/dashboard/GetDashboardDataV2` | `DashboardController.GetDashboardDataV2` | DashboardController.GetDashboardDataV2 | see contract | confirmed |
| BE-API-CONFIG-340 | `POST /api/dashboard/GetBillerData` | `DashboardController.GetBillerData` | DashboardController.GetBillerData | see contract | confirmed |
| BE-API-CONFIG-341 | `POST /api/dashboard/GetDashboardAndBanners` | `DashboardController.GetDashboardAndBanners` | DashboardController.GetDashboardAndBanners | see contract | confirmed |
| BE-API-CONFIG-342 | `GET /api/dashboard/GetRediskey` | `DashboardController.GetAllKeys` | DashboardController.GetAllKeys | see contract | partial |
| BE-API-CONFIG-343 | `GET /api/dashboard/RemoveRedisKeys` | `DashboardController.RemoveRedisKeys` | DashboardController.RemoveRedisKeys | see contract | partial |
| BE-API-CONFIG-344 | `POST /api/dashboard/enc` | `DashboardController.enc` | DashboardController.enc | see contract | confirmed |
| BE-API-CONFIG-345 | `POST /api/dashboard/dec` | `DashboardController.dec` | DashboardController.dec | see contract | partial |
| BE-API-CONFIG-346 | `POST /api/dashboard/kikoba/items` | `DashboardController.GetKikobaDashboardItems` | DashboardController.GetKikobaDashboardItems | see contract | confirmed |
| BE-API-CONFIG-347 | `POST /api/dashboard/selfonboarding/items` | `DashboardController.GetSelfOnboardingItems` | DashboardController.GetSelfOnboardingItems | see contract | confirmed |
| BE-API-CONFIG-348 | `POST /api/dashboard/invite` | `DashboardController.GetInviteIcons` | DashboardController.GetInviteIcons | see contract | confirmed |
| BE-API-CONFIG-349 | `POST /api/LeaderboardApp/get` | `LeaderboardAppController.Get` | LeaderboardAppController.Get | see contract | confirmed |
| BE-API-CONFIG-350 | `POST /api/ResponseCodeApp/get` | `ResponseCodeAppController.Get` | ResponseCodeAppController.Get | see contract | confirmed |
| BE-API-CONFIG-351 | `POST /api/ResponseCodeApp/enc` | `ResponseCodeAppController.enc` | ResponseCodeAppController.enc | see contract | confirmed |
| BE-API-CONFIG-352 | `POST /api/ResponseCodeApp/dec` | `ResponseCodeAppController.dec` | ResponseCodeAppController.dec | see contract | partial |
| BE-API-CONFIG-353 | `GET /api/ResponseCodeApp/get-response-code-details/{responseCodeId}/{language}/{channel}` | `ResponseCodeAppController.GetResponseCodeDetails` | ResponseCodeAppController.GetResponseCodeDetails | see contract | partial |
| BE-API-CONFIG-354 | `POST /api/ResponseCodeApp/getAllAppConfig` | `ResponseCodeAppController.GetAllTableValues` | ResponseCodeAppController.GetAllTableValues | see contract | partial |
| BE-API-CONFIG-355 | `POST /api/BundlesApp/GetBundles` | `BundlesAppController.GetBundles` | BundlesAppController.GetBundles | see contract | confirmed |
| BE-API-CONFIG-356 | `POST /api/BundlesApp/GetBOBundles` | `BundlesAppController.GetBOBundles` | BundlesAppController.GetBOBundles | see contract | confirmed |
| BE-API-CONFIG-357 | `POST /api/BundlesApp/GetBOBundlesYas` | `BundlesAppController.GetBOBundlesYas` | BundlesAppController.GetBOBundlesYas | see contract | confirmed |
| BE-API-CONFIG-358 | `POST /api/BundlesApp/GetSeziakoBundles` | `BundlesAppController.GetSeziakoBundles` | BundlesAppController.GetSeziakoBundles | see contract | confirmed |
| BE-API-CONFIG-359 | `POST /api/BundlesApp/GetAllOperators` | `BundlesAppController.GetAllOperators` | BundlesAppController.GetAllOperators | see contract | confirmed |
| BE-API-CONFIG-360 | `POST /api/BundlesApp/encdatabundle` | `BundlesAppController.enc` | BundlesAppController.enc | see contract | confirmed |
| BE-API-CONFIG-361 | `POST /api/BundlesApp/decdatabundle` | `BundlesAppController.decdatabundle` | BundlesAppController.decdatabundle | see contract | partial |
| BE-API-CONFIG-362 | `POST /api/BundlesApp/decnetworkbundle` | `BundlesAppController.decnetworkbundle` | BundlesAppController.decnetworkbundle | see contract | partial |
| BE-API-CONFIG-363 | `POST /api/personalizedforyou/add` | `PersonalizedForYouAppController.Add` | PersonalizedForYouAppController.Add | see contract | confirmed |
| BE-API-CONFIG-364 | `POST /api/personalizedforyou/get` | `PersonalizedForYouAppController.Get` | PersonalizedForYouAppController.Get | see contract | confirmed |
| BE-API-CONFIG-365 | `POST /api/MerchantManagementApp/GetByMsisdn` | `MerchantManagementAppController.GetByMsisdn` | MerchantManagementAppController.GetByMsisdn | see contract | confirmed |
| BE-API-CONFIG-366 | `POST /api/MerchantManagementApp/CreateOwnerMerchant` | `MerchantManagementAppController.CreateOwnerMerchant` | MerchantManagementAppController.CreateOwnerMerchant | see contract | confirmed |
| BE-API-CONFIG-367 | `POST /api/MerchantManagementApp/GetPrivileges` | `MerchantManagementAppController.GetPrivileges` | MerchantManagementAppController.GetPrivileges | see contract | confirmed |
| BE-API-CONFIG-368 | `POST /api/MerchantManagementApp/UpdatePrivileges` | `MerchantManagementAppController.UpdatePrivileges` | MerchantManagementAppController.UpdatePrivileges | see contract | confirmed |
| BE-API-CONFIG-369 | `POST /api/MerchantManagementApp/enc` | `MerchantManagementAppController.enc` | MerchantManagementAppController.enc | see contract | confirmed |
| BE-API-CONFIG-370 | `POST /api/MerchantManagementApp/dec` | `MerchantManagementAppController.dec` | MerchantManagementAppController.dec | see contract | partial |
| BE-API-CONFIG-371 | `POST /api/MerchantManagementApp/decpreviliges` | `MerchantManagementAppController.decprivileges` | MerchantManagementAppController.decprivileges | see contract | partial |
| BE-API-CONFIG-372 | `POST /api/FaqApp/get` | `FaqAppController.Get` | FaqAppController.Get | see contract | confirmed |
| BE-API-CONFIG-373 | `POST /api/FaqApp/enc` | `FaqAppController.enc` | FaqAppController.enc | see contract | confirmed |
| BE-API-CONFIG-374 | `POST /api/FaqApp/dec` | `FaqAppController.dec` | FaqAppController.dec | see contract | partial |
| BE-API-CONFIG-375 | `POST /api/GamesApp/get` | `GamesAppController.Get` | GamesAppController.Get | see contract | confirmed |
| BE-API-CONFIG-376 | `POST /api/GamesApp/getScreenWise` | `GamesAppController.GetScreenWise` | GamesAppController.GetScreenWise | see contract | confirmed |
| BE-API-CONFIG-377 | `POST /api/ThemesApp/GetAll` | `ThemesAppController.GetAllCategories` | ThemesAppController.GetAllCategories | see contract | confirmed |
| BE-API-CONFIG-378 | `POST /api/ThemesApp/GetById` | `ThemesAppController.GetByCategoryId` | ThemesAppController.GetByCategoryId | see contract | confirmed |
| BE-API-CONFIG-379 | `POST /api/ThemesApp/enc` | `ThemesAppController.enc` | ThemesAppController.enc | see contract | confirmed |
| BE-API-CONFIG-380 | `POST /api/BankBillersApp/GetBankBillers` | `BankBillersAppController.GetBankBillers` | BankBillersAppController.GetBankBillers | see contract | confirmed |
| BE-API-CONFIG-381 | `POST /api/BankBillersApp/enc` | `BankBillersAppController.enc` | BankBillersAppController.enc | see contract | confirmed |
| BE-API-CONFIG-382 | `POST /api/BankBillersApp/dec` | `BankBillersAppController.dec` | BankBillersAppController.dec | see contract | partial |
| BE-API-CONFIG-383 | `POST /api/YasServices/get` | `YasServicesController.Get` | YasServicesController.Get | see contract | confirmed |
| BE-API-CONFIG-384 | `POST /api/MixxTipApp/eligibility` | `MixxTipAppController.Eligibility` | MixxTipAppController.Eligibility | see contract | confirmed |
| BE-API-CONFIG-385 | `POST /api/MixxTipApp/dec/eligibility` | `MixxTipAppController.DecEligibility` | MixxTipAppController.DecEligibility | see contract | partial |
| BE-API-CONFIG-386 | `POST /api/MixxTipApp/enc/eligibility` | `MixxTipAppController.EncEligibility` | MixxTipAppController.EncEligibility | see contract | confirmed |
| BE-API-CONFIG-387 | `POST /api/Podcast/Podcast` | `PodcastController.Podcast` | PodcastController.Podcast | see contract | confirmed |
| BE-API-CONFIG-388 | `POST /api/Podcast/enc` | `PodcastController.enc` | PodcastController.enc | see contract | confirmed |
| BE-API-CONFIG-389 | `POST /api/TvPressOffers/GetByDigitalSubscriptionParty` | `TvPressOffersController.GetByDigitalSubscriptionParty` | TvPressOffersController.GetByDigitalSubscriptionParty | see contract | confirmed |
| BE-API-CONFIG-390 | `POST /api/FiberProductApp/getall` | `FiberProductAppController.GetAll` | FiberProductAppController.GetAll | see contract | confirmed |
| BE-API-CONFIG-391 | `POST /api/AppCards/GetAppCards` | `AppCardsController.GetAllAppCards` | AppCardsController.GetAllAppCards | see contract | confirmed |
| BE-API-CONFIG-392 | `POST /api/AppCards/GetAllItems` | `AppCardsController.GetAllItems` | AppCardsController.GetAllItems | see contract | confirmed |
| BE-API-CONFIG-393 | `POST /api/Agents` | `AgentsController.GetAll` | AgentsController.GetAll | see contract | confirmed |
| BE-API-CONFIG-394 | `POST /api/Agents/GetAllAgents` | `AgentsController.GetAllAgents` | AgentsController.GetAllAgents | see contract | confirmed |
| BE-API-CONFIG-395 | `POST /api/TerrifApp/GetTerrifTransactionRules` | `TerrifAppController.GetTerrifTransactionRules` | TerrifAppController.GetTerrifTransactionRules | see contract | confirmed |
| BE-API-CONFIG-396 | `POST /api/AppImages/GetImagesByCategroy` | `AppImagesController.GetImagesByCategroy` | AppImagesController.GetImagesByCategroy | see contract | confirmed |
| BE-API-CONFIG-397 | `POST /api/BannerPromotionApp/get` | `BannerPromotionAppController.Get` | BannerPromotionAppController.Get | see contract | confirmed |
| BE-API-CONFIG-398 | `POST /api/BannerPromotionApp/dec` | `BannerPromotionAppController.dec` | BannerPromotionAppController.dec | see contract | partial |
| BE-API-CONFIG-399 | `POST /api/BannerPromotionApp/decbody` | `BannerPromotionAppController.decbody` | BannerPromotionAppController.decbody | see contract | partial |
| BE-API-CONFIG-400 | `POST /api/BannerPromotionApp/enc` | `BannerPromotionAppController.enc` | BannerPromotionAppController.enc | see contract | confirmed |
| BE-API-CONFIG-401 | `POST /api/ConfigurationApp/get` | `ConfigurationAppController.Get` | ConfigurationAppController.Get | see contract | confirmed |
| BE-API-CONFIG-402 | `POST /api/ConfigurationApp/enc` | `ConfigurationAppController.enc` | ConfigurationAppController.enc | see contract | confirmed |
| BE-API-CONFIG-403 | `POST /api/ConfigurationApp/dec` | `ConfigurationAppController.dec` | ConfigurationAppController.dec | see contract | partial |
| BE-API-CONFIG-404 | `POST /api/ConfigurationApp/getallmixxpointscategories` | `ConfigurationAppController.GetAllMixxPointsCategories` | ConfigurationAppController.GetAllMixxPointsCategories | see contract | confirmed |
| BE-API-CONFIG-405 | `POST /api/Mmp/MmpSubCategory/create` | `MmpSubCategoryController.Create` | MmpSubCategoryController.Create | see contract | confirmed |
| BE-API-CONFIG-406 | `POST /api/Mmp/MmpSubCategory/update` | `MmpSubCategoryController.Update` | MmpSubCategoryController.Update | see contract | confirmed |
| BE-API-CONFIG-407 | `POST /api/Mmp/MmpSubCategory/getbyid` | `MmpSubCategoryController.GetById` | MmpSubCategoryController.GetById | see contract | partial |
| BE-API-CONFIG-408 | `GET /api/Mmp/MmpSubCategory/getall` | `MmpSubCategoryController.GetAll` | MmpSubCategoryController.GetAll | see contract | partial |
| BE-API-CONFIG-409 | `POST /api/Mmp/MmpSubCategory/delete` | `MmpSubCategoryController.Delete` | MmpSubCategoryController.Delete | see contract | confirmed |
| BE-API-CONFIG-410 | `POST /api/Mmp/MmpCity/create` | `MmpCityController.Create` | MmpCityController.Create | see contract | confirmed |
| BE-API-CONFIG-411 | `POST /api/Mmp/MmpCity/update` | `MmpCityController.Update` | MmpCityController.Update | see contract | confirmed |
| BE-API-CONFIG-412 | `POST /api/Mmp/MmpCity/getbyid` | `MmpCityController.GetById` | MmpCityController.GetById | see contract | partial |
| BE-API-CONFIG-413 | `GET /api/Mmp/MmpCity/getall` | `MmpCityController.GetAll` | MmpCityController.GetAll | see contract | partial |
| BE-API-CONFIG-414 | `POST /api/Mmp/MmpCity/delete` | `MmpCityController.Delete` | MmpCityController.Delete | see contract | confirmed |
| BE-API-CONFIG-415 | `POST /api/Mmp/MmpCategory/create` | `MmpCategoryController.Create` | MmpCategoryController.Create | see contract | confirmed |
| BE-API-CONFIG-416 | `POST /api/Mmp/MmpCategory/update` | `MmpCategoryController.Update` | MmpCategoryController.Update | see contract | confirmed |
| BE-API-CONFIG-417 | `POST /api/Mmp/MmpCategory/getbyid` | `MmpCategoryController.GetById` | MmpCategoryController.GetById | see contract | partial |
| BE-API-CONFIG-418 | `GET /api/Mmp/MmpCategory/getall` | `MmpCategoryController.GetAll` | MmpCategoryController.GetAll | see contract | partial |
| BE-API-CONFIG-419 | `POST /api/Mmp/MmpCategory/delete` | `MmpCategoryController.Delete` | MmpCategoryController.Delete | see contract | confirmed |
| BE-API-CONFIG-420 | `POST /api/Mmp/MmpApp/GetAll` | `MmpAppController.GetAll` | MmpAppController.GetAll | see contract | confirmed |
| BE-API-CONFIG-421 | `POST /api/ManageFirebase/getall` | `ManageFirebase.GetFirebaseKeys` | ManageFirebase.GetFirebaseKeys | JWT + AuthorizationFilter | confirmed |
| BE-API-CONFIG-422 | `POST /api/ManageFirebase/update` | `ManageFirebase.UpdateFirebaseKey` | ManageFirebase.UpdateFirebaseKey | JWT + AuthorizationFilter | confirmed |
| BE-API-CONFIG-423 | `POST /api/ManageFirebase/refreshKey` | `ManageFirebase.refreshFirebaseKey` | ManageFirebase.refreshFirebaseKey | JWT + AuthorizationFilter | confirmed |
| BE-API-CONFIG-424 | `POST /api/ManageFirebase/delete` | `ManageFirebase.DeleteSectionItemAsync` | ManageFirebase.DeleteSectionItemAsync | JWT + AuthorizationFilter | confirmed |
| BE-API-CONFIG-425 | `POST /api/TimeBasedIcon/gettimebasedsections` | `TimeBasedIcon.GetTimeBasedSections` | TimeBasedIcon.GetTimeBasedSections | JWT + AuthorizationFilter | confirmed |
| BE-API-CONFIG-426 | `POST /api/TimeBasedIcon/gettimebasedsubsections` | `TimeBasedIcon.GetTimeBasedSubsections` | TimeBasedIcon.GetTimeBasedSubsections | JWT + AuthorizationFilter | confirmed |
| BE-API-CONFIG-427 | `POST /api/TimeBasedIcon/getall` | `TimeBasedIcon.GetTimeBasedIcons` | TimeBasedIcon.GetTimeBasedIcons | JWT + AuthorizationFilter | confirmed |
| BE-API-CONFIG-428 | `POST /api/TimeBasedIcon/update` | `TimeBasedIcon.SaveSectionItemAsync` | TimeBasedIcon.SaveSectionItemAsync | JWT + AuthorizationFilter | confirmed |
| BE-API-CONFIG-429 | `POST /api/TimeBasedIcon/create` | `TimeBasedIcon.CreateItemAsync` | TimeBasedIcon.CreateItemAsync | JWT + AuthorizationFilter | confirmed |
| BE-API-CONFIG-430 | `POST /api/TimeBasedIcon/delete` | `TimeBasedIcon.DeleteSectionItemAsync` | TimeBasedIcon.DeleteSectionItemAsync | JWT + AuthorizationFilter | confirmed |

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
| `imagecategory` / `imagecategory` | EF set |
| `imagesubcategory` / `imagesubcategory` | EF set |
| `tvpressoffers` / `tvpressoffers` | EF set |
| `translations` / `translations` | EF set |
| `terrifunits` / `terrifunits` | EF set |
| `terrifamounttype` / `terrifamounttype` | EF set |
| `translationsmessages` / `translationsmessages` | EF set |
| `gsmdatabundles` / `gsmdatabundles` | EF set |
| `auditlog` / `auditlogs` | EF set |
| `gsmnetworkbundles` / `gsmnetworkbundles` | EF set |
| `gsmbundles` / `gsmbundles` | EF set |
| `bankbillers` / `bankbillers` | EF set |
| `giftthemecategory` / `themecategories` | EF set |
| `gifttheme` / `themes` | EF set |
| `giftmoneyrecord` / `giftmoneyrecord` | EF set |
| `ownermerchants` / `ownermerchants` | EF set |
| `appcard` / `appcards` | EF set |
| `mchangoaccountconfiguration` / `mchangoaccountconfiguration` | EF set |
| `mchangoqrconfiguration` / `mchangoqrconfiguration` | EF set |
| `mchangointerestconfiguration` / `mchangointerestconfiguration` | EF set |
| `MerchantQRConfiguration` / `MerchantQRConfiguration` | EF set |
| `MerchantReqToPayConfigurations` / `MerchantReqToPayConfigurations` | EF set |
| `airtimeoperator` / `airtimeoperators` | EF set |
| `ConsumerQRConfiguration` / `consumerqrconfiguration` | EF set |
| `fiberproduct` / `fiberproduct` | EF set |
| `customermsisdn` / `customermsisdn` | EF set |
| `kikobadashboarditem` / `kikobadashboarditem` | EF set |
| `inviteicon` / `inviteicon` | EF set |
| `selfonboardingitem` / `selfonboardingitem` | EF set |
| `homelayoutsection` / `homelayoutsection` | EF set |
| `homecarouselcard` / `homecarouselcard` | EF set |
| `menuitem` / `menuitem` | EF set |
| `appfooter` / `appfooter` | EF set |
| `personalizedforyouitem` / `personalizedforyouitem` | EF set |
| `personalizedforyouuserdata` / `personalizedforyouuserdata` | EF set |
| `dashboardlayout` / `dashboardlayout` | EF set |
| `dashboardconfig` / `dashboardconfig` | EF set |
| `mmpcity` / `mmpcities` | EF set |
| `mppcategory` / `mppcategories` | EF set |
| `mppsubcategory` / `mppsubcategories` | EF set |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`AzureBlobStorage:<redacted-purpose>`, `AzureBlobStorage:BannerContainer`, `AzureBlobStorage:DashboardContainer`, `AzureBlobStorage:DiasporaContainer`, `AzureBlobStorage:GamesContainer`, `AzureBlobStorage:PodcastContainer`, `AzureBlobStorage:StockContainer`, `AzureBlobStorage:UserJourneyContainer`, `CacheExpiry`, `ConfigurationInternalApi:ApiKey`, `DBServerUrl`, `DiasporaRegistrationAPI:InternationalRegistrationURL`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `EnableLog:Warning`, `Encryption_Decryption_Key`, `FCMNotify`, `FireBaseUser:<redacted-purpose>`, `FireBaseUser:email`, `FirebaseAuthClient:ApiKey`, `FirebaseAuthClient:AuthDomain`, `FirebaseClient:<redacted-purpose>`, `FirebaseClient:BasePath`, `FirebaseDbName`, `FlowIds`, `IV`, `IdentityApi:InternalApiKey`, `IsRedisCluster`, `Origins`, `PelatroOffers:ApiKey`, `PelatroOffers:ClientId`, `PelatroOffers:Url`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:IsHttpsRabbitMQ`, `RabbitMQ:LogQueueName`, `RabbitMQ:LogURL`, `RabbitMQ:Port`, `RabbitMQ:Username`, `RedisPassword (key name)<redacted-purpose>`

## Open questions
- Gateway public URLs not in-repo.
