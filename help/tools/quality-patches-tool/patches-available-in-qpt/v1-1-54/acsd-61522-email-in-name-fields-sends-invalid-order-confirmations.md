---
title: ACSD-61522： *名字和姓氏*欄位中的電子郵件地址會傳送無效的訂單確認
description: 套用ACSD-61522修補程式以修正Adobe Commerce問題，該問題導致可能在來賓客戶的*[!UICONTROL First Name]*和*[!UICONTROL Last Name]*欄位中輸入電子郵件地址，從而導致傳送的訂單確認電子郵件無效。
feature: Checkout, Customers
role: Admin, Developer
exl-id: e1ed7a57-4054-44db-bc17-9b9056096fce
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-61522： *名字和姓氏*&#x200B;欄位中的電子郵件地址會傳送無效的訂單確認

ACSD-61522修補程式修正了來賓客戶的&#x200B;*[!UICONTROL First Name]*&#x200B;和&#x200B;*[!UICONTROL Last Name]*&#x200B;欄位中可能輸入電子郵件地址的問題，導致傳送的訂單確認電子郵件無效。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54時，即可使用此修補程式。 修補程式ID為ACSD-61522。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p9

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

系統允許在客體客戶的&#x200B;*[!UICONTROL First Name]*&#x200B;和&#x200B;*[!UICONTROL Last Name]*&#x200B;欄位中輸入電子郵件地址，導致傳送無效的訂單確認電子郵件。

<u>要再現的步驟</u>：

1. 以訪客客戶身分將任何產品新增到購物車。
1. 移至&#x200B;**[!UICONTROL Checkout]**。
1. 在&#x200B;*[!UICONTROL Email Address]*&#x200B;欄位中填入&#x200B;*test1@example.com*。
1. 在&#x200B;*[!UICONTROL First Name]*&#x200B;欄位中填入&#x200B;*<test2@example.com>*。
1. 以&#x200B;*<test3@example.com>*&#x200B;填滿&#x200B;*[!UICONTROL Last Name]*。
1. 填寫其他必填欄位。
1. 下訂單。

<u>預期結果</u>：

無法在&#x200B;*[!UICONTROL First Name]*&#x200B;和&#x200B;*[!UICONTROL Last Name]*&#x200B;欄位中使用電子郵件地址。

<u>實際結果</u>：

1. 已下訂單。
1. *[!UICONTROL First Name]*&#x200B;和&#x200B;*[!UICONTROL Last Name]*&#x200B;欄位已儲存為已輸入的內容。
1. 訂單確認電子郵件會傳送到所有三封電子郵件。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
