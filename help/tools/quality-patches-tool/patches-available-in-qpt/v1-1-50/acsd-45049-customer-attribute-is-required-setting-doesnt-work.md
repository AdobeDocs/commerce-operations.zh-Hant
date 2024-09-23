---
title: 「ACSD-45049：客戶『必要』屬性設定無法按照管理員中的網站範圍運作」
description: 套用ACSD-45049修補程式以修正Adobe Commerce中客戶「[!UICONTROL Is required]」屬性未依照Admin中的網站範圍正確覆寫的問題。
feature: Attributes, Customers
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-45049：客戶&#x200B;*[!UICONTROL Is required]*&#x200B;屬性設定無法按照Admin中的網站範圍運作

ACSD-45049修補程式修正了客戶&#x200B;*[!UICONTROL Is required]*&#x200B;屬性設定無法按照Admin中的網站範圍正確運作的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.50時，即可使用此修補程式。 修補程式ID為ACSD-45049。 請注意，問題已在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.4-p7和2.4.5 - 2.4.5-p9

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

根據Admin中的網站範圍，客戶&#x200B;*[!UICONTROL Is required]*&#x200B;屬性設定無法正常運作。

<u>要再現的步驟</u>：

1. 建立兩個網站。
1. 開啟&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer attribute]**。
1. 建立新屬性，設定&#x200B;**[!UICONTROL Is value required]** = *否*。
1. 切換到預設網站，然後變更&#x200B;**[!UICONTROL Is value required]** = *是*。 另一個網站有預設值。
1. 從Admin為非預設網站建立新客戶。

<u>預期結果</u>：

非預設網站不需要屬性。

<u>實際結果</u>：

* 在Admin中建立客戶時，非預設網站需要屬性。
* 在店面註冊客戶時，非預設網站不需要此屬性。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
