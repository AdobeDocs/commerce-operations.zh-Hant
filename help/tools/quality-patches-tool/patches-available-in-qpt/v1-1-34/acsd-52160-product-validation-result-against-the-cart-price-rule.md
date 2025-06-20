---
title: ACSD-52160：根據購物車價格規則的產品驗證結果
description: 套用ACSD-52160修補程式以修正Adobe Commerce問題，該問題導致根據規則條件*[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*未正確評估購物車價格規則的產品驗證結果。
exl-id: 8f8799c9-850a-4c8f-bde4-68df64e46c85
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-52160：未正確評估購物車價格規則的產品驗證結果

ACSD-52160修補程式修正未根據規則條件&#x200B;*[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*&#x200B;正確評估購物車價格規則之產品驗證結果的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34時，即可使用此修補程式。 修補程式ID為ACSD-52160。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

未根據規則條件&#x200B;*[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*&#x200B;正確評估購物車價格規則的產品驗證結果。

<u>要再現的步驟</u>：

1. 建立指派給兩個不同類別的兩個產品。
1. 建立&#x200B;**[!UICONTROL Cart Price Rule]**，其條件如下：

   * *[!UICONTROL FOUND]*&#x200B;引數中的&#x200B;**SKU 1**
   * *[!UICONTROL NOT FOUND]*&#x200B;引數中的&#x200B;**SKU 2**

1. 將兩個產品新增到購物車。
1. 套用優惠券代碼。

<u>預期結果</u>

不會套用優惠券代碼，因為購物車包含來自受限制類別的產品。

<u>實際結果</u>

將會套用優惠券代碼。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant>)。
