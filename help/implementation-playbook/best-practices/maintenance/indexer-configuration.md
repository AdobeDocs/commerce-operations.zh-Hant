---
title: 索引器的設定最佳實務
description: 遵循索引器設定的最佳實務，以維護並最佳化網站效能。
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: 29168544e3a33b874b104f308bd53cb475ac2638
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# 索引器設定的最佳實務

為了最佳化及維護網站效能，請使用本文所述的效能最佳實務來檢閱及更新索引器設定。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md)：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 設定索引子以依排程更新

Adobe Commerce有兩種索引子模式： [!UICONTROL Update on Save]和[!DNL Update on Schedule]。

- 當目錄或其他資料變更時，**[!UICONTROL Update on Save]**&#x200B;模式會立即更新索引。 例如，如果管理員使用者將新產品新增到類別，則類別產品索引會在儲存更新時立即重新索引。

- **[!UICONTROL Update on Schedule]**&#x200B;模式會儲存資料更新的相關資訊，而重新索引作業和索引更新是由在背景以排程間隔執行的cron作業所管理。 cron作業並不總是在每次執行時執行重新索引。 只有在索引器變更記錄中有新專案時（例如，索引器上有待處理專案），才會重新索引。

如果大型存放區有多個管理員在後端工作或有許多匯入和匯出，則會觸發頻繁的索引更新。 如果您的網站索引設定設為[!UICONTROL Update on Save]模式，經常重新索引會降低資料庫效能，進而減慢網站效能，並造成重新索引程式長時間延遲，尤其是對於大型商店。

若要最大化網站效能，請遵循以下編制索引最佳實務：

- 檢閱索引設定。
- 針對大型網站、經常更新且流量很大的網站，將索引子設定為&#x200B;_[!UICONTROL Update on Schedule]_。 請參閱[索引管理](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/tools/index-management#change-the-index-mode)。
- 遵循[效能最佳實務](../../../performance/configuration.md)管理索引。

>[!IMPORTANT]
>
>[!DNL Customer Grid]索引子行為在2.4.8中變更：
>
>- **2.4.8**&#x200B;之前： [!DNL Customer Grid]索引子只能使用[!UICONTROL Update on Save]選項重新索引，不支援[!UICONTROL Update by Schedule]選項。
>- **2.4.8和更新版本**： [!DNL Customer Grid]索引子同時支援[!UICONTROL Update on Save]和[!UICONTROL Update by Schedule]模式，且預設為[!UICONTROL Update by Schedule]。

## 其他資訊

- [管理員使用者的索引管理](../../../configuration/cli/manage-indexers.md#configure-indexers)
- 使用Magento CLI的[索引管理](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html?lang=zh-Hant)
- [開發人員的索引概觀](https://developer.adobe.com/commerce/php/development/components/indexing/)
