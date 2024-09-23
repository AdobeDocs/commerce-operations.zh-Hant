---
title: 'ACSD-48857：使用 [!DNL Page Builder]編輯後無法儲存變更'
description: 套用ACSD-48857修補程式以修正使用者使用 [!DNL Page Builder]編輯後無法儲存變更的Adobe Commerce問題。
feature: Admin Workspace, CMS, Page Builder
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-48857：使用[!DNL Page Builder]編輯後無法儲存變更

ACSD-48857修補程式修正了使用者使用[!DNL Page Builder]編輯後無法儲存變更的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28時，即可使用此修補程式。 修補程式ID為ACSD-48857。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用[!DNL Page Builder]編輯之後，使用者無法儲存變更。

<u>要再現的步驟</u>

1. 登入Admin網站。
1. 導覽至「**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**」以建立空白的CMS頁面。
1. 執行此SQL指令碼以設定下列&#x200B;**[!UICONTROL Content]**&#x200B;欄位值：

   ```SQL
   update cms_page set content = '<div data-content-type="text" data-appearance="default" data-element="main"><h4 style="text-align: center;" contenteditable="true" data-placeholder="Edit Heading Text" data-content-type="heading" data-appearance="default" data-element="main">THE RULES</h4></div>' where page_id=8;
   ```

1. 在Admin中返回&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**。
1. 編輯您的頁面。
1. 前往&#x200B;**[!UICONTROL Content]**&#x200B;標籤。
1. 按一下&#x200B;**[!UICONTROL Save]**。

<u>預期結果</u>

已實施HTML內容淨化。 這會移除文字編輯器產生之內容中的[!DNL Page Builder]保留HTML屬性。

<u>實際結果</u>

頁面保持未儲存狀態，且載入器持續旋轉。 在主控台中會產生下列錯誤：

```
[ERROR] Page Builder was rendering for 5 seconds without releasing locks.
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
