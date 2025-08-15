---
title: ACSD-47336：在Adobe Commerce管理中關閉通知時出現[!UICONTROL Something went wrong]錯誤
description: 套用ACSD-47336修補程式來修正Adobe Commerce問題，此問題導致使用者在[!UICONTROL Something went wrong]管理員中關閉通知時看到 [!DNL Commerce] 錯誤。
feature: Admin Workspace
role: Admin
exl-id: da0c0119-6720-493f-a278-d573ed898a63
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-47336：在Adobe Commerce管理中關閉通知時出現&#x200B;_[!UICONTROL Something went wrong]_錯誤

ACSD-47336修補程式修正了使用者在&#x200B;_[!UICONTROL Something went wrong]_Admin中關閉通知時看到[!DNL Commerce]錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24時，即可使用此修補程式。 修補程式ID為ACSD-47336。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法）： 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法）： 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在&#x200B;_[!UICONTROL Something went wrong]_管理員中關閉通知時，使用者會看到[!DNL Commerce]錯誤。

<u>要再現的步驟</u>：

1. 執行大量作業（例如，從產品格線大量更新產品屬性）。
1. 完成作業（例如，執行`bin/magento queue:consumer:start product_action_attribute.update`）。
1. 重新整理[!DNL Commerce]管理頁面，展開管理通知區段，然後按一下&#x200B;**[!UICONTROL Dismiss All Completed Tasks]**&#x200B;連結。

<u>預期結果</u>：

清除已完成的任務時，不應顯示&#x200B;_[!UICONTROL Something went wrong]_錯誤。

<u>實際結果</u>：

顯示&#x200B;_[!UICONTROL Something went wrong]_錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜尋修補程式[!DNL Quality Patches Tool]。
