---
title: ACSD-55566： [!UICONTROL mergeCart]突變失敗，在 [!DNL GraphQL] 回應中發生內部伺服器錯誤
description: 套用ACSD-55566修補程式，以修正合併來源與目的地購物車（具有相同的組合專案）時，「mergeCart」變異失敗且 [!DNL GraphQL] 回應中發生內部伺服器錯誤的Adobe Commerce問題。
feature: GraphQL, Shopping Cart
role: Admin, Developer
exl-id: 84c6fbb9-73b3-4197-aff3-49743f0ebb2c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-55566： `mergeCart`突變失敗，在[!DNL GraphQL]回應中發生內部伺服器錯誤

ACSD-55566修補程式修正了`mergeCart`突變失敗且[!DNL GraphQL]回應中發生內部伺服器錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48時，即可使用此修補程式。 修補程式ID為ACSD-55566。 請注意，此問題已排程在Adobe Commerce 2.5.0中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

合併具有相同組合專案的來源和目的地購物車時，`mergeCart`變異失敗，且在[!DNL GraphQL]回應中發生內部伺服器錯誤。

<u>要再現的步驟</u>：

1. 建立自訂來源與自訂庫存。
1. 將建立的庫存指派給主要網站。
1. 建立簡單產品並將建立的來源指派給它（數量=2）。
1. 建立一個包含一個選項和一個子產品的套件產品（在步驟3中建立的產品）。
1. 透過[!DNL GraphQL]建立訪客購物車。
1. 新增已選取兩個選項的套件組合產品。
1. 儲存&#x200B;*cartID*。
1. 建立客戶並產生客戶代號。
1. 建立客戶購物車。
1. 將具有相同設定的相同套件產品新增至購物車。
1. 嘗試將訪客購物車與客戶購物車合併。

<u>預期結果</u>：

客戶購物車包含來自兩個購物車的產品。

<u>實際結果</u>：

您收到內部錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
