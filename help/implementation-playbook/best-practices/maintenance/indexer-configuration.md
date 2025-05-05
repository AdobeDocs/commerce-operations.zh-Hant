---
title: 索引器的配置最佳做法
description: 按照索引器配置的最佳做法維護和優化網站績效。
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# 索引器配置的最佳做法

若要優化和維護網站績效，請使用本文中所述的性能最佳做法查看和更新索引器配置。

## 受影響的產品和版本

[所有受支援的版本](../../../release/versions.md) ：

- Adobe Systems Commerce on 雲端基礎結構
- 本地Adobe Systems商務

## 將索引器設置為按計劃更新

Adobe Systems商務具有兩種類型的索引器模式： [!UICONTROL Update on Save] 和 [!DNL Update on Schedule]。

- **[!UICONTROL Update on Save]** 模式會在您的目錄或其他數據發生變更時立即更新索引。 例如，如果管理員用戶向類別添加新產品，則保存更新時會立即重新編製類別產品索引。

- **[!UICONTROL Update on Schedule]**&#x200B;模式會儲存資料更新的相關資訊，而重新索引作業和索引更新是由在背景以排程間隔執行的cron作業所管理。 cron 作業並不總是在每次運行時都執行重新索引。 僅當索引器更改日誌中有新條目（例如，索引器上存在積壓）時，它才會重新編製索引。

具有多個管理員在後端工作或具有許多導入和導出的大型商店會觸發頻繁的索引更新。 如果將網站索引配置設置為 [!UICONTROL Update on Save] 模式，則頻繁重新編製索引會降低資料庫性能，從而降低網站績效速度並導致重新編製索引過程出現長時間延遲，尤其是對於大型商店。

為了最大程度地網站績效，追隨以下索引最佳實務：

- 查看索引配置。
- 將索引器設置為 用於 _[!UICONTROL Update on Schedule]_&#x200B;大型網站以及更新頻繁且流量量大的網站。 請參閱 [Index管理](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management#change-the-index-mode)。
- 遵循 [管理索引的性能最佳做法](../../../performance/configuration.md) 。

>[!IMPORTANT]
>
>只能 [!DNL Customer Grid] 使用 該 [!UICONTROL Update on Save] 選項重新編製索引。 此索引不支援該 `Update by Schedule` 選項。

## 其他資訊

- [管理員使用者的Index管理](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [使用MagentoCLI的索引管理](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [面向開發人員的索引概述](https://developer.adobe.com/commerce/php/development/components/indexing/)
