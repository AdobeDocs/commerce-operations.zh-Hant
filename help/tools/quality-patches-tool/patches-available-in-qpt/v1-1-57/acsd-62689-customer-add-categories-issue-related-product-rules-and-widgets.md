---
title: ACSD-62689：無法在深度4之後新增[!UICONTROL Related Product Rules]和Widget中的類別
description: 套用ACSD-62689修補程式來修正Adobe Commerce問題，其中客戶無法在深度四個巢狀之後新增[!UICONTROL Related Product Rules]和Widget中的類別。
feature: Categories
role: Admin, Developer
exl-id: 2506744a-01c8-462b-9a27-cd0bdb5664f9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-62689：無法在深度4之後新增&#x200B;*[!UICONTROL Related Product Rules]*&#x200B;和Widget中的類別

>[!NOTE]
>
>此修補程式已由[ACP2E-3689](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3689-issues-with-category-tree-display-reflect-anchor-non-anchor-relationships.md)取代。

ACSD-62689修補程式修正了客戶無法在深度4個巢狀結構之後新增&#x200B;*[!UICONTROL Related Product Rules]*&#x200B;和Widget類別的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57時，即可使用此修補程式。 修補程式ID為ACSD-62689。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

客戶無法在深度4個巢狀之後新增&#x200B;*[!UICONTROL Related Product Rules]*&#x200B;和Widget中的類別。

<u>要再現的步驟</u>：

1. 在預設根類別下建立兩個名為&#x200B;*[!UICONTROL Anchor]*&#x200B;和&#x200B;*[!UICONTROL Non-Anchor]*&#x200B;的類別。
   * 請確定&#x200B;*[!UICONTROL Non-Anchor]*&#x200B;類別的&#x200B;*[!UICONTROL Is Anchor]*&#x200B;旗標已停用。
1. 前往「**[!UICONTROL Content]** > **[!UICONTROL Widgets]**」並建立Widget。
1. 在&#x200B;*[!UICONTROL Layout Updates]*&#x200B;底下，選取&#x200B;*[!UICONTROL Display on]*&#x200B;欄位中的&#x200B;**[!UICONTROL Non-Anchor Categories]**。
1. 按一下&#x200B;**[!UICONTROL Specific Categories]**。
1. 按一下類別選取圖示。
1. 展開根類別。
1. 檢查類別。 兩者皆應停用，且不可選取。
1. 在&#x200B;*[!UICONTROL Layout Updates]*&#x200B;底下，選取&#x200B;*[!UICONTROL Display on]*&#x200B;欄位中的&#x200B;**[!UICONTROL Anchor Categories]**。 然後依照步驟5和6操作。
1. 檢查類別。 兩者皆應啟用且可供選取。

<u>預期結果</u>：

在步驟7中，只能選取&#x200B;*[!UICONTROL Non-Anchor]*&#x200B;類別。 在步驟9中，*[!UICONTROL Anchor]*&#x200B;類別應為可選取的。

<u>實際結果</u>：

在步驟7中，無法選取兩個類別。 在步驟9中，兩個類別都是可選取的。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。

