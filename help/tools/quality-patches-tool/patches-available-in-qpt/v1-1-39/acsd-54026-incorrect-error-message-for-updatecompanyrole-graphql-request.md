---
title: ACSD-54026： updateCompanyRole GraphQL請求的錯誤訊息不正確
description: 套用ACSD-54026修補程式以修正Adobe Commerce問題，其中針對非授權使用者的updateCompanyRole GraphQL請求存在不正確的錯誤訊息。
feature: Roles/Permissions
role: Admin, Developer
exl-id: 21695333-5f18-48db-acde-246f269dd691
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-54026： `updateCompanyRole` GraphQL要求的錯誤訊息不正確

ACSD-54026修補程式修正了針對非授權使用者的`updateCompanyRole` GraphQL請求有不正確的錯誤訊息的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.39時，即可使用此修補程式。 修補程式ID為ACSD-54026。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

針對非授權使用者的`updateCompanyRole`個GraphQL請求取得不正確的錯誤訊息。

<u>要再現的步驟</u>：

1. 在設定中啟用B2B公司。
1. 建立公司。
1. 傳送`updateCompanyRole`個GraphQL要求，但不傳遞持有人權杖或持有人權杖無效。
1. 觀察GraphQL回應中的錯誤訊息。

<u>預期結果</u>：

您收到下列錯誤訊息： *目前的客戶未獲授權。*

<u>實際結果</u>：

您收到下列錯誤訊息： *客戶不是公司使用者。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
