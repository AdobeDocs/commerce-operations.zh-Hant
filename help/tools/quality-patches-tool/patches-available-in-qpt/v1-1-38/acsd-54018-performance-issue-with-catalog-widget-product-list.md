---
title: ACSD-54018：目錄Widget產品清單的效能問題
description: 套用ACSD-54018修補程式，修正在新增具有條件和屬性型別布林值的目錄Widget產品清單時，頁面載入緩慢的Adobe Commerce問題。
feature: Attributes, Catalog Management, Page Builder, Page Content, Storefront
role: Admin, Developer
exl-id: 2fb7ca37-78cc-45f4-86a3-d922cf4d1457
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-54018：目錄Widget產品清單的效能問題

ACSD-54018修補程式修正新增附有條件和屬性型別布林值的目錄Widget產品清單時，頁面載入緩慢的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.38時，即可使用此修補程式。 修補程式ID為ACSD-54018。 請注意，問題已在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

新增具有條件和屬性型別布林值的目錄Widget產品清單時，頁面載入速度緩慢。

<u>要再現的步驟</u>：

1. 產生100,000種產品。
1. 建立範圍設定為[!UICONTROL Store View]的bool屬性。
1. 將屬性指派給所有屬性集。
   * 將屬性值&#x200B;*是*&#x200B;指派給所有產品。
1. 現在移至「**[!UICONTROL Catalog]** > **[!UICONTROL Products]**」，並選取所有100k產品。
   * 選擇&#x200B;**[!UICONTROL Actions]** > **[!UICONTROL Update Attribute]**。
   * 將bool屬性設定為&#x200B;*是*&#x200B;並儲存。
   * 如果您已登出此步驟，請檢查&#x200B;*附註*。
1. 移至CLI並執行`php bin/magento queue:con:start product_action_attribute.update`。
   * 請確定所有產品的屬性均已更新。
1. 現在移至&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Pages]**&#x200B;並建立新頁面。
1. 開啟&#x200B;**[!UICONTROL Page Builder]** > **[!UICONTROL Add row]** > **[!UICONTROL Add Content]** > **[!UICONTROL Products]**。
1. 選擇&#x200B;*[!UICONTROL Select Products By]* = *[!UICONTROL Condition]*。
1. 將條件&#x200B;*[!UICONTROL Created attribute]*&#x200B;設定為&#x200B;*[!UICONTROL Yes]*&#x200B;並儲存。
1. 前往前端，並開啟建立的頁面。
1. 停用全頁快取並封鎖html快取。
1. 檢查頁面載入速度。
1. 重新載入頁面幾次，然後計算平均載入時間。

<u>預期結果</u>：

頁面載入迅速。

<u>實際結果</u>：

載入頁面需要5到10秒。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
