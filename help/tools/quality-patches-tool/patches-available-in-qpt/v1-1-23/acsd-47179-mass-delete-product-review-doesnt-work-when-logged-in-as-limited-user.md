---
title: 「ACSD-47179：以受限使用者角色登入時，大量刪除產品評論無法運作」
description: 套用ACSD-47179修補程式，修正以受限使用者角色登入時，大量刪除產品評論無法運作的Adobe Commerce問題。
feature: Marketing Tools, Products, Roles/Permissions
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-47179：以受限使用者角色登入時，無法大量刪除產品評論

ACSD-47179修補程式修正了以受限使用者角色登入時，大量刪除產品評論無法運作的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23時，即可使用此修補程式。 修補程式ID為ACSD-47179。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

以受限使用者角色登入時，無法大量刪除產品評論。

<u>要再現的步驟</u>：

1. 建立次要網站。
1. 建立僅限於次要網站的使用者角色，並擁有下列章節的完整許可權：
   * 目錄
   * 客戶
   * 行銷
1. 建立產品並將其指派至次要網站。
1. 從前端為產品新增兩個評論。
1. 使用剛建立的受限制管理員使用者登入[!DNL Commerce]管理員。
1. 嘗試整批刪除暫緩稽核。

<u>預期結果</u>：

具有足夠許可權的管理員可以大量刪除擱置的稽核。

<u>實際結果</u>：

您收到下列錯誤： _發生錯誤。 在support_report.log_&#x200B;中產生例外狀況

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
