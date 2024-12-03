---
title: ACSD-56246：排程產品更新時清除多選屬性值
description: 套用ACSD-56246修補程式，修正排程產品更新清除多選屬性值之Adobe Commerce問題。
feature: Products, Attributes, Staging
role: Admin, Developer
exl-id: 1751a03d-2610-423f-be2f-b9d060452904
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-56246：排程產品更新會清除多選屬性值

ACSD-56246修補程式修正了排程產品更新清除多選屬性值的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44時，即可使用此修補程式。 修補程式ID為ACSD-56246。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

排程的產品更新會清除多選屬性值。

<u>要再現的步驟</u>：

1. 安裝Adobe Commerce。
1. 前往「**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**」並建立下列屬性：

   * 預設標籤：方案
   * 存放區所有者的目錄輸入型別：多重選取
   * 管理選項（您屬性的值）：Choice、Sunscape、Safetyshield
   * 屬性代碼： customer_program
   * 範圍：全域
   * 新增至欄選項：否
   * 使用篩選器選項：否
   * 店面屬性
   * 位置： *333*
   * 允許在店面使用HTML標籤：否

1. 執行
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`。
1. 執行
   `bin/magento setup:upgrade`。
1. 移至「**[!UICONTROL Admin]**」>「挑選任何簡單產品」>「選取方案屬性中的所有專案」>「按一下&#x200B;**[!UICONTROL Save the product]**」。
1. 排程在下一分鐘更新此產品，並執行以下命令以讓內容測試作業：
   `for i in {1..100}; do bin/magento cron:run; done`。

<u>預期結果</u>：

產品的&#x200B;**[!UICONTROL program]**&#x200B;屬性不應變更。

<u>實際結果</u>：

產品的&#x200B;**[!UICONTROL program]**&#x200B;屬性已清除。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
