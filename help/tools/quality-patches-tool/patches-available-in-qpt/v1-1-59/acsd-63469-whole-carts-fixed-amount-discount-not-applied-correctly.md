---
title: ACSD-63469：固定金額購物車折扣未正確套用多個規則
description: 套用ACSD-63469修補程式以修正Adobe Commerce的問題，也就是套用多個規則時，無法正確套用整個購物車的固定金額折扣。
feature: Price Rules
role: Admin, Developer
exl-id: fb6dee57-281e-4165-8b70-7ff5949eb677
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-63469：固定金額購物車折扣未正確套用多個規則

ACSD-63469修補程式修正套用多個規則時，無法正確套用整個購物車的固定金額折扣的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59時，即可使用此修補程式。 修補程式ID為ACSD-63469。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果同時套用多個&#x200B;**[!UICONTROL Fixed amount discount for whole cart]**&#x200B;規則，且產品有折扣或特殊價格，則折扣值的計算不正確。

<u>要再現的步驟</u>：

1. 建立兩種價格分別為$850和$85的產品，並將它們的特殊價格分別設定為$765和$68。
1. 建立兩個&#x200B;**[!UICONTROL Cart Price Rules]**，如下所示：
   * 規則1
      * **[!UICONTROL Conditions]**：針對$850產品，將&#x200B;*數量*&#x200B;設定為&#x200B;*等於或大於2*
      * **[!UICONTROL Actions]**：套用&#x200B;**[!UICONTROL Fixed amount discount for whole cart]** / *$153*
   * 規則2
      * **[!UICONTROL Conditions]**：對於$85的產品，將&#x200B;*數量*&#x200B;設定為&#x200B;*等於或大於2*
      * **[!UICONTROL Actions]**：套用&#x200B;**[!UICONTROL Fixed amount discount for whole cart]** / *$14*
1. 將兩個產品新增至購物車，每個產品的數量為2。

<u>預期結果</u>：

購物車套用的折扣為$167。

<u>實際結果</u>：

購物車套用的折扣為$41。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 安裝修補程式後所需的其他步驟

（本節為選用；套用修補程式修正問題後，可能需要執行一些步驟。） 

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
