---
title: ACSD-62635：在 [!DNL GraphQL]中顯示的多重商店相關產品不正確
description: 套用ACSD-62635修補程式以修正Adobe Commerce問題，該問題導致多商店相關產品無法在 [!DNL GraphQL] 產品查詢中正確顯示。
feature: B2B
role: Admin, Developer
exl-id: 540cd37b-4dc5-42d1-a968-2989262effdd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-62635： [!DNL GraphQL]中無法正確顯示多商店相關產品

ACSD-62635修補程式修正多商店相關產品未在[!DNL GraphQL]產品查詢中正確顯示的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=zh-Hant) 1.1.57時，即可使用此修補程式。 修補程式ID為ACSD-62635。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

啟用B2B時，即使要求中使用商店檢視範圍，[!DNL GraphQL]要求也會傳回所有網站的所有相關產品。

<u>要再現的步驟</u>：

1. 建立兩個網站、商店和商店檢視。
1. 建立下列簡單產品：
   * 一個主要SKU為&#x200B;*product1*&#x200B;的已指派給所有網站
   * 一個僅指派給&#x200B;*網站1*
   * 僅指派給&#x200B;*網站2*&#x200B;的一個
   * 一個已指派給&#x200B;*網站1*&#x200B;和&#x200B;*網站2*
1. 新增與&#x200B;*product1*&#x200B;相關的所有產品。
1. 啟用[!UICONTROL B2B]和[!UICONTROL Shared Catalog]。
1. 將所有產品新增至預設的共用目錄。
1. 傳送[!DNL GraphQL]要求以擷取&#x200B;*product1*&#x200B;及其相關產品，標題中的商店代碼為&#x200B;*網站1*。

<u>預期結果</u>：

回應僅包含來自網站的相關產品，這些產品對應至要求標頭中傳送的商店代碼。

<u>實際結果</u>：

回應包含所有網站的所有相關產品，無論請求中指定的商店程式碼為何。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
