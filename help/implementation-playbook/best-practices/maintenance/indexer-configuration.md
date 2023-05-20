---
title: 索引器配置最佳做法
description: 通過遵循索引器配置的最佳做法維護和優化站點效能。
role: Admin, User
feature: Best Practices
feature-set: Commerce
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# 索引器配置的最佳做法

要優化和維護站點效能，請使用本文中描述的效能最佳實踐查看和更新索引器配置。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce在雲基礎架構上
- Adobe Commerce內部

## 設定索引器以更新計畫

Adobe Commerce有兩種索引器模式： [!UICONTROL Update on Save] （預設設定）和 [!DNL Update on Schedule]。

- **[!UICONTROL Update on Save]** 模式會在目錄或其他資料更改時立即更新索引。 例如，如果管理員用戶將新產品添加到類別，則在保存更新時立即重新索引類別產品索引。

- **[!UICONTROL Update on Schedule]** 模式儲存有關資料更新的資訊，並且重新索引操作和索引更新由在後台以預定時間間隔運行的cron作業管理。

如果有一個大型儲存，而且有多個管理員在後端工作，或者有許多導入和導出操作會觸發頻繁的索引更新。 如果站點索引配置設定為 [!UICONTROL Update on Save] 模式，頻繁的重新索引降低了資料庫效能，這會降低站點效能，並導致重新索引過程中出現長的延遲，特別是對於大型儲存。

要最大限度地提高站點效能，請遵循以下索引最佳做法：

- 查看索引配置。
- 將索引器設定為 _[!UICONTROL Update on Schedule]_適用於大型站點，以及更新頻繁且流量較大的站點。 請參閱 [索引管理](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode)。
- 關注 [最佳效能](../../../performance/configuration.md) 中。

>[!IMPORTANT]
>
>的 [!DNL Customer Grid] 只能使用 [!UICONTROL Update on Save] 的雙曲餘切值。 此索引不支援 `Update by Schedule` 的雙曲餘切值。

## 其他資訊

- [管理員用戶的索引管理](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [使用MagentoCLI進行索引管理](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [開發人員索引概述](https://developer.adobe.com/commerce/php/development/components/indexing/)
