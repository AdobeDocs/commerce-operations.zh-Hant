---
title: ACSD-61799：套用至報價的多重固定折扣購物車規則的折扣總計計算不正確
description: 套用ACSD-61799修補程式以修正當對報價套用多個具有固定折扣的購物車規則時，總折扣無法正確計算的Adobe Commerce問題。
feature: Price Rules
role: Admin, Developer
exl-id: a87ec1cd-f141-43b9-bde1-eca354c12d4e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-61799：套用至報價的多重固定折扣購物車規則的折扣總計計算不正確

ACSD-61799修補程式可解決/修正當對報價套用多個具有固定折扣的購物車規則時，總折扣計算錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54時，即可使用此修補程式。 修補程式ID為ACSD-61799。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

將具有&#x200B;*[!UICONTROL Fixed amount discount for the whole cart]*&#x200B;的多個購物車規則套用至購物車時，未正確計算總折扣。

<u>要再現的步驟</u>：

1. 建立價格為$1000的四項產品。
1. 建立三個購物車價格規則，且不含可對整個購物車提供$100折扣的任何條件。
1. 建立另一個購物車價格規則，給予整個購物車$100的折扣，並附上條件，以防止套用規則。
1. 停用規則。
1. 新增三種產品至購物車，並觀察購物車中的折扣。
1. 新增其他產品至購物車，並觀察購物車中的折扣。
1. 啟用停用的購物車價格規則。
1. 更新購物車頁面，並觀察購物車中的折扣。

<u>預期結果</u>：

1. 新增其他產品至購物車不會變更折扣金額。
1. 以不適用的條件啟用購物車價格規則不會變更折扣金額。

<u>實際結果</u>：

1. 新增其他產品至購物車會變更折扣金額。
1. 以不適用的條件啟用購物車價格規則會變更折扣金額。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
