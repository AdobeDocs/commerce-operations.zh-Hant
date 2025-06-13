---
title: ACSD-59378：匯入期間儲存區層級 [!DNL URL] 的重寫更新不正確
description: 套用ACSD-59378修補程式以修正匯入期間未正確更新存放區層級 [!DNL URL] 重寫的Adobe Commerce問題。
feature: Data Import/Export
role: Admin, Developer
exl-id: dc54d810-dcc6-42c6-a877-d00d3cf4f9a5
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-59378：匯入期間錯誤地更新了存放區層級[!DNL URL]重寫

ACSD-59378修補程式修正了匯入期間未正確更新存放區層級[!DNL URL]重寫的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50時，即可使用此修補程式。 修補程式ID為ACSD-59378。 請注意，此問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.5-p5

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.5x （所有2.4.5版本）

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

匯入期間未正確更新存放區層級[!DNL URL]重寫。

<u>要再現的步驟</u>：

1. 在&#x200B;**所有存放區檢視**&#x200B;範圍中建立具有`url_key = key_default`的產品。
1. 在&#x200B;**預設存放區檢視**&#x200B;範圍中設定`url_key = key_store`。
1. 匯出產品。
1. 匯入此產品的[!DNL CSV]檔案，其中包含下列資料：
   * `store_view_code`欄設定為&#x200B;*empty*，因此適用於&#x200B;**所有存放區檢視**&#x200B;範圍。
   * `url_key`已設定為預設金鑰&#x200B;*`key_default`*。

<u>預期結果</u>：

[!DNL URL]重寫僅針對沒有覆寫`url_key`的存放區檢視重新產生（預設值`url_key`適用）。

<u>實際結果</u>：

已刪除`key_store` [!DNL URL]個重寫，但產品之&#x200B;**預設存放區檢視**&#x200B;層級上的[!DNL URL]重寫仍設為&#x200B;*`key_store`*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
