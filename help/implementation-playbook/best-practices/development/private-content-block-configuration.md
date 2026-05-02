---
title: 私人內容區塊的最佳實務
description: 瞭解設定私人內容區塊的最佳實務，以最佳化店面效能。
role: Developer
feature: Best Practices
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
source-git-commit: f9a135fc63574ccbecd3f564a87fc5c4ac03f009
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# 私人內容區塊的最佳實務

當私人內容區塊包含`_isScopePrivate`變數時，該區塊將無法快取。 由於未快取私人區塊，因此Adobe Commerce必須針對每個會增加伺服器負載的客戶請求擷取相同的資料。

不要將`_isScopePrivate`變數用於私人內容，請建立區塊和範本以顯示與使用者無關的資料。 此資料會由Adobe Commerce UI元件取代為使用者特定資料，此元件可更有效率地處理預先呈現資料。 如需指示，請參閱&#x200B;_[!DNL Commerce PHP Extensions Guide]_&#x200B;中的[私人內容](https://developer.adobe.com/commerce/php/development/cache/page/private-content/)。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md)：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 對效能的潛在影響

具有包含`_isScopePrivate`變數的私人內容區塊的網站會觸發AJAX請求，以擷取每個客戶請求的相同資料。 這會增加回應時間，並使用可用來處理更多關鍵業務店面作業的其他資源，例如客戶註冊、購物車更新、訂單提交和付款交易。

## 其他資訊

- [私人內容](../../../performance/configuration.md#client-side-optimization-settings)
- _[!DNL Commerce PHP Extensions Guide]_&#x200B;中的[可快取和私用區塊](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#cacheable-and-private-blocks)
