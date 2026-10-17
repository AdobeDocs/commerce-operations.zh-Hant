---
title: ACSD-49065：報價專案在管理員中不可見
description: 套用ACSD-49065修補程式來修正Adobe Commerce問題，亦即如果報價專案僅指派給自訂庫存，則無法在管理員中看到報價專案。
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
exl-id: fc3bea92-305b-4598-9915-3422d61c76ec
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 792a7e9b-6519-5e99-a913-56c3dd2408da
    internal-label: Quotes
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%
---
# ACSD-49065：報價專案在管理員中不可見

ACSD-49065修補程式修正了報價專案僅指定給自訂庫存時無法在管理員中顯示的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.28時，即可使用此修補程式。 修補程式ID為ACSD-49065。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果報價專案僅指派給自訂庫存，則不會在管理員中顯示。

先決條件：

必須安裝&#x200B;**[!UICONTROL B2B]**&#x200B;與&#x200B;**[!UICONTROL Inventory]**&#x200B;模組。

<u>要再現的步驟</u>：

1. 在&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**&#x200B;下啟用&#x200B;**[!UICONTROL Company]**&#x200B;和&#x200B;**[!UICONTROL B2B Quote]**。
1. 建立次要&#x200B;**[!UICONTROL Inventory Source]**&#x200B;並將其指派給次要&#x200B;**[!UICONTROL Inventory Stock]**。
1. 僅指派次要（非預設） **[!UICONTROL Inventory Source]**&#x200B;以建立新產品。
1. 前往店面並建立新的公司帳戶。 以&#x200B;**[!UICONTROL Company Admin]**&#x200B;身分登入，並將建立的產品加入購物車。
1. 瀏覽到購物車和&#x200B;*[!UICONTROL Request a Quote]*。
1. 前往管理員，並在&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Quotes]**&#x200B;檢視要求的報價。

<u>預期結果</u>：

專案會顯示在以新產品建立的新報價中，而不需重新儲存產品。

<u>實際結果</u>：

*[!UICONTROL Items Quoted]*&#x200B;區段是空的。 如果您重新儲存新建立的產品，專案就會出現。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
