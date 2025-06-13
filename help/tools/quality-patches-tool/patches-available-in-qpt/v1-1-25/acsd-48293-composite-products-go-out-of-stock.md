---
title: ACSD-48293：複合產品無庫存（已售出）子產品已補充庫存
description: 套用ACSD-48293修補程式來修正Adobe Commerce問題，此問題發生在售出的子產品恢復庫存時，複合產品會缺貨。
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: 2aa75e97-373e-4e4a-a545-69bce807ca4d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# ACSD-48293：複合產品無庫存（已售出）子產品已補充庫存

ACSD-48293修補程式修正當已售出的子產品恢復庫存時，複合產品缺貨的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25時，即可使用此修補程式。 修補程式ID為ACSD-48293。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當已售出的子產品返回到庫存時，複合產品會缺貨。

<u>要再現的步驟</u>：

1. 建立次要網站、商店和商店檢視。
1. 建立兩個來源和庫存，並將其指派給每個網站。
1. 在&#x200B;**[!UICONTROL Store]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** > **[!UICONTROL Display Out-of-Stock Products]** = *[!UICONTROL Yes]*&#x200B;下啟用顯示無存貨產品選項。
1. 使用主要網站的庫存來源（設定數量= 1），以一個關聯產品建立可設定產品。
1. 為可設定產品下訂單。
1. 執行cron。
1. 從店面開啟可設定的產品，並確認其無庫存。
1. 從[!UICONTROL Admin]開啟可設定的產品並將&#x200B;**[!UICONTROL Manage Stock Option]**&#x200B;設定為&#x200B;*[!UICONTROL No]*。
1. 執行cron。
1. 出貨訂單，並將數量新增至簡易產品，使其備貨。
1. 執行cron。
1. 檢查店面的產品可用性。

<u>預期結果</u>：

可設定的產品有庫存。

<u>實際結果</u>：

可設定的產品沒有庫存。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
