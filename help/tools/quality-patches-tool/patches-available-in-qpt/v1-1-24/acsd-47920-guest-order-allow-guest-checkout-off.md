---
title: 'ACSD-47920：即使[!UICONTROL Allow Guest Checkout]已關閉，訪客使用者仍可透過REST API下訂單'
description: 套用ACSD-47920修補程式以修正透過REST API以訪客使用者身分下訂單的Adobe Commerce問題，即使[!UICONTROL Allow Guest Checkout]已關閉亦然。
feature: REST, Checkout, Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-47920：即使&#x200B;**[!UICONTROL Allow Guest Checkout]**&#x200B;已關閉，訪客使用者仍可透過REST API下訂單

ACSD-47920修補程式修正了即使在&#x200B;**[!UICONTROL Allow Guest Checkout]**&#x200B;關閉時，仍可透過REST API以訪客使用者身分下達訂單的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24時，即可使用此修補程式。 修補程式ID為ACSD-47920。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

即使&#x200B;**[!UICONTROL Allow Guest Checkout]**&#x200B;已關閉，也可以透過Rest API以訪客使用者身分下訂單。

<u>要再現的步驟</u>：

1. 前往Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** >並將&#x200B;**[!UICONTROL Allow Guest Checkout]**&#x200B;設定為&#x200B;_否_。
1. 使用REST API將產品新增到購物車及下訂單。

<u>預期結果</u>：

如果&#x200B;**[!UICONTROL Allow Guest Checkout]**&#x200B;設為&#x200B;_否_，則訪客簽出API傳回錯誤&#x200B;*[!UICONTROL Sorry, guest checkout is not available]*。

<u>實際結果</u>：

即使&#x200B;**[!UICONTROL Allow Guest Checkout]**&#x200B;設定為&#x200B;_否_，訪客簽出API仍允許下訂單。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
