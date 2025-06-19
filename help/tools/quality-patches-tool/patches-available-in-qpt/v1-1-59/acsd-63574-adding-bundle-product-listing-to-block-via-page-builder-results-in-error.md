---
title: ACSD-63574：將[!UICONTROL Bundle Product]清單新增至via [!DNL Page Builder] 的區塊導致錯誤
description: 套用ACSD-63574修補程式以修正Adobe Commerce的問題，其中使用「Checkbox」或「Multi Select」選項新增**[!UICONTROL Bundle Product]**透過 [!DNL Page Builder] 新增至區塊會導致錯誤。
feature: Page Builder, Page Content
role: Admin, Developer
exl-id: bb56c0c2-e094-4173-8260-da154df79748
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-63574：透過[!DNL Page Builder]新增[!UICONTROL Bundle Product]清單至區塊導致錯誤

ACSD-63574修補程式修正透過[!DNL Page Builder]將具有`Checkbox`或`Multi Select`選項的&#x200B;**[!UICONTROL Bundle Product]**&#x200B;新增至區塊導致錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59時，即可使用此修補程式。 修補程式ID為ACSD-63574。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.4-p10

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用[!DNL Page Builder]將&#x200B;**[!UICONTROL Bundle Product]**&#x200B;新增至區塊時，產品Widget預覽會中斷，並顯示錯誤訊息&#x200B;*很抱歉，產生此內容時發生錯誤*。 當套件組合產品包含`Checkbox`或`Multi Select`選項型別，且`indexer dimension mode`設定為`website_and_customer_group`時，會發生此問題。 例外狀況記錄會顯示下列錯誤：

    ``
    report.CRITICAL： PDOException： SQLSTATE[42S02]：找不到基底資料表或檢視： 1146資料表`db_name.catalog_product_index_price_cg0_ws0`在/home/vendor/magento/framework/DB/Statement/Pdo/Mysql.php：90
    ``
中不存在
<u>要再現的步驟</u>：

1. 前往&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**。
1. 在左側面板中，展開&#x200B;**[!UICONTROL Catalog]**&#x200B;並從下列選項中選取&#x200B;**[!UICONTROL Catalog]**。
1. 向下捲動至&#x200B;**[!UICONTROL Price]**&#x200B;區段，並將&#x200B;**[!UICONTROL Catalog Price Scope]**&#x200B;設為&#x200B;**[!UICONTROL Global]**。
1. 使用以下命令將`Indexer dimension mode`設為`website_and_customer_group`：

   `bin/magento indexer:set-dimensions-mode catalog_product_price website_and_customer_group`

1. 使用套件組合選項型別`Checkbox`或`Multi Select`建立&#x200B;**[!UICONTROL Bundle Product]**，並將產品指派至類別。
1. 前往&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Blocks]** > **[!UICONTROL Edit Content with Page Builder]**。
1. 選取已建立產品指派到的類別，並嘗試&#x200B;**[!UICONTROL Save]**。

<u>預期結果</u>：

產品已新增且沒有錯誤。

<u>實際結果</u>：

當&#x200B;**[!UICONTROL Bundle Product]**&#x200B;選項型別為`Checkbox`或`Multi Select`，且`indexer dimension mode`設定為`website_and_customer_group`時，無法透過[!DNL Page Builder]新增產品。 它擲回錯誤： *很抱歉，產生此內容時發生錯誤*。


## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
