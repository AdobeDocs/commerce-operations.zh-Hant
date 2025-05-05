---
title: Adobe隱私權JavaScript資料庫
description: 瞭解如何使用自訂工具來存取和刪除Adobe Commerce收集的客戶個人資訊。
hide: true
hidefromtoc: true
exl-id: 5080e03b-0a83-405c-a232-b93311e284a3
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Adobe隱私權JavaScript資料庫

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

[Adobe隱私權JavaScript資料庫](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html?lang=zh-Hant)是一組工具，可協助建立存取和刪除私人資料的程式。

Adobe Commerce資料追蹤服務可儲存適用於隱私權法規的私人資訊，例如[一般資料保護規範(GDPR)](gdpr.md)和[加州消費者隱私保護法(CCPA)](ccpa.md)。

此程式庫提供一組統一的功能，可用於建立隱私權資料請求、傳送給每個產品的實施，以及收集回應。 使用此資料庫來擷取和移除這些資料追蹤服務儲存在瀏覽器中的資料。

## 安裝

使用下列其中一種方法下載程式庫檔案：

- npm： `npm install @adobe/adobe-privacy`
- GitHub： [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

取得檔案後，您需要將其新增到Adobe Commerce執行個體中安裝的自訂模組或主題。 依照[使用自訂JavaScript](https://developer.adobe.com/commerce/frontend-core/javascript/custom/)主題中說明的指示完成此工作。

## 使用狀況

AdobePrivacy JS資料庫提供多種功能，用於管理儲存在瀏覽器中的身分資料。

`retrieveIdentities()`
：從服務傳回身分陣列，以及在服務中找不到的身分陣列

`removeIdentities()`
：從瀏覽器移除身分，並傳回具有`isDeleteClientSide`布林值屬性的身分物件陣列，以指出資料是否已刪除。

`retrieveThenRemoveIdentities()`
：此函式類似於`removeIdentities()`，因為它會擷取身分識別陣列，並從瀏覽器中移除身分識別。

如需有關使用這些函式的詳細資訊和範例，請參閱[正式程式庫檔案](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html?lang=zh-Hant)。

### 初始化

將新的`AdobePrivacy`物件例項化，以在實作程式碼中使用AdobePrivacy JS程式庫。

```js
var adobePrivacy = new AdobePrivacy({});
```

建構函式在具現化期間接受具有引數的設定物件。
如需這些組態引數的清單，請參閱[官方程式庫檔案](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html?lang=zh-Hant)。
