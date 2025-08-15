---
title: ACSD-60267：透過可設定的產品選項新增產品時，FPT套用不正確
description: 套用ACSD-60267修補程式以修正Adobe Commerce問題：當直接將簡單產品新增至購物車時，已修正產品稅(FPT)會正確套用，但透過可設定產品選項選取相同產品時失敗。
feature: Taxes
role: Admin, Developer
exl-id: 919b3b96-1995-4faf-aaf1-b5cbb20e46bf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-60267：透過可設定的產品選項新增產品時，FPT套用不正確

ACSD-60267修補程式修正將簡單產品直接新增到購物車時，固定產品稅(FPT)正確套用的問題，但在透過可設定產品選項選取相同產品時失敗。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.54時，即可使用此修補程式。 修補程式ID為ACSD-60267。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當具有FPT的簡單產品加入購物車時，Fixed Product Tax (FPT)可正常運作，但是當透過可設定的產品選擇加入產品時，FPT則無法新增。

<u>要再現的步驟</u>：

1. 導覽至&#x200B;*[!UICONTROL Enable FPT]*&#x200B;管理員&#x200B;*>* > *>* > **[!UICONTROL Configuration]**，將&#x200B;**[!UICONTROL Sales]**&#x200B;設為&#x200B;**[!UICONTROL Tax]**&#x200B;是&#x200B;**[!UICONTROL Fixed Product Taxes]**。
1. 建立FPT屬性並將其指派給&#x200B;*[!UICONTROL Attribute Set]*。
1. 開啟&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**。
1. 針對&#x200B;*[!UICONTROL Default Label]*，輸入識別屬性的標籤。
1. 將&#x200B;*[!UICONTROL Catalog Input for Store Owner]*&#x200B;設為&#x200B;*[!UICONTROL Fixed Product Tax]*。
1. 建立新的稅捐和區域，並將其指派給新的&#x200B;*[!UICONTROL Tax Rule]*。
1. 使用兩個簡單產品建立可設定的產品。
1. 現在將兩個不同的FPT值指派給這些簡單產品。
1. 重新編制索引，並檢查店面的價格。
1. 將產品新增到購物車並檢查小計。

<u>預期結果</u>：

* *[!UICONTROL Catalog]*&#x200B;頁面顯示包含FPT的價格。
* 購物車中的小計包括FPT。

<u>實際結果</u>：

* *[!UICONTROL Catalog]*&#x200B;頁面未顯示包含FPT值的價格。
* 小計和摘要無效。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
