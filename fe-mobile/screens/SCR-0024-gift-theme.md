---
kb_section: fe-mobile
type: screen
ids: [SCR-0024, SCR-0025]
feature: tanzania_gift
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# SCR-0024 Gift theme (`TanzaniaGiftWidget`)

**Controller:** `TanzaniaGiftWidgetController` · **Flow:** FLW-0009 · **APIs:** API-0097, API-0098

## Entry

After a gift receiver is chosen. `onInit` calls `getGiftTheme`, which only fills a local label list. The network calls run from `onReady`.

## Actions

| Action | Validation | API | Result |
|---|---|---|---|
| Categories | Cache miss or version mismatch | API-0097 | `responseData[]` `id`, `name`, `iconUrl`. Cached without encryption |
| Themes | First category id, unless the theme cache matches | API-0098 | `responseData[]` `id`, `imageUrl`, `message`, `bgColor`, `foreground` |
| Next | A theme is selected | — | SCR-0025 |

When pre-login `isvalentine` is `true`, a category named `Valentine Day` is sorted first, and a theme whose `message` is `Event` supplies the gradient colors (BR-0019).

# SCR-0025 Gift preview (`TanzaniaGiftPreviewWidget`)

No API of its own. Send now opens `SendMoneyConfirmationWidget` (SCR-0010) with `themeId`, `catagoryId`, `message`, category URL, and theme URL.

The button contains `useCaseType == UseCaseTypes.giftMoney` as a comparison. It does not assign `useCaseType`.

The confirm controller then calls API-0099 when the gift fields were stored by `setValuesForGift`.

## Evidence

- `lib/ui/controllers/tanzania_gift/tanzania_festive_gift/tanzania_gift_widget_controller.dart` @ `6328b7254`
- `lib/ui/widgets/tanzania_gift/tanzania_festive_gift/tanzania_gift_preview_widget.dart` › `getNextButtonContainer`
- `lib/ui/controllers/sendmoney/send_money_confirmation_controller.dart` › `requestSendMoneyProcessPaymentForGift`
