---
title: ACSD-48318： 'system.log'中的環境模擬巢狀錯誤
description: 套用ACSD-48318修補程式以修正Adobe Commerce中每次傳送發票電子郵件時出現錯誤訊息*main.ERROR：不允許環境模擬巢狀結構*的問題。
feature: System, Orders
role: Admin, Developer
exl-id: 24af18de-80dd-4e0a-bdf9-5b9c075fc608
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# ACSD-48318： `system.log`中的環境模擬巢狀錯誤

ACSD-48318修補程式修正了每次傳送發票電子郵件時，*中都會出現錯誤訊息:Environmentmain.ERROR*&#x200B;模擬巢狀不允許`system.log`的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53時，即可使用此修補程式。 修補程式ID為ACSD-48318。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

每次傳送發票電子郵件時，*中都會出現錯誤訊息*&#x200B;不允許環境模擬巢狀`system.log`。

<u>要再現的步驟</u>：

1. 下單並產生商業發票。
1. 從Admin開啟發票，然後按一下&#x200B;**[!UICONTROL Send Email]**。
1. 按一下&#x200B;*，對*&#x200B;銷退折讓單&#x200B;*和*&#x200B;出貨&#x200B;**[!UICONTROL Send Email]**&#x200B;執行相同的步驟。

<u>預期結果</u>：

`system.log`中沒有錯誤。

<u>實際結果</u>：

`system.log`被&#x200B;*main淹沒。錯誤：不允許環境模擬巢狀化*&#x200B;錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

[[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
