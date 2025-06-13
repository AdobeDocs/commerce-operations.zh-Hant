---
title: ACSD-48866：請求類別的RSS摘要時發生錯誤
description: 套用ACSD-48866修補程式以修正請求類別的RSS摘要時發生錯誤的Adobe Commerce問題。
feature: Admin Workspace, Categories
role: Admin
exl-id: f278a90f-f30c-401f-a544-713c89eb208a
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# ACSD-48866：請求類別的RSS摘要時發生錯誤

ACSD-48866修補程式修正了請求類別的RSS摘要時會發生錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28時，即可使用此修補程式。 修補程式ID為ACSD-48866。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

請求類別的RSS摘要時發生錯誤。

<u>要再現的步驟</u>：

1. 在&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Catalog]** > **[!UICONTROL RSS Feeds]** > **[!UICONTROL RSS Config]** > **[!UICONTROL Enable RSS]**&#x200B;中啟用RSS摘要。
1. 在&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Catalog]** > **[!UICONTROL RSS Feeds]** > **[!UICONTROL Catalog]** > **[!UICONTROL Top Level Category]**&#x200B;中啟用[!UICONTROL Top Level Category]。
1. 瀏覽店面RSS摘要類別頁面。
1. 檢查`var/log`中的記錄檔。

<u>預期結果</u>：

記錄檔中沒有錯誤。

<u>實際結果</u>：

記錄檔中顯示下列錯誤：

```
Text fields are not optimised for operations that require per-document field data like aggregations and sorting, so these operations are disabled by default. Please use a keyword field instead. Alternatively, set fielddata=true on [updated_at] in order to load field data by uninverting the inverted index.
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
