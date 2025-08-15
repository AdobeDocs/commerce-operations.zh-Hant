---
title: ACSD-66301：在Commerce管理員中將產品從訂單移至購物車會導致數量不符
description: 套用ACSD-66301修補程式以修正Adobe Commerce問題，其中從管理員面板建立訂單時，客戶購物車中的產品新增至訂單後並未移除。
feature: Orders, Products
role: Admin, Developer
type: Troubleshooting
exl-id: 61e0e491-b2dc-4ae0-807e-2ae80d17f9c2
source-git-commit: 1e56c38713344b117ca3882861ced35e602b3239
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-66301：在Commerce管理員中將產品從訂單移回購物車導致數量不符

ACSD-66301修補程式修正了在「管理員」中將產品從訂單移回購物車導致數量不符的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67時，即可使用此修補程式。 修補程式ID為ACSD-66301。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p10、2.4.7-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6-p9 - 2.4.6-p11， 2.4.7-p4 - 2.4.7-p6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在Commerce管理員中，將產品從訂單移回購物車會導致數量不符。

<u>要再現的步驟</u>：

1. 透過店面建立使用者。
2. 新增產品至購物車，其數量= *5*。
3. 前往「管理員」面板，並開啟新增產品的使用者帳戶。
4. 按一下&#x200B;**[!UICONTROL Create Order]**。
5. 在左側面板中，您可以檢視客戶活動，包括新增的產品和數量。
6. 將產品新增至訂單。
7. 更新主要訂單區段中的數量= *4*。
8. 按一下&#x200B;**[!UICONTROL Update Items and Quantities]**&#x200B;按鈕。
9. 將選取的專案從訂單移回客戶的購物車。

<u>預期結果</u>：

產品已新增至購物車，新數量= *4*。

<u>實際結果</u>：

產品已新增至購物車，舊數量= *5*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
