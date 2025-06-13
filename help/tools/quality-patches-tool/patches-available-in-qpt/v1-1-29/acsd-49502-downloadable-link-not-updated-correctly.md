---
title: ACSD-49502： [!DNL staging] 更新後，可下載的連結未正確更新
description: 套用ACSD-49502修補程式以修正Adobe Commerce問題，此問題發生在將 [!DNL staging] 更新套用至可下載產品後，可下載連結未正確更新。
feature: Staging
role: Admin
exl-id: 9bdc9a7e-4291-4438-9ba0-65fcab1f95bb
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-49502： [!DNL staging]更新後未正確更新可下載的連結

ACSD-49502修補程式修正將[!DNL staging]更新套用至可下載產品後，可下載連結未正確更新的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29時，即可使用此修補程式。 修補程式ID為ACSD-49502。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

將[!DNL staging]更新套用至可下載的產品後，可下載的連結未正確更新。

<u>要再現的步驟</u>：

1. 建立包含連結的可下載產品。
1. 建立客戶帳戶並登入。
1. 將可下載的產品從店面新增到購物車。
1. 在&#x200B;**[!UICONTROL Admin]**&#x200B;中，為可下載的產品排程新的更新，並讓排程的更新完成。
1. 完成店面的訂單。

<u>預期結果</u>：

使用排程的更新時，當先前新增的產品在購物車中時，可下載的連結會保留。

<u>實際結果</u>：

在客戶的&#x200B;*[!UICONTROL My Account]* ([!UICONTROL My Downloadable Products])下以及在&#x200B;**[!UICONTROL Admin]**&#x200B;中的訂單檢視頁面皆遺失可下載的連結。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
