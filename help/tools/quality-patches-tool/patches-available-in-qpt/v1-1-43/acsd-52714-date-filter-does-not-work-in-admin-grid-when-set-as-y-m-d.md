---
title: ACSD-52714：設定為y-m-d時，日期篩選器在管理格線中無法運作
description: 套用ACSD-52714修補程式，修正日期格式設為y-m-d時，日期篩選器在管理格線中無法運作的Adobe Commerce問題。
feature: Attributes
role: Admin, Developer
exl-id: 4a34900b-9566-41bb-8d3e-18a440117907
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-52714：設定為y-m-d時，日期篩選器在管理格線中無法運作

ACSD-52714修補程式修正日期格式設為y-m-d時，日期篩選器在管理格線中無法運作的問題。安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43時，即可使用此修補程式。 修補程式ID為ACSD-52714。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

日期格式設為y-m-d時，日期篩選器無法在管理網格中運作。

<u>要再現的步驟</u>：

1. 安裝乾淨的Adobe Commerce。
1. 編輯
   `/app/code/Magento/Customer/view/adminhtml/ui_component/customer_listing.xml`
檔案並新增
   `<dateFormat>Y-MM-dd</dateFormat>`
至
   `<column name="created_at" class="Magento\Ui\Component\Listing\Columns\Date" component="Magento_Ui/js/grid/columns/date" sortOrder="100">`
在標籤下
   `<dataType>date</dataType>`

1. 排清快取`bin/magento c:f`。
1. 登入Admin並從&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL All Customers]**&#x200B;建立新客戶。

   * 起始：目前日期減1天
   * 至：目前日期

1. 按一下&#x200B;**[!UICONTROL Apply Filters]**。

<u>預期結果</u>：

格線的日期篩選器不論地區設定為何，皆可正常運作。

<u>實際結果</u>：

出現下列訊息： *我們找不到任何記錄*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
