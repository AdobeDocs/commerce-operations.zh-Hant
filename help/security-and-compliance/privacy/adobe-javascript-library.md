---
title: Adobe隱私JavaScript庫
description: 瞭解如何使用自定義工具訪問和刪除Adobe Commerce和Magento Open Source收集的客戶個人資訊。
hide: true
hidefromtoc: true
exl-id: 5080e03b-0a83-405c-a232-b93311e284a3
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# Adobe隱私JavaScript庫

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

的 [Adobe隱私JavaScript庫](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) 是一組工具，用於幫助建立訪問和刪除私有資料的進程。

Adobe Commerce和Magento Open Source資料跟蹤服務可以儲存適用於隱私法規的隱私資訊，如 [一般資料保護法規(GDPR)](gdpr.md) 和 [加利福尼亞消費者隱私法(CCPA)](ccpa.md)。

此庫提供一組統一的功能，用於建立隱私資料請求、將其發送到每個產品的實施以及收集響應。 使用此庫可檢索和刪除這些資料跟蹤服務儲存在瀏覽器中的資料。

## 安裝

使用以下方法之一下載庫檔案：

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

在您擁有該檔案後，您需要將其添加到Adobe Commerce和Magento Open Source實例中安裝的自定義模組或主題中。 按照 [使用自定義JavaScript](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) 主題完成此任務。

## 用法

AdobePrivacy JS庫提供了各種功能，用於管理儲存在瀏覽器中的身份資料。

`retrieveIdentities()`
:返回服務中的一組標識，以及在服務中找不到的一組標識

`removeIdentities()`
:從瀏覽器中刪除標識並返回具有 `isDeleteClientSide` boolean屬性，用於指示資料是否已刪除。

`retrieveThenRemoveIdentities()`
:此函式類似於 `removeIdentities()` 中，它將檢索一組標識並從瀏覽器中刪除它們。

有關使用這些函式的詳細資訊和示例，請參見 [正式庫文檔](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html)。

### 初始化

實例化新 `AdobePrivacy` 對象，用於在實現代碼中使用AdobePrivacy JS庫。

```js
var adobePrivacy = new AdobePrivacy({});
```

在實例化期間，建構子接受帶有參數的配置對象。
請參閱 [正式庫文檔](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) 清單。
