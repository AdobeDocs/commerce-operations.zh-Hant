---
title: ACSD-62872：排程更新驗證不正確
description: 套用ACSD-62872修補程式，修正排程更新驗證錯誤且屬性驗證唯一的Adobe Commerce問題。
feature: Catalog Management, Admin Workspace
role: Admin, Developer
source-git-commit: f734dab2316237d60164a430eeabed17782b0ae6
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# ACSD-62872：排程更新驗證不正確

ACSD-62872修補程式修正唯一屬性驗證的問題，即排程的更新驗證不正確。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56時，即可使用此修補程式。 修補程式ID為ACSD-62872。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

排程的自訂屬性更新未正確驗證。

<u>要再現的步驟</u>：

1. 建立類別的自訂屬性。
1. 導覽至&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Categories]**。
1. 建立新類別。
1. 在相同類別中，移至&#x200B;**[!UICONTROL Scheduled Updates]**&#x200B;區段。
1. 設定此類別在未來任何時間的新更新。
1. 在開始排程更新之前，請嘗試編輯類別的已建立排程更新。

<u>預期結果</u>：

應該能夠更新排程的更新。

<u>實際結果</u>：

擲回錯誤： *「自訂屬性」屬性值不是唯一的。 設定唯一值，然後再試一次。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
