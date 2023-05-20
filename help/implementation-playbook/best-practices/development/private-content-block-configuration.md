---
title: 專用內容塊的最佳做法
description: 瞭解配置私有內容塊以優化店面效能的最佳做法。
role: Developer
feature: Best Practices
feature-set: Commerce
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# 專用內容塊的最佳做法

當私有內容塊包含 `_isScopePrivate` 變數，該塊不可快取。 由於私有塊未快取，Adobe Commerce必須為每個客戶請求檢索相同的資料，這會增加伺服器負載。

而不是使用 `_isScopePrivate` 為私有內容建立變數，建立塊和模板以顯示用戶不可知的資料。 該資料由Adobe CommerceUI元件用用戶專用資料替換，該元件可更有效地處理預呈現資料。 有關說明，請參見 [專用內容](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) 的 _[!DNL Commerce PHP Extensions Guide]_。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce在雲基礎架構上
- Adobe Commerce內部

## 潛在效能影響

具有包含以下內容的私有內容塊的站點 `_isScopePrivate` 變數AJAX觸發請求以檢索每個客戶請求的相同資料。 這增加了響應時間，並使用了可用於處理更多業務關鍵型店面操作的額外資源，如客戶註冊、購物車更新、訂單提交和付款交易。

## 其他資訊

- [專用內容](../../../performance/configuration.md#client-side-optimization-settings)
- [高吞吐量AJAX請求導致效能差](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)
