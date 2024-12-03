---
title: ACSD-54060：限制的管理員無法儲存產品（如果它是其他產品的子項）
description: 套用ACSD-54060修補程式以修正Adobe Commerce限制管理員無法儲存產品（如果產品是指派給其他範圍之其他產品的子產品）的問題。
feature: Admin Workspace, Roles/Permissions, Products
role: Admin, Developer
exl-id: 2af24cbf-65a1-4bd6-aad3-19b613bee7f2
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-54060：限制的管理員無法儲存產品（如果它是其他產品的子項）

ACSD-54060修補程式修正受限管理員無法儲存產品（若為指派至不同範圍的另一個產品的子產品）的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.42時，即可使用此修補程式。 修補程式ID為ACSD-54060。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果受限制的管理員是另一個產品的子項，且被指派到不同範圍，則該受限制的管理員無法儲存產品。

<u>要再現的步驟</u>：

1. 建立其他網站。
1. 建立簡單產品並將其指派給兩個網站。
1. 以簡單產品作為唯一變數建立可設定產品，並僅將可設定產品指派給預設網站。
1. 建立只能存取第二個網站的受限管理員使用者。
1. 以受限制的管理員使用者身分登入。
1. 請嘗試變更第二個網站範圍內的簡單產品名稱。

<u>預期結果</u>：

受限制的管理員可以變更產品名稱。

<u>實際結果</u>：

發生錯誤： *需要更多許可權才能檢視此專案*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
