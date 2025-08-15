---
title: ACSD-64684：儲存值超過999的禮品卡時發生驗證錯誤，因為一千位以逗號分隔(1,000)
description: 套用ACSD-64684修補程式以修正Adobe Commerce問題，在儲存值超過999的禮品卡時，由於逗號為「1,000」(1,000)而導致驗證錯誤。
feature: Catalog Management
role: Admin, Developer
exl-id: 327c5d28-b52c-4da9-a905-8a3deb755241
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-64684：儲存值超過999的禮品卡時發生驗證錯誤，因為一千位以逗號分隔(1,000)

ACSD-64684修補程式修正了儲存禮品卡時，由於逗號「1,000」(1,000)而導致值超過999時發生驗證錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61時，即可使用此修補程式。 修補程式ID為ACSD-64684。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

編輯和儲存值大於999的禮品卡時，因為數字中有逗號（千位分隔符號），例如「一千」(1,000)，所以發生驗證錯誤。

<u>要再現的步驟</u>：

1. 建立禮卡產品。
   1. 輸入1,000作為[!UICONTROL Amount]。
   1. 按一下&#x200B;**[!UICONTROL Save]**。

<u>預期結果</u>：

* 已儲存金額為1,000的新禮品卡。

<u>實際結果</u>：

* 當禮卡金額大於999時發生驗證錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
