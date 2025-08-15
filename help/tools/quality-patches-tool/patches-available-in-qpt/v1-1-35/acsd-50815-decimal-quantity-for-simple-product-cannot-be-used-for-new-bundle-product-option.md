---
title: ACSD-50815：簡單產品的小數數量無法用於新的套件產品選項
description: 套用ACSD-50815修補程式，修正Adobe Commerce中簡單產品的小數點數量無法用於新捆綁產品選項的問題。
feature: Products
role: Admin
exl-id: 5cd69abe-bd88-497d-9696-804c787b73ef
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-50815：簡單產品的小數數量無法用於新的套件產品選項

ACSD-50815修補程式修正了簡單產品的小數數量無法用於新捆綁產品選項的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.35時，即可使用此修補程式。 修補程式ID為ACSD-50815。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

簡單產品的小數數量無法用於新的套裝產品選項。

<u>要再現的步驟</u>：

1. 以管理員身分登入。
1. 建立新的簡單產品。
   * 在&#x200B;**[!UICONTROL Advanced Inventory]**&#x200B;視窗中，設定[!UICONTROL Qty Uses Decimal] = [!UICONTROL Yes]。
   * 儲存簡單產品。
1. 建立新的套件產品。
1. 新增任何選項。
1. 將簡單產品新增至此選項。
1. 在套件產品選項中設定簡單產品的小數數量。 例如1.5。

<u>預期結果</u>：

可以設定小數數量。 不會顯示任何錯誤。

<u>實際結果</u>：

錯誤，*請在此欄位*&#x200B;中輸入有效數字。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
