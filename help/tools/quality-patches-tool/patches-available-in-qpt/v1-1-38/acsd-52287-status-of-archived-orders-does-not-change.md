---
title: ACSD-52287：已封存訂單的狀態不會變更
description: 套用ACSD-52287修補程式，以修正Adobe Commerce的問題，即已封存訂單在提交銷退折讓單後，其狀態不會在網格上從*completed*變更為*closed*。
feature: Orders, Checkout
role: Admin, Developer
exl-id: 012f49ba-fdc1-4e1e-87fe-7b9c661f231b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# ACSD-52287：已封存訂單的狀態不會變更

ACSD-52287修補程式修正了在提交銷退折讓單後，已封存訂單的狀態未在網格上從&#x200B;*已完成*&#x200B;變更為&#x200B;*已關閉*&#x200B;的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.38時，即可使用此修補程式。 修補程式ID為ACSD-52287。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

提交銷退折讓單後，已封存訂單的狀態不會在網格上從&#x200B;*已完成*&#x200B;變更為&#x200B;*已關閉*。

<u>要再現的步驟</u>：

1. 設定&#x200B;*[!UICONTROL Asynchronous Indexing]*。
   * 在管理員側邊欄上，前往&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**。
   * 在左側面板中，展開&#x200B;**[!UICONTROL Advanced]**&#x200B;區段並在下方選擇&#x200B;**[!UICONTROL Developer]**。
   * 展開&#x200B;**[!UICONTROL Grid Settings]**&#x200B;區段。
   * 將&#x200B;*[!UICONTROL Asynchronous indexing]*&#x200B;設為&#x200B;*是*。
   * 按一下&#x200B;**[!UICONTROL Save Config]**。
1. 設定&#x200B;*[!UICONTROL Order Archive]*。
   * 在管理員側邊欄上，前往&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**。
   * 在左側面板中，展開&#x200B;**[!UICONTROL Sales]**&#x200B;區段並在下方選擇&#x200B;**[!UICONTROL Sales]**。
   * 展開&#x200B;**[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]**&#x200B;區段。
   * 將&#x200B;*[!UICONTROL Enable Archiving]*&#x200B;設為&#x200B;*是* （保留其餘組態為預設值）。
   * 按一下&#x200B;**[!UICONTROL Save Config]**。
1. 在前端下訂單。
1. 執行[!DNL cron]以便出現在&#x200B;*[!UICONTROL Admin Order Grid]*&#x200B;中。
1. 開立商業發票並送出訂單，以將訂單狀態更新為&#x200B;*完成*。
1. 執行[!DNL cron]以使用最新的訂單狀態更新&#x200B;*[!UICONTROL Sales Order Grid]*。
1. 封存訂單。
1. 移至&#x200B;*[!UICONTROL Archived order grid]*。
1. 開啟已封存的訂單，並藉由建立[!UICONTROL Credit Memo]以使[!UICONTROL Order status]： *已關閉*&#x200B;將訂單退款。
1. 執行[!DNL cron]幾次。
1. 檢查&#x200B;*[!UICONTROL Archived order grid]*&#x200B;的新訂單狀態。

<u>預期結果</u>：

訂單顯示為&#x200B;*已關閉*。

<u>實際結果</u>：

訂單顯示為&#x200B;*完成*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
