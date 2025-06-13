---
title: ACSD-52786：目錄規則*[!UICONTROL SKU is]*適用於所有以SKU開頭的產品
description: 套用ACSD-52786修補程式以修正目錄規則條件*[!UICONTROL SKU is]*適用於從指定SKU開始的所有產品的Adobe Commerce問題。
feature: Price Rules
role: Admin
exl-id: 668d5f16-18a9-4054-aa6e-1fb8fa211373
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-52786：目錄規則&quot;*[!UICONTROL SKU is]*&quot;適用於所有以SKU開頭的產品

ACSD-52786修補程式修正了目錄規則條件&#x200B;*[!UICONTROL SKU is]*&#x200B;適用於從指定SKU開始的所有產品的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.35時，即可使用此修補程式。 修補程式ID為ACSD-52786。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

目錄規則條件&#x200B;*[!UICONTROL SKU is]*&#x200B;適用於所有以指定SKU開頭的產品。

<u>要再現的步驟</u>：

1. 建立兩個產品，一個使用SKU「24」，另一個使用SKU「24-MB01」。
1. 導覽至&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**。
1. 套用下列條件：
   * *[!UICONTROL If **&#x200B;所有&#x200B;**&#x200B;條件皆為 **&#x200B; TRUE &#x200B;**]*： *[!UICONTROL SKU is 24]*
1. 設定動作中的任何折扣金額。
1. 按一下&#x200B;**[!UICONTROL Save and Apply]**。
1. 排清快取。
1. 前往店面，檢視24-MB01的價格。

<u>預期結果</u>：

目錄規則僅套用至SKU等於24的單一產品。

<u>實際結果</u>：

目錄規則條件&#x200B;*[!UICONTROL SKU is]*&#x200B;適用於所有以指定SKU開頭的產品。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
