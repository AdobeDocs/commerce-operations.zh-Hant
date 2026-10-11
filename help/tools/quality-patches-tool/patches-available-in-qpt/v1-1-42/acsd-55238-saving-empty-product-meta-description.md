---
title: ACSD-55238：儲存空的產品中繼說明
description: 套用ACSD-55238修補程式以修正Adobe Commerce問題，其中中繼說明一律會顯示包含[!DNL Page Builder]或其他HTML編輯器產生的HTML程式碼的產品說明，且無法將它設定為空白。
feature: Products, Page Builder, Page Content
role: Admin, Developer
exl-id: 39ccf1bb-a71a-47a0-b252-e6331e2df9b0
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
    internal-label: Developer tools
subfeature_v2:
  - id: ed510963-0b8c-4764-86f6-f3c7735bc334
    internal-label: Page Builder
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%
---
# ACSD-55238：儲存空的產品中繼說明

ACSD-55238修補程式修正中繼說明中一律顯示包含HTML編輯器所產生HTML程式碼的產品說明的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.42時，即可使用此修補程式。 修補程式ID為ACSD-55238。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

包含[!DNL Page Builder]或其他HTML編輯器產生的HTML程式碼的產品說明一律會顯示在中繼說明中，且無法將其設為空白。

<u>要再現的步驟</u>：

1. 前往「**[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Block]**」，並使用任何內容建立新區塊。
1. 前往「**[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product]**」並建立新產品。 將中繼說明設定為空白。
1. 在&#x200B;*[!UICONTROL Content]*&#x200B;索引標籤中使用&#x200B;*[!DNL Page Builder]*&#x200B;新增上面建立的區塊，並儲存產品。
1. 在店面開啟產品並檢查其doc元素`meta name = "description"`。

<u>預期結果</u>：

中繼說明是空的。

<u>實際結果</u>：

當產品的描述中有區塊時，即會用於產品中繼描述。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
