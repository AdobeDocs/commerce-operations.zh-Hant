---
title: ACSD-52929：重新索引預設來源專案的備援請求
description: 套用ACSD-52929修補程式來修正Adobe Commerce問題，其中當庫存索引器設定為非同步模式時，有重新索引預設來源專案的多餘請求。
feature: Configuration, Inventory
role: Admin, Developer
exl-id: 904aed0e-a6cd-4a0f-949d-bb32fcd77356
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-52929：重新索引預設來源專案的備援請求

ACSD-52929修補程式修正了在非同步模式中設定清查索引器時，重新索引預設來源專案的請求冗餘的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.38時，即可使用此修補程式。 修補程式ID為ACSD-52929。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當庫存索引器設定為非同步模式時，重新索引預設來源專案的要求有備援。

<u>要再現的步驟</u>：

1. 設定[!DNL RabbitMQ]。
1. 移至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]**&#x200B;並設定&#x200B;**[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]**，以啟用非同步重新索引策略。
1. 建立自訂詳細目錄來源。
1. 登入[!DNL RabbitMQ]儀表板，並移至[佇列]索引標籤。
1. 檢查`inventory.indexer.sourceItem`佇列並確保它沒有訊息。
1. 從後端開啟簡單產品，並將&#x200B;*[!UICONTROL stock only]*&#x200B;新增至自訂來源並儲存產品。
1. 載入[!DNL RabbitMQ]儀表板中的`inventory.indexer.sourceItem`佇列，然後檢查訊息。

<u>預期結果</u>：

自訂來源的佇列中只有一個訊息。

<u>實際結果</u>：

佇列中會顯示兩個訊息：一個代表預設來源，另一個代表自訂來源。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
