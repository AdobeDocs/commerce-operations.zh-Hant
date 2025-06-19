---
title: ACSD-64178： [!UICONTROL Edit Attribute Set]頁面載入速度緩慢，包含數千個產品屬性
description: 套用ACSD-64178修補程式以修正Adobe Commerce問題，若有數千個產品屬性，[!UICONTROL Edit Attribute Set]頁面載入速度緩慢。
feature: Catalog Management
role: Admin, Developer
exl-id: 959d825d-1b7b-49f0-b49f-64e149106e91
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# ACSD-64178： [!UICONTROL Edit Attribute Set]頁面載入速度緩慢，包含數千個產品屬性

ACSD-64178修補程式修正&#x200B;**[!UICONTROL Edit Attribute Set]**&#x200B;頁面載入緩慢（若有數千個產品屬性）的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61時，即可使用此修補程式。 修補程式ID為ACSD-64178。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果有數千個產品屬性，**[!UICONTROL Edit Attribute Set]**&#x200B;頁面載入速度會很慢。

<u>要再現的步驟</u>：

1. 至少建立4200個未指派給任何屬性集的屬性。
1. 在管理員側邊欄上，前往&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Attribute Set]**。 按一下任何屬性集以進行編輯。

<u>預期結果</u>：

頁面會在合理的時間內載入。

<u>實際結果</u>：

載入頁面需要幾分鐘的時間。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
