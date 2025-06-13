---
title: ACSD-50512：更新可下載產品中繼更新的開始日期時發生錯誤
description: 套用ACSD-51892修補程式以修正Adobe Commerce效能問題，其中錯誤*可下載連結與產品無關。請確認連結，然後再試一次* （在更新可下載產品測試版更新的開始日期時發生）。
feature: Products, Staging
role: Admin
exl-id: 9c3b4d45-c500-46a7-8679-a8aa9e0a66d6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-50512：更新可下載產品測試更新的開始日期時發生錯誤

ACSD-50512修補程式修正錯誤&#x200B;*可下載連結與產品無關的問題。 請驗證連結，然後再試一次*，此動作會在更新可下載產品測試更新的開始日期時發生。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.33時，即可使用此修補程式。 修補程式ID為ACSD-51502。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

錯誤&#x200B;*可下載的連結與產品無關。 請驗證連結，然後再試一次*，此動作會在更新可下載產品測試更新的開始日期時發生。

<u>要再現的步驟</u>：

1. 建立可下載的產品，其中包含&#x200B;*可下載連結*&#x200B;和&#x200B;*範例連結*。
1. 為相同產品建立排程更新，並儲存產品。
1. 編輯預先設定的排程更新（從步驟2）並變更開始日期。
1. 儲存排定的更新。

<u>預期結果</u>：

已成功儲存排程更新的變更。

<u>實際結果</u>：

您收到錯誤： *可下載的連結與產品無關。 請驗證連結，然後再試一次*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
