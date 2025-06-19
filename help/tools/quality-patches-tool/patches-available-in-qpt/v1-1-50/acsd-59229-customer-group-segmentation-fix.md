---
title: ACSD-59229：由於過期的X-Magento-Vary值，導致客戶群組資料配置錯誤
description: 套用ACSD-59229修補程式以修正Adobe Commerce問題，該問題導致客戶群組相關資訊因請求中的過時X-Magento-Vary值而儲存在錯誤的區段中。
feature: Customers, Personalization, Marketing Tools
role: Admin, Developer
exl-id: c039c114-d920-4b05-b5e9-3e9b73490ee0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# ACSD-59229：由於過期的X-Magento-Vary值，導致客戶群組資料配置錯誤

ACSD-59229修補程式修正客戶群組相關資訊因請求中的過時X-Magento-Vary值而儲存在錯誤區段的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50時，即可使用此修補程式。 修補程式ID為ACSD-59229。 請注意，問題已在2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

客戶群組相關資訊會儲存在錯誤的區段中，因為請求中的過時X-Magento-Vary值。

<u>必要條件</u>：

請確定已安裝包含範例資料的Adobe Commerce B2B且已設定[!DNL Varnish]。

<u>要再現的步驟</u>：

1. 設定[!DNL SKU 24-MB01]的進階定價：
   1. [!UICONTROL Regular price] = *9999$*
   1. [!UICONTROL Catalog and Tier Price]：
      * *批發* = *$200*
      * *Retailer* = *$30*

1. 建立兩個客戶帳戶。
1. 將兩個客戶指派給&#x200B;**批發**&#x200B;群組。
1. 開啟兩個不同的瀏覽器工作階段，並與每個客戶登入。
1. 導覽至每個客戶的&#x200B;**[!UICONTROL 24-MB01]**&#x200B;產品頁面，並確認顯示的價格為&#x200B;*$200*。
1. 將其中一個客戶的客戶群組變更為&#x200B;**零售業**。
1. 使用下列命令清除快取： `bin/magento cache:flush full_page`。
1. 重新整理每個客戶的產品頁面。

<u>預期結果</u>：

1. 零售客戶可看到產品的&#x200B;*$30*&#x200B;正確價格。
1. 批發客戶可看到產品的&#x200B;*$200*&#x200B;的正確價格。

<u>實際結果</u>：

1. 零售客戶可看到產品的&#x200B;*$30*&#x200B;正確價格。
1. 批發客戶看到產品的&#x200B;*$30* （零售價）價格不正確。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
