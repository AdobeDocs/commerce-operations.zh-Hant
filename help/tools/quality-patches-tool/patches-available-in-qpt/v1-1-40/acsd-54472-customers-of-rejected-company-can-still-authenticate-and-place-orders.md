---
title: 「ACSD-54472：被拒絕公司的客戶仍然可以驗證」
description: 套用ACSD-54472修補程式以修正遭拒絕公司的客戶仍可驗證，以及遭封鎖和遭拒絕公司的客戶仍可下訂單的Adobe Commerce問題。
feature: B2B
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ACSD-54472：被拒絕公司的客戶仍可驗證

ACSD-54472修補程式修正被拒絕公司的客戶仍可驗證，以及被封鎖和拒絕公司的客戶仍可下訂單的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40時，即可使用此修補程式。 修補程式ID為ACSD-54472。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

被拒絕公司的客戶仍然可以驗證，被封鎖和被拒絕公司的客戶仍然可以下訂單。

<u>要再現的步驟</u>：

1. 建立公司。
1. 透過[!DNL GraphQL]新增產品至購物車。
1. 將公司狀態變更為&#x200B;*已封鎖*。
1. 傳送[!DNL GraphQL]請求以下訂單並建立可轉讓的報價。
1. 將公司狀態變更為&#x200B;*已拒絕*。
1. 傳送[!DNL GraphQL]要求以取得公司的使用者授權權杖。
1. 將客戶狀態設為&#x200B;*非使用中*。
1. 傳送[!DNL GraphQL]要求以取得公司的使用者授權權杖。

<u>預期結果</u>：

* *已封鎖*&#x200B;公司的使用者並未下達訂單與可轉讓報價。
* 未取得&#x200B;*Rejected*&#x200B;公司之使用者的授權權杖。
* 未取得&#x200B;*非作用中*&#x200B;客戶的授權權杖。

<u>實際結果</u>：

* 訂單與可轉讓報價由&#x200B;*已封鎖*&#x200B;公司的使用者下單。
* 已為&#x200B;*已拒絕*&#x200B;公司的使用者取得授權權杖。
* 已為&#x200B;*非作用中*&#x200B;客戶取得授權權杖。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
