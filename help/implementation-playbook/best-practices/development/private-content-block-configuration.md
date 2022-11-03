---
title: 私人內容區塊最佳作法
description: 了解設定私人內容區塊以最佳化店面效能的最佳實務。
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 私人內容區塊最佳作法

當私人內容區塊包含 `_isScopePrivate` 變數，則區塊無法快取。 由於未快取私人區塊，Adobe Commerce必須擷取每個客戶請求的相同資料，而增加伺服器負載。

而非使用 `_isScopePrivate` 變數，建立區塊和範本以顯示不受使用者限制的資料。 此資料會由Adobe Commerce以使用者特定資料取代 [UI元件](https://glossary.magento.com/ui-component/)，可更有效率地處理預先轉譯資料。 如需指示，請參閱 [私人內容](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) 在 _[!DNL Commerce PHP Extensions Guide]_.

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce雲基礎架構
- Adobe Commerce內部

## 潛在的效能影響

具有包含的私人內容區塊的網站 `_isScopePrivate` 變數會觸發AJAX請求，以擷取每個客戶請求的相同資料。 這會增加回應時間，並使用可用於處理更多業務關鍵型店面操作（如客戶註冊、購物車更新、訂單提交和付款交易）的額外資源。

## 其他資訊

- [私人內容](../../../performance/configuration.md#client-side-optimization-settings)
- [高吞吐量AJAX請求會導致效能不佳](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)


