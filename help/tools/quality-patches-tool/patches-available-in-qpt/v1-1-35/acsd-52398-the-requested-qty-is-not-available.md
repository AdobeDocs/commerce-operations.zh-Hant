---
title: 'ACSD-52398：嘗試更新套件產品的數量時，無法使用要求的數量'
description: 套用ACSD-52398修補程式以修正嘗試更新店面購物車中捆綁產品的數量時，無法取得請求數量的Adobe Commerce問題。
feature: Shopping Cart, Quotes, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-52398：嘗試更新套件產品的數量時，無法使用要求的數量

ACSD-52398修補程式修正嘗試更新店面購物車中捆綁產品的數量時，無法取得請求數量的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.35時，即可使用此修補程式。 修補程式ID為ACSD-52398。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

嘗試更新店面購物車中捆綁產品的數量時，無法使用請求的數量。

<u>要再現的步驟</u>：

1. 建立數量為&#x200B;*1*&#x200B;和&#x200B;*10*&#x200B;的兩個簡單產品。
1. 使用簡單產品建立套件式產品。
1. 將隨附產品新增到購物車。
1. 編輯產品，並嘗試針對可用&#x200B;*10*&#x200B;個專案的選項，將數量更新為&#x200B;*3*。

<u>預期結果</u>：

沒有錯誤。 數量已成功更新，因為此選項有&#x200B;*10*&#x200B;個庫存專案。

<u>實際結果</u>：

擲回下列錯誤： *要求的數量無法使用*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。