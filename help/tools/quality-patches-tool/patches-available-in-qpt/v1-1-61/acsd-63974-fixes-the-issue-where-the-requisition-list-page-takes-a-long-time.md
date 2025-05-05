---
title: ACSD-63974：修正分頁導致[!UICONTROL Requisition List]載入時間變慢的問題
description: 套用ACSD-63974修補程式以修正[!UICONTROL Requisition List]頁面有太多專案時需花很長時間載入的問題。
feature: B2B
role: Admin, Developer
source-git-commit: e5f8112b870e3550b4f3a9113be48428a54d454a
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# ACSD-63974：修正分頁導致[!UICONTROL Requisition List]載入時間變慢的問題

ACSD-63974修補程式修正專案過多時&#x200B;**[!UICONTROL Requisition List]**&#x200B;頁面載入時間過長的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61時，即可使用此修補程式。 修補程式ID為ACSD-63974。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當有許多專案(2000+)時，**[!UICONTROL Requisition List]**&#x200B;頁面需要很長時間才能載入。 這是由於缺少分頁，導致所有專案同時載入。

<u>要再現的步驟</u>：

1. 前往「**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > *[!UICONTROL General]* > **[!UICONTROL B2B features]**」。
1. 將&#x200B;**[!UICONTROL Enable Requisition List]**&#x200B;設為&#x200B;*是*。
1. 編輯`setup/performance-toolkit/profiles/ce/small.xml`中的`simple_products`節點，產生2000+個產品。
1. 執行命令：

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. 建立客戶並登入。
1. 將所有產品新增至「**[!UICONTROL Requisition List]**」。
1. 檢視店面上的&#x200B;**[!UICONTROL Requisition List]**。


<u>預期結果</u>：

頁面應在合理的時間內載入。


<u>實際結果</u>：

頁面載入時間會隨著專案數量而增加，因為缺少分頁會一次載入所有專案。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的升級和修補程式>套用修補程式。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
