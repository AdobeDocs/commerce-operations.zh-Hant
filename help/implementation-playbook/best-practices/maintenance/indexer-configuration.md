---
title: 索引器的配置最佳做法
description: 遵循索引器配置的最佳做法，維護和優化站點效能。
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 索引器配置的最佳實務

要優化和維護站點效能，請使用本文所述的效能最佳實踐來檢查和更新索引器配置。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce雲基礎架構
- Adobe Commerce內部

## 設定索引器以按計畫更新

Adobe Commerce有兩種索引器模式： [!UICONTROL Update on Save] （預設設定）和 [!DNL Update on Schedule].

- **[!UICONTROL Update on Save]** 模式會在目錄或其他資料變更時立即更新索引。 例如，如果管理員使用者將新產品新增至類別，則儲存更新時，會立即重新索引類別產品索引。

- **[!UICONTROL Update on Schedule]** 模式儲存有關資料更新的資訊，而重新索引操作和索引更新是由cron作業管理，該作業在後台以預定時間間隔運行。

有多名管理員在後端工作的大型存放區，或有許多匯入和匯出項目，都會觸發頻繁的索引更新。 如果您的網站索引配置設定為 [!UICONTROL Update on Save] 模式中，頻繁重新索引會降低資料庫效能，降低網站效能，並導致重新索引過程中的長延遲，特別是對於大型商店。

要最大限度地提高站點效能，請遵循以下索引最佳做法：

- 查看索引配置。
- 將索引器設定為 _[!UICONTROL Update on Schedule]_適用於大型網站，以及經常更新和大量流量的網站。 請參閱 [索引管理](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).
- 追隨 [效能最佳實務](../../../performance/configuration.md) 用於管理索引。

## 其他資訊

- [管理員用戶的索引管理](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [使用MagentoCLI進行索引管理](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [開發人員的索引概述](https://developer.adobe.com/commerce/php/development/components/indexing/)
