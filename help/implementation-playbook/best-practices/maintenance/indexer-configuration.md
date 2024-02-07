---
title: 索引器的設定最佳實務
description: 遵循索引器設定的最佳實務，以維護並最佳化網站效能。
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: af66d47279245f8ee105030bbb33d77b1b35c3e5
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# 索引器設定的最佳實務

為了最佳化及維護網站效能，請使用本文所述的效能最佳實務來檢閱及更新索引器設定。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 設定索引子以依排程更新

Adobe Commerce有兩種索引子模式： [!UICONTROL Update on Save] （預設設定）和 [!DNL Update on Schedule].

- **[!UICONTROL Update on Save]** 模式會在目錄或其他資料變更時立即更新索引。 例如，如果管理員使用者將新產品新增到類別，則類別產品索引會在儲存更新時立即重新索引。

- **[!UICONTROL Update on Schedule]** 模式會儲存資料更新的相關資訊，而重新索引作業和索引更新則由cron作業管理，該作業會以排定的間隔在背景執行。 cron作業並不總是在每次執行時執行重新索引。 只有在索引器變更記錄中有新專案時（例如，索引器上有待處理專案），才會重新索引。

如果大型存放區有多個管理員在後端工作或有許多匯入和匯出，則會觸發頻繁的索引更新。 如果您的網站索引設定設為 [!UICONTROL Update on Save] 模式，頻繁重新索引會降低資料庫效能，進而減慢網站效能，並造成重新索引程式長時間延遲，尤其是對於大型商店。

若要最大化網站效能，請遵循以下編制索引最佳實務：

- 檢閱索引設定。
- 將索引子設為 _[!UICONTROL Update on Schedule]_適用於經常更新且流量很大的大型網站和網站。 另請參閱 [索引管理](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).
- 追隨 [效能最佳實務](../../../performance/configuration.md) 用於管理索引。

>[!IMPORTANT]
>
>此 [!DNL Customer Grid] 只能使用重新索引 [!UICONTROL Update on Save] 選項。 此索引不支援 `Update by Schedule` 選項。

## 其他資訊

- [管理員使用者的索引管理](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [使用MagentoCLI進行索引管理](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [適用於開發人員的索引概觀](https://developer.adobe.com/commerce/php/development/components/indexing/)
