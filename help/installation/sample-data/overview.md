---
title: 範例資料概觀
description: 了解如何為Adobe Commerce和Magento Open Source專案使用範例資料。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---


# 範例資料概觀

範例資料會根據Luma主題提供店面，這些主題會包含產品、類別、客戶註冊等。 它的功能與商務店麵類似，您可以使用管理員來控制價格、庫存和促銷定價規則。

您可以在安裝商務軟體之前或之後安裝範例資料。 處理完範例資料後，您可以移除該資料，或依照 [移除範例資料模組或更新範例資料](remove-or-update.md).

>[!WARNING]
>
>無法卸載示例資料。 建議您僅使用範例資料來了解Adobe Commerce和Magento Open Source的運作方式。 請避免在安裝範例資料的系統中執行任何開發作業。

您可以透過下列任何方式安裝選用的範例資料：

| 安裝方法 | 說明 | 所需技能級別 |
|--- |--- |--- |
| 使用撰寫器 | [執行 `magento sampledata:deploy` 修改應用程式的根 `composer.json`](composer-packages.md) 啟用範例資料模組。 | 需要撰寫器知識和對商務檔案系統的存取。 |
| 複製儲存庫 | [複製GitHub存放庫](git-repositories.md) 和範例資料存放庫，然後將它們連結在一起。 | 僅供貢獻開發人員使用。 其他所有人都應使用上述方法之一。 |
