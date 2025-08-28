---
title: ACP2E-3767：儲存套件組合產品後，最後一個套件組合選項會重新出現
description: 套用ACP2E-3767修補程式以修正無法移除套件組合產品中最後一個套件組合選項的Adobe Commerce問題。
feature: Products, Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: f39442925d9cc82087af9e84d91137a0fcd0ec14
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# ACP2E-3767：儲存套件組合產品後，最後一個套件組合選項會重新出現

ACP2E-3767修補程式修正儲存套件產品後最後一個套件組合選項會重新出現的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69時，即可使用此修補程式。 修補程式ID為ACP2E-3767。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

無法移除套件組合產品中的最後一個套件組合選項。

<u>要再現的步驟</u>：

1. 前往&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]**。
1. 從下拉式清單中選取&#x200B;**[!UICONTROL Simple Product]**。
1. 輸入所需資料並儲存。
1. 前往&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]**。
1. 從下拉式清單中選取&#x200B;**[!UICONTROL Bundle Product]**。
1. 輸入必要的資料。
1. 在套件組合專案中，按一下&#x200B;**[!UICONTROL Add Option]**。
1. 新增標題至新選項，然後按一下&#x200B;**[!UICONTROL Add Products to Option]**。
1. 選取先前建立的簡單產品，然後選取&#x200B;**[!UICONTROL Add Selected Products]**。
1. 儲存套件組合產品。
1. 移除束選項並儲存。

<u>預期結果</u>：

1. 已成功移除組合選項。
1. 如果不允許移除，則會顯示訊息。

<u>實際結果</u>：

1. 束選項保持活動狀態。
1. 未顯示錯誤或通知。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
