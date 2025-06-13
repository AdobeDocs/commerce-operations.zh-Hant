---
title: ACSD-53636： [!UICONTROL Product Listing]頁面上未顯示一般價格
description: 套用ACSD-53636修補程式，修正具有可設定產品之子項產品具有特殊價格的*[!UICONTROL Product Listing]*頁面上未顯示一般價格的Adobe Commerce問題。
feature: Catalog Management, Products
role: Admin, Developer
exl-id: e6d66ae4-2c21-466a-b03c-a1f486e7fa29
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-53636： *[!UICONTROL Product Listing]*&#x200B;頁面上未顯示一般價格

ACSD-53636修補程式針對具有可設定之子項產品的特殊價格，修正了&#x200B;*[!UICONTROL Product Listing]*&#x200B;頁面上未顯示一般價格的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43時，即可使用此修補程式。 修補程式ID為ACSD-53636。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.4-p6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

對於具有可設定之子項產品具有特殊價格的可設定產品，*[!UICONTROL Product Listing]*&#x200B;頁面上不會顯示一般價格。

<u>要再現的步驟</u>：

1. 登入管理員並移至&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Catalog]**，然後建立或開啟任何可設定的產品。
2. 開啟子產品，並為所有或其中一個子產品新增特殊價格，然後儲存產品。
3. 前往前端，並開啟可設定產品的&#x200B;**[!UICONTROL Product Detail]**&#x200B;頁面；在特殊價格子產品的色票上，您會看到&#x200B;*[!UICONTROL Regular price]*&#x200B;刪除線（預期）。
4. 移至前端，並開啟具有特殊價格之可設定產品的&#x200B;**[!UICONTROL Product Listing]**&#x200B;頁面；檢視可設定產品色票變更不會顯示一般價格，這與&#x200B;*[!UICONTROL Product Detail Page]*&#x200B;和其他簡單產品不同。

<u>預期結果</u>：

在&#x200B;*[!UICONTROL Product Listing]*&#x200B;頁面上，可設定的產品會顯示其子產品的正常價格。

<u>實際結果</u>：

在&#x200B;*[!UICONTROL Product Listing]*&#x200B;頁面上，可設定的產品未顯示其子產品的正常價格。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
