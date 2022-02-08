---
title: Adobe Commerce整合選項
description: 探索將其他系統與您的Adobe Commerce實施整合的選項。
exl-id: 10de70d2-ff3b-4f10-b370-01d805b745dc
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# 典型整合點和資料流

整合和資料流主要有兩種方法，它們非常相似，但有一個關鍵區別。

## 單片

下圖描述了一種將Adobe Commerce同時用作後端系統和店面應用程式的整體方法：

![Adobe Commerce整體圖](../../assets/playbooks/integration-monolith.svg)

## 無頭

下圖描述了一種無頭方法，它使用Adobe Commerce作為與DXP/CMS/自定義應用程式整合的後端系統作為店面應用程式：

![Adobe Commerce無頭圖](../../assets/playbooks/integration-headless.svg)

整體式和無頭式的唯一區別是店面整合，這會影響用戶的體驗。 Adobe Commerce店面直接與第三方服務整合，無頭店則依靠自己的店面來定制和整合同一服務。 一些服務（如支付和單點登錄）需要店面和Adobe Commerce定制來完成整合流程。

## 第三方系統

一些熱門服務已經有了支援Adobe Commerce或熱門店面解決方案的擴展，如PWA Studio、Adobe Experience Manager和Vue Storefront，這些解決方案可以從其擴展市場或相關的第三方網站上找到。 即使沒有現有的延長，Adobe Commerce和其他無頭店面整合的努力也是類似的。 所有第三方服務通常都有文檔來解釋如何與它們整合。 這些服務只是一些例子；各國和市場可能有不同的選擇。

## 企業整合

對於企業系統整合（通常也稱為後端整合），業務資料流會受到影響。 根據不同的業務類型和需求，它可以使用我們已經介紹的三種不同的整合選項。

SKU、庫存和基本價格等產品必需資料通常來自ERP，而銷售價格通常由每個銷售渠道(例如Adobe Commerce)或CPQ（B2B或私人銷售）管理。 由於產品強制資料（庫存除外）不會經常更改，因此最佳做法是通過REST API或批量檔案導入使用計畫的批更新。 對於庫存，最佳做法是每天對與不同銷售渠道共用的產品庫存進行完整更新，以避免過度銷售。 此外，在24小時內對ERP進行增量更改。

產品目錄、元資料和營銷內容可以由每個銷售渠道(例如，Adobe Commerce)或中央PIM單獨管理。 由於元資料也不經常更改，因此最佳做法是通過REST API或批量檔案導入使用計畫的批更新。

訂單資料包括訂單、報價(B2B)、發運、退貨和交換資料，這些資料通常從集中的OMS和WMS系統中管理。 訂單資料應盡快同步，因此REST API通常是最佳選項。 為獲得更好的效能，請考慮減少API調用數。 對於訂單狀態、發運、退貨和交換資料，請考慮在小時或分鐘內計畫REST批更新API。

B2B資料通常從集中式CRM中管理。 即時API用於驗證現有客戶和建立新客戶。 對於B2B，可能需要引入更多API來同步Adobe Commerce與CRM或CPQ之間的不同公司員工、組和價目表。

還有一些其他系統整合，如eDM用於電子郵件營銷和業務資料分析的業務智慧，這些整合通常通過REST API或檔案導出/導入（通常由現有擴展支援）來完成。
