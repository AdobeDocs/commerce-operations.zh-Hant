---
title: 'ACSD-52133：升級後無法儲存客戶帳戶'
description: 套用ACSD-52133修補程式，修正Adobe Commerce升級後無法儲存客戶帳戶的問題。
feature: Customers, Upgrade
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-52133：升級後無法儲存客戶帳戶

ACSD-52133修補程式修正了升級後無法儲存客戶帳戶的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.35時，即可使用此修補程式。 修補程式ID為ACSD-52133。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

升級後無法儲存客戶帳戶。

<u>要再現的步驟</u>：

1. 安裝Adobe Commerce 2.4.4版。
1. 建立客戶。
1. 將Adobe Commerce從已建立客戶的舊版2.4.4升級至2.4.6。
1. 在`env.php`中設定加密金鑰，如下所示：

   `d337b914e91ff703b1e94ba4156aadf0`

1. 在`customer_entity`資料表下的任何客戶中，將下列值設定到資料庫中：

   ```
   -> rp_token as incr4869
   -> rp_token_created_at as "2021-04-29 20:06:14"
   ```

1. 前往&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**。
1. 編輯上述值已更新的客戶。
1. 按一下&#x200B;**[!UICONTROL Save Customer]**&#x200B;或&#x200B;**[!UICONTROL Save and Continue Edit]**

<u>預期結果</u>：

已成功儲存客戶且沒有錯誤。

<u>實際結果</u>：

* 未儲存客戶記錄。
* 管理員看到下列錯誤訊息： *儲存客戶時發生錯誤。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
