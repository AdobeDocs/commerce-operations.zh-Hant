---
title: ACSD-64137：依郵遞區號搜尋取車地點不適用於荷蘭本地化
description: 套用ACSD-64137修補程式，修正依郵遞區號搜尋取件位置不適用於荷蘭當地語系化的問題。
feature: Shipping/Delivery
role: Admin, Developer
source-git-commit: 4947133daaffb919aeba986c8a6b88ecb2e1b943
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---


# ACSD-64137：依郵遞區號搜尋取車地點不適用於荷蘭本地化

ACSD-64137修補程式修正荷蘭本地化無法依郵遞區號正確搜尋收取位置的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60時，即可使用此修補程式。 修補程式ID為ACSD-64137。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

荷蘭的郵遞區號搜尋沒有在前端結帳頁面上顯示結果。 然而，它依城市運作，且顯示對應的地址時不會進行搜尋。

<u>要再現的步驟</u>：

1. 安裝具有清查模組的乾淨執行個體。
1. 建立自訂庫存。
1. 使用荷蘭地址建立兩個來源，並將它們指派給庫存（郵遞區號7311ER和7311AE）。
1. 建立簡單產品並新增詳細目錄。
1. 導覽至「**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]**」以啟用&#x200B;**[!UICONTROL In-Store Delivery]**。
1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Distance Provider for Distance Based SSA]**」。 將&#x200B;**[!UICONTROL Provider]**&#x200B;設定為&#x200B;*離線計算*。
1. 執行以下命令，匯入NL國家/地區的地理名稱。

   ```bash
   bin/magento inventory-geonames:import NL
   ```

1. 將產品新增到購物車並前往送貨步驟。
1. 選取&#x200B;**[!UICONTROL Pick In Store]**。 然後，按一下&#x200B;**[!UICONTROL Select Other]**&#x200B;以選取其他商店。
1. 在&#x200B;**[!UICONTROL Select Store]**&#x200B;搜尋表單中輸入&#x200B;*7311*&#x200B;或&#x200B;*7311AE*。


**預期結果**：

* 應填入相符存放區。

**實際結果**：

* 找不到結果。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
