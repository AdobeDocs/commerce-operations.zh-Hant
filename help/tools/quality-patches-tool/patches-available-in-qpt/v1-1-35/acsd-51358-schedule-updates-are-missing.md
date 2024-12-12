---
title: ACSD-51358：缺少排程更新
description: 套用ACSD-51358修補程式以修正Adobe Commerce問題，該問題導致排程更新中的變更在沒有結束日期的情況下移除相同實體上的其他排程更新。
feature: Staging
role: Admin, Developer
exl-id: 6e2e598b-72f1-4f00-a989-3f75bf65f8f0
source-git-commit: 1a78b2afa6e751d430700e72f512f7d82d1c1bdd
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51358：缺少排程更新

ACSD-51358修補程式修正了排程更新中無結束日期的變更導致移除相同實體上其他排程更新的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.35時，即可使用此修補程式。 修補程式ID為ACSD-51358。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

排程更新中沒有結束日期的變更會導致移除相同實體上的其他排程更新。

<u>要再現的步驟</u>：

1. 建立不含結束日期的&#x200B;**[!UICONTROL scheduled update]** （*更新1*）。
1. 建立開始日期與第一次更新相同的新&#x200B;**[!UICONTROL scheduled update]**，但新增隔天和結束日期（*更新2*）。
1. 編輯在步驟1建立的&#x200B;**[!UICONTROL scheduled update]** （*更新1*），並儲存變更。

<u>預期結果</u>

編輯(*update 1*)時，(*update 2*)應保留在&#x200B;**[!UICONTROL schedule update]**&#x200B;清單中。

<u>實際結果</u>

編輯（*更新1*）時，（*更新2*）已從&#x200B;**[!UICONTROL schedule update]**&#x200B;清單中移除。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)。
