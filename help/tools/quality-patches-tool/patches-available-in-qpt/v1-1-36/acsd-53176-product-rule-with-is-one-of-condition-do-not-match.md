---
title: ACSD-53176：具有「為其中之一」條件的產品規則不相符
description: 套用ACSD-53176修補程式以修正Adobe Commerce問題，該問題導致相關產品規則「為其中一項」條件無法正確用於「相符產品」。
feature: Marketing Tools
role: Admin
exl-id: 8260c6ac-3ca2-4361-9e36-a8a58468fa95
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-53176：具有`is one of`條件的產品規則不相符

ACSD-53176修補程式修正了&#x200B;**產品符合**&#x200B;時，相關產品規則`is one of`條件無法正確運作的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.36時，即可使用此修補程式。 修補程式ID為ACSD-53176。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

相關產品規則`is one of`條件無法正確運作，無法讓&#x200B;**產品符合**。

<u>要再現的步驟</u>：

1. 建立3-4個產品。
1. 建立新的相關產品規則。

   設定規則以符合兩個或多個產品：
   * `SKU is one of "S1,S2".`

   設定規則以顯示兩個或多個專案：
   * `Product SKU is one of constant value "S2,S3".`

1. 開啟店面上的S1產品。

<u>預期結果</u>：

相關產品「S2」和「S3」會顯示在產品頁面「S1」和「S2」上。

<u>實際結果</u>：

相關產品不會顯示在產品頁面上。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
