---
title: ACSD-60804：編輯與已刪除公司相關聯的客戶會導致錯誤
description: 套用ACSD-60804修補程式以修正Adobe Commerce問題，其中編輯與已刪除公司相關聯的客戶會導致錯誤*在null*上呼叫成員函式getSuperUserId()。
feature: Companies, Customers, B2B
role: Admin, Developer
exl-id: 09241160-f5ed-41f8-8bb6-2bb8ed5cccd5
source-git-commit: 9d39b1045099a71d23f25ad1ef4932f78b1f33f0
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-60804：編輯與已刪除公司相關聯的客戶會導致錯誤

ACSD-60804修補程式修正了編輯與已刪除公司關聯的客戶時，在null *上造成錯誤*&#x200B;呼叫成員函式getSuperUserId()的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53時，即可使用此修補程式。 修補程式ID為ACSD-60804。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.6-p2

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

編輯與已刪除公司關聯的客戶會導致錯誤&#x200B;*呼叫null*&#x200B;上的成員函式getSuperUserId()。

<u>必要條件：</u>：

安裝並啟用Adobe Commerce B2B模組。

<u>要再現的步驟</u>：

1. 前往&#x200B;**[!UICONTROL Settings]** > **[!UICONTROL B2B]** > **[!UICONTROL Enable Company]**。
1. 前往&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL Company]** > **[!UICONTROL Create New Company]**。
1. 登入執行個體的`mysql`。
1. 刪除`entity_id` = *1*&#x200B;的公司。
1. 前往&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL All Customers]**。
1. 編輯您建立公司時自動建立的客戶。

<u>預期結果</u>：

編輯客戶時未擲回例外狀況錯誤。

<u>實際結果</u>：

發生錯誤：如果沒有任何公司與客戶相關聯，則在null *上呼叫getSuperUserId()成員函式。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
