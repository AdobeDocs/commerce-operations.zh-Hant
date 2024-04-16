---
title: 範例資料概述
description: 瞭解如何在Adobe Commerce專案中使用範例資料。
exl-id: 828b009d-a6ff-4db2-aa1a-838f6f55a194
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# 範例資料概述

範例資料提供以Luma主題為基礎的店面，配備產品、類別、客戶註冊等。 它的功能就像Commerce的店面，您可以使用管理員來控制價格、庫存和促銷定價規則。

>[!NOTE]
>
>若要檢閱和分析資料庫和各種功能，請考慮使用真實資料而不是範例資料。 範例資料設計為預先產生的商店模擬，以示範主題設計和基本商店行為。 安裝範例資料時，所有範例資料實體都會直接寫入資料庫表格。

您可以在安裝Commerce軟體之前或之後安裝範例資料。 使用完範例資料後，您可以將其移除或全新安裝，如中所述 [移除範例資料模組或更新範例資料](remove-or-update.md).

>[!WARNING]
>
>無法解除安裝範例資料。 僅使用範例資料來瞭解Adobe Commerce的運作方式。 請避免在已安裝範例資料的系統上進行任何開發。

您可以透過下列任何方式安裝選用的範例資料：

| 安裝方法 | 說明 | 所需技能等級 |
|--- |--- |--- |
| 使用撰寫器 | [執行 `magento sampledata:deploy` 修改應用程式的根目錄 `composer.json`](composer-packages.md) 以啟用範例資料模組。 | 需要Composer知識以及對Commerce檔案系統的存取權。 |
| 複製存放庫 | [複製GitHub存放庫](git-repositories.md) 和範例資料存放庫，然後將它們連結在一起。 | 僅供參與開發人員使用。 其他人都應使用上述其中一種方法。 |
