---
title: 「ACSD-56886：可設定的產品在子產品停用時無庫存」
description: 套用ACSD-56886修補程式來修正Adobe Commerce問題，此問題導致可設定產品在產品停用時失去庫存子項。
feature: Products
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-56886：當子產品停用時，可設定的產品會無庫存

ACSD-56886修補程式修正了子產品停用時，可設定產品無存貨的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.45時，即可使用此修補程式。 修補程式ID為ACSD-56886。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當子項產品停用時，可設定的產品會變成無庫存。

<u>要再現的步驟</u>：

1. 以管理員身分登入。
1. 在&#x200B;**[!UICONTROL Update By Schedule]**&#x200B;模式中設定所有索引子。
1. 建立下列可設定的產品：

   * 名稱= *可設定的測試1*
   * 屬性= *色彩*
   * 值= *red*&#x200B;和&#x200B;*black*
   * **紅色**&#x200B;子產品的價格= *$100*；
   * 「黑色」子產品的價格= *$200*。

1. 為可設定產品建立以下排程更新：

   * 開始日期= *3*&#x200B;分鐘後。
   * 結束日期= *5*&#x200B;分鐘後。
   * 產品名稱= *測試可設定1已編輯*。
   * 停用&#x200B;**可設定**&#x200B;區段中的&#x200B;**red**&#x200B;子產品。

1. 等待開始日期。
1. 在店面開啟可設定的產品詳細資訊。

<u>預期結果</u>：

可設定的產品會顯示為&#x200B;**庫存中的**，並具有&#x200B;**低至200**&#x200B;的標籤。

<u>實際結果</u>：

可設定的產品會顯示為&#x200B;**缺貨**。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
