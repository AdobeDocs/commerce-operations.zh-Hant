---
title: 「ACSD-54983：具有GraphQL的公司使用者UID不適用於非作用中使用者」
description: 套用ACSD-54983修補程式以修正Adobe Commerce問題，即當使用者狀態設為非使用中時，無法取得具有GraphQL要求的公司使用者UID。
feature: GraphQL
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-54983：具有GraphQL的公司使用者UID不適用於非作用中的使用者

ACSD-54983修補程式修正了當使用者狀態設為非使用中時，無法讓公司使用者UID收到GraphQL請求的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43時，即可使用此修補程式。 修補程式ID為ACSD-54983。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當使用者狀態設為非作用中時，無法取得具有GraphQL要求的公司使用者UID。

<u>要再現的步驟</u>：

1. 建立具有管理員使用者的公司。 例如company@test.com。
1. 建立新客戶。
1. 將新客戶指派給公司。
1. 取得&#x200B;**[!UICONTROL company admin token]**。
1. 使用&#x200B;**[!UICONTROL company admin token]**&#x200B;擷取公司結構。 請參閱我們的開發人員檔案中的[傳回公司結構](https://developer.adobe.com/commerce/webapi/graphql/schema/b2b/company/queries/company/#return-the-company-structure)。
1. 回應只包含具有其ID的&#x200B;*ACTIVE*&#x200B;客戶。
1. 將公司使用者更新為&#x200B;*非使用中*。
1. 再次擷取公司結構。

<u>預期結果</u>：

當狀態設定為非使用中時，可取得公司使用者UID。

<u>實際結果</u>：

非作用中客戶不在清單中。 當狀態設定為非使用中時，無法取得公司使用者UID。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
