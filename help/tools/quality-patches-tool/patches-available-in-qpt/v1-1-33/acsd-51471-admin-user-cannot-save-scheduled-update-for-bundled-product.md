---
title: ACSD-51471：管理員使用者無法儲存套件產品的排程更新
description: 套用ACSD-51471修補程式以修正Adobe Commerce問題，該問題導致管理員使用者無法針對使用簡單產品及排程更新的套件產品儲存排程更新。
exl-id: d8134111-63f0-4476-a407-677bda52fa90
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-51471：管理員使用者無法儲存套件產品的排程更新

ACSD-51471修補程式修正了管理員使用者無法為使用簡單產品與排程更新的套件產品儲存排程更新的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33時，即可使用此修補程式。 修補程式ID為ACSD-51471。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

對於使用簡單產品的套件產品，如果其本身有排程更新，管理員使用者無法儲存該產品的排程更新。

<u>要再現的步驟</u>：

1. 建立簡單的產品。
1. 新增簡單產品的排程更新，只包含&#x200B;*開始日期*&#x200B;且沒有&#x200B;*結束日期*。
1. 套用更新後，請變更產品的SKU。
1. 建立套件式產品，並將步驟1中建立的簡單產品新增為子產品。
1. 為套件產品建立排程更新，以啟用套件產品。 提供排程更新的&#x200B;*開始日期*&#x200B;和&#x200B;*結束日期*。
1. 儲存排定的更新。

<u>預期結果</u>：

排定的更新已成功儲存。

<u>實際結果</u>：

儲存排定的更新時發生下列錯誤： *要求的產品不存在。 請驗證產品，然後再試一次。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
