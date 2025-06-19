---
title: ACSD-63182：在重複套件產品後儲存產品時發生錯誤
description: 套用ACSD-63182修補程式以修正Adobe Commerce問題，此問題發生在啟用MSI的套件產品重複後儲存產品時發生錯誤。
feature: Inventory, Catalog Management
Role: Admin, Developer
exl-id: 2c664c89-e00e-40a8-9127-8c3f36c5bab9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-63182：在重複套件產品後儲存產品時發生錯誤

ACSD-63182修補程式修正了套裝產品複製後，無法儲存作為套裝選項的簡單產品的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58時，即可使用此修補程式。 修補程式ID為ACSD-63182。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

複製套件組合產品後，儲存作為套件組合選項的簡單產品時發生錯誤。

<u>要再現的步驟</u>：

1. 建立新的MSI來源和庫存。
1. 建立兩個簡單的產品： **p1**&#x200B;和&#x200B;**p2**。
1. 建立搭售產品&#x200B;**b1**，並將&#x200B;**p1**&#x200B;和&#x200B;**p2**&#x200B;作為搭售選項。
1. 編輯&#x200B;**組合產品b1**&#x200B;並按一下***[!UICONTROL Save and Duplicate]***。
1. 編輯&#x200B;**簡單產品p1**&#x200B;並按一下&#x200B;**[!UICONTROL Save]**。

<u>預期結果</u>：

產品已儲存且未發生錯誤。

<u>實際結果</u>：

會顯示下列錯誤：
*例外狀況：具有相同ID &#39;XXX&#39;的專案(Magento\Catalog\Model\Product\Interceptor)已經存在。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
