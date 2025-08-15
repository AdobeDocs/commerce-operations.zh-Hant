---
title: ACSD-51645：如果Magento_OfflineShipping擴充功能已停用，儲存新的購物車價格規則
description: 套用ACSD-51645修補程式來修正Adobe Commerce問題，此問題會在停用Magento_OfflineShipping擴充功能的情況下儲存新的購物車價格規則時發生錯誤。
exl-id: ce747ae4-6d2f-41c0-ba75-7da72be359c7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-51645：如果Magento_OfflineShipping擴充功能已停用，儲存新的購物車價格規則

ACSD-51645修補程式修正了在停用Magento_OfflineShipping擴充功能的情況下，儲存新的購物車價格規則時發生錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33時，即可使用此修補程式。 修補程式ID為ACSD-51645。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果擴充功能`Magento_OfflineShipping`已停用，儲存新的購物車價格規則時發生錯誤。

<u>要再現的步驟</u>：

1. 停用`Magento_OfflineShipping`模組。
1. 登入&#x200B;**管理員**。
1. 前往&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**。
1. 建立新的&#x200B;**[!UICONTROL Cart Price Rule]**。
1. 填寫必填欄位。
1. 儲存&#x200B;**[!UICONTROL Cart Price Rule]**。

<u>預期結果</u>：

已成功儲存購物車價格規則。

<u>實際結果</u>：

發生下列錯誤：
`report.ERROR: Warning: Undefined array key "simple_free_shipping" in app/code/Magento/SalesRule/Controller/Adminhtml/Promo/Quote/Save.php on line 67 [] []`

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)：搜尋修補程式[!DNL Quality Patches Tool]。
