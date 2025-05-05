---
title: ACSD-60344：在使用[!UICONTROL Purchase Order]自動核準時復制訂單確認電子郵件
description: 套用ACSD-60344修補程式以修正使用[!UICONTROL Purchase Order]自動核準時傳送重複訂單確認電子郵件的Adobe Commerce問題。
feature: Purchase Orders
role: Admin, Developer
source-git-commit: afa03b31e4af0be1ebc0d12aabd4f9d8be17d1fe
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# ACSD-60344：在使用&#x200B;*[!UICONTROL Purchase Order]*&#x200B;自動核準時復制訂單確認電子郵件

ACSD-60344修補程式修正了使用&#x200B;*[!UICONTROL Purchase Order]*&#x200B;進行自動核準時傳送重複訂單確認電子郵件的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55時，即可使用此修補程式。 修補程式ID為ACSD-60344。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.6-p4

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用&#x200B;*[!UICONTROL Purchase Order]*&#x200B;自動核準時會傳送重複的訂單確認電子郵件。

<u>必要條件</u>

啟用B2B模組和&#x200B;*[!UICONTROL Purchase Order]*。

<u>要再現的步驟</u>：

1. 建立公司帳戶並為其啟用&#x200B;*[!UICONTROL Purchase Order]*。
1. 建立一般使用者帳戶，並將其以公司使用者的身分新增至公司帳戶。
1. 使用此帳戶下訂單。
1. 執行cron並檢查電子郵件。

<u>預期結果</u>：

每個訂單僅會收到一封訂單確認電子郵件。

<u>實際結果</u>：

收到兩封訂單確認電子郵件。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
