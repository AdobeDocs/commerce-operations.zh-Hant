---
title: 示例資料概述
description: 瞭解如何使用Adobe Commerce和Magento Open Source項目的示例資料。
exl-id: 828b009d-a6ff-4db2-aa1a-838f6f55a194
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# 示例資料概述

示例資料提供基於Luma主題的庫面，該主題包括產品、類別、客戶註冊等。 它的功能與Commerce商店一樣，您可以使用管理員來操縱價格、庫存和促銷定價規則。

您可以在安裝Commerce軟體之前或之後安裝示例資料。 完成對示例資料的處理後，您可以刪除該資料，也可以按中所討論的方式安裝新資料 [刪除示例資料模組或更新示例資料](remove-or-update.md)。

>[!WARNING]
>
>無法卸載示例資料。 我們建議您僅使用示例資料來瞭解Adobe Commerce和Magento Open Source的工作方式。 避免在安裝了示例資料的系統中進行任何開發。

可以通過以下任何方式安裝可選示例資料：

| 安裝方法 | 說明 | 所需技能級別 |
|--- |--- |--- |
| 使用作曲家 | [運行 `magento sampledata:deploy` 修改應用程式的根 `composer.json`](composer-packages.md) 啟用示例資料模組。 | 需要Composer知識和對Commerce檔案系統的訪問權。 |
| 克隆儲存庫 | [克隆GitHub儲存庫](git-repositories.md) 和示例資料儲存庫，然後將它們連結在一起。 | 僅供開發人員使用。 其他人都應使用上述方法之一。 |
