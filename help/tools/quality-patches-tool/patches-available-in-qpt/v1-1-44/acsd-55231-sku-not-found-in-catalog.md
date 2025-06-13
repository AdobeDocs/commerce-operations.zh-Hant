---
title: ACSD-55231：使用快速訂購功能時找不到SKU錯誤
description: 套用ACSD-55231修補程式，修正您收到*「在目錄中找不到SKU」*的錯誤（嘗試使用快速訂購功能將產品新增至購物車時）。Adobe Commerce
feature: Products, Checkout, B2B
role: Admin, Developer
exl-id: f0a04773-7395-4945-a72b-5a6a018bc94e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# ACSD-55231：使用快速訂購功能時找不到SKU錯誤

ACSD-55231修補程式修正了您取得&#x200B;*「嘗試使用快速訂購功能將產品新增到購物車時，在目錄「*」中找不到SKU錯誤。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44時，即可使用此修補程式。 修補程式ID為ACSD-55231。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

取得&#x200B;*&#39;使用快速訂購功能搜尋要新增至購物車的產品時，在目錄&#39;*&#x200B;中找不到SKU錯誤。

<u>要再現的步驟</u>：

1. 安裝Adobe Commerce搭配B2B模組。
1. 導覽至「**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]**」並設定：
   * **[!UICONTROL Enable company]**： *是*
   * **[!UICONTROL Enable Shared Catalog]**： *是*
   * **[!UICONTROL Enable Quick Order]**： *是*
1. 儲存上述設定。
1. 前往&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]**&#x200B;並建立新的共用目錄。
1. 導覽至「**[!UICONTROL Customers]** > **[!UICONTROL All Customers]**」並建立新客戶：
   * 在群組欄位中，選擇最近建立的共用目錄，並將&#x200B;*[!UICONTROL Allow remote shopping assistance]*&#x200B;設定為&#x200B;*是*。
1. 產生SKU為&#x200B;*p12*&#x200B;的簡單產品，將其與類別&#x200B;*c1*&#x200B;建立關聯，然後在[!UICONTROL Product in Shared Catalog]區段中選擇新建立的共用目錄。
1. 執行：

   ```
   bin/magento ind:rei 
   bin/magento c:f 
   bin/magento cron:run (multiple times)
   ```

1. 重新整理管理頁面。
1. 導覽至「**[!UICONTROL Customers]** > **[!UICONTROL All Customers]**」並編輯先前建立的客戶。
1. 按一下&#x200B;**[!UICONTROL Login as customer]**。
1. 移至&#x200B;**[!UICONTROL Quick order]**。
1. 搜尋&#x200B;*p12* SKU並按一下&#x200B;**[!UICONTROL Product Suggestion]**。
1. 將此產品加入購物車並下訂單。
1. 返回&#x200B;**[!UICONTROL Quick Order]**，再次搜尋SKU *p12*，然後按一下&#x200B;**[!UICONTROL Product Suggestion]**。

<u>預期結果</u>：

您可以使用快速訂購功能將產品新增到購物車。

<u>實際結果</u>：

您無法使用快速訂購功能將產品新增到購物車並取得&#x200B;*&#39;在搜尋產品SKU時，在目錄&#39;*&#x200B;中找不到SKU發生錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
