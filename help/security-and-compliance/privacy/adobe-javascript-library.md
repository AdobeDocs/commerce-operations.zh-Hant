---
title: Adobe隱私權JavaScript程式庫
description: 了解如何使用自訂工具存取和刪除Adobe Commerce和Magento Open Source收集的客戶個人資訊。
hide: true
hidefromtoc: true
source-git-commit: 495dfd515759e4df507479de57118586eac14fda
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---


# Adobe隱私權JavaScript程式庫

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

此 [Adobe隱私權JavaScript程式庫](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) 是一套工具，可協助您建立存取和刪除私人資料的程式。

Adobe Commerce和Magento Open Source資料追蹤服務可儲存適用於隱私權法規的私人資訊，例如 [一般資料保護規範(GDPR)](gdpr.md) 和 [加州消費者隱私法(CCPA)](ccpa.md).

此程式庫提供一組統一的功能，用於建立隱私權資料請求、將其傳送至每個產品的實作，以及收集回應。 使用此程式庫可透過這些資料追蹤服務擷取和移除瀏覽器中儲存的資料。

## 安裝

使用下列其中一種方法來下載程式庫檔案：

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

取得檔案後，您需要將其新增至Adobe Commerce和Magento Open Source例項中安裝的自訂模組或主題。 遵循 [使用自訂JavaScript](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) 完成此任務的主題。

## 使用狀況

AdobePrivacy JS程式庫提供多種功能，可管理儲存在瀏覽器中的身分資料。

`retrieveIdentities()`
:從服務傳回身分陣列，以及在服務中找不到身分陣列

`removeIdentities()`
:從瀏覽器移除身分，並傳回一系列身分物件，其中包含 `isDeleteClientSide` 布林屬性，指出資料是否已刪除。

`retrieveThenRemoveIdentities()`
:此函式類似於 `removeIdentities()` 在中，會擷取身分陣列並從瀏覽器中移除。

如需使用這些函式的詳細資訊和範例，請參閱 [官方圖書館檔案](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html).

### 初始化

實例化新 `AdobePrivacy` 物件，以在實施程式碼中使用AdobePrivacy JS資料庫。

```js
var adobePrivacy = new AdobePrivacy({});
```

建構函式在實例化期間接受具有參數的配置對象。
請參閱 [官方圖書館檔案](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) 以取得這些設定參數的清單。
