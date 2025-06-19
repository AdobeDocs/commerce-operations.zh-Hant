---
title: ACSD-52202：當非預設庫存設定為0數量時，預設庫存可銷售數量錯誤地變更為0
description: 套用ACSD-52202修補程式來修正Adobe Commerce問題，該問題導致當訂單中的非預設庫存設定為0數量時，預設庫存可銷售數量錯誤地變為0。
feature: Inventory, Products
role: Admin
exl-id: 2ba5cc3b-9774-49f6-948f-371ab3c0c9df
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-52202：當訂單中的非預設存貨設定為0數量時，預設存貨可銷售數量會錯誤地變更為0

ACSD-52202修補程式修正了當非預設庫存設定為訂單中的0數量時，預設庫存可銷售數量（數量）錯誤地變為0的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.35時，即可使用此修補程式。 修補程式ID為ACSD-52202。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當訂單中的非預設存貨設定為0數量時，預設存貨可銷售數量會錯誤地變更為0。

<u>要再現的步驟</u>：

1. 登入[!DNL Admin]。
1. 建立&#x200B;**網站2**。
1. 建立自訂&#x200B;**來源2**。
1. 建立自訂&#x200B;**stock2**。
1. 將&#x200B;**來源2**&#x200B;和&#x200B;**庫存2**&#x200B;指派給&#x200B;**網站1**，並將預設來源和庫存指派給預設網站。
1. 建立簡單產品並指派預設來源的&#x200B;**qty** = *10*，以及&#x200B;**source2**&#x200B;來源的&#x200B;**qty** = *1*。
1. 為&#x200B;**網站2**&#x200B;下含&#x200B;**數量** = *1*&#x200B;的訂單。
1. 建立商業發票與出貨。
1. 檢查簡單產品&#x200B;**可銷售數量**。

<u>預期結果</u>：

**來源2**&#x200B;的&#x200B;**可銷售數量** = *10*。

<u>實際結果</u>：

兩個來源的&#x200B;**可銷售數量** = *0*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
