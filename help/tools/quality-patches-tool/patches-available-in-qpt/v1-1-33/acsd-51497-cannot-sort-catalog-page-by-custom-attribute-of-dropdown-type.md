---
title: ACSD-51497：無法依「下拉式清單」型別的自訂屬性排序目錄頁面
description: 套用ACSD-51497修補程式，修正Adobe Commerce中客戶無法依下拉式清單型別的自訂屬性排序目錄頁面的問題。
feature: Attributes, Cache, Catalog Management, Categories
role: Developer
exl-id: c66a7e04-fd2a-47be-8f7a-7982780a5414
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# ACSD-51497：無法依型別&#x200B;*Dropdown*&#x200B;的自訂屬性排序目錄頁面

ACSD-51497修補程式修正客戶無法依型別&#x200B;*下拉式清單*&#x200B;的自訂屬性排序目錄頁面的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33時，即可使用此修補程式。 修補程式ID為ACSD-51497。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.3.7-p4， 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

客戶無法依型別&#x200B;*下拉式清單*&#x200B;的自訂屬性排序目錄頁面。

<u>要再現的步驟</u>

1. 建立大約6個簡單產品，並將其指派給單一類別。
1. 建立產品屬性，以便在清單頁面上將其新增為排序選項。

   * 前往「**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Add New Attribute]**」。
   * 在&#x200B;**[!UICONTROL Properties]**&#x200B;索引標籤中，設定下列專案：

      * *[!UICONTROL Default Label]* = *測試*
      * 存放區擁有者的&#x200B;*[!UICONTROL Catalog Input Type]* = *下拉式清單*
      * *[!UICONTROL Options]*：

         * *第一個*
         * *秒*
         * *第三*
         * *第四*

   * 在&#x200B;**[!UICONTROL Storefront Properties]**&#x200B;索引標籤中，設定下列專案：

      * *[!UICONTROL Used for sorting in product listing]* = *是*
      * 將所有其他選項保留為&#x200B;*預設*。

1. 將&#x200B;*test*&#x200B;屬性指派給&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**&#x200B;中設定的&#x200B;*預設*&#x200B;屬性。
1. 將產品設定為具有&#x200B;*test*&#x200B;屬性值。

   * SKU： s00001，測試：第四
   * SKU： s00002，測試：第三
   * SKU： s00003，測試：秒
   * SKU： s00004，測試：第一個
   * SKU： s00005，測試：第四
   * SKU： s00006，測試：第三

1. 重新索引並清除快取。
1. 前往店面上的類別。
1. 依&#x200B;*test*&#x200B;屬性排序。

<u>預期結果</u>：

產品會依&#x200B;*test*&#x200B;屬性排序。

<u>實際結果</u>：

產品未依&#x200B;*test*&#x200B;屬性排序。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
