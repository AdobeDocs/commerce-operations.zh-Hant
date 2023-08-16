---
title: Adobe Commerce整合選項
description: 探索將其他系統與Adobe Commerce實作整合的選項。
exl-id: 10de70d2-ff3b-4f10-b370-01d805b745dc
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# 典型的整合點和資料流程

整合和資料流程有兩個主要方法，它們非常類似，但有一個主要差異。

## 整體式

下圖說明將Adobe Commerce同時用作後端系統和店面應用程式的整體方法：

![Adobe Commerce整體圖表](../../assets/playbooks/integration-monolith.svg)

## Headless

下圖說明使用Adobe Commerce作為後端系統，並與DXP/CMS/自訂應用程式整合作為店面應用程式的Headless方法：

![Adobe Commerce headless圖表](../../assets/playbooks/integration-headless.svg)

整體式與Headless方法的唯一差異在於店面整合，這會影響客戶的使用體驗。 Monolithic會直接使用Adobe Commerce店面與協力廠商服務整合，而Headless則需仰賴店面來自訂與整合相同的服務。 某些服務(如付款和單一登入(SSO))需要同時自訂店面和Adobe Commerce才能完成整合流程。

## 協力廠商系統

部分熱門服務已有絕佳擴充功能可支援Adobe Commerce或PWA Studio、Adobe Experience Manager和Vue Storefront等熱門店面解決方案（可從其擴充功能市集或相關協力廠商網站取得）。 即使沒有現有的擴充功能，實作Adobe Commerce與其他Headless店面之間整合的工作也類似。 所有協力廠商服務通常都有檔案可說明如何與整合。 這些服務只是一些範例；不同的國家和市場可能有不同的選擇。

## 企業整合

對於通常也稱為後端整合的企業系統整合，會影響業務資料流程。 根據不同的業務型別和需求，它可以使用三種不同的整合選項，我們之前已匯入此選項。

SKU、庫存和基本價格等產品強制資料通常來自ERP，而銷售價格通常由每個銷售管道(例如Adobe Commerce)或CPQ （B2B或私人銷售）管理。 由於產品強制資料（庫存除外）不會經常變更，因此最佳實務是透過REST API或大量檔案匯入使用已排程的批次更新。 對於詳細目錄，最佳實務是每天完整更新與不同銷售管道共用的產品詳細目錄，以避免過度銷售。 此外，請在24小時內排程從ERP進行遞增變更。

產品目錄、中繼資料和行銷內容可由每個銷售管道(例如Adobe Commerce)或中央PIM分別管理。 由於中繼資料也不會經常變更，因此最佳實務是透過REST API或大量檔案匯入使用已排程的批次更新。

訂單資料包括訂單、報價(B2B)、出貨、退貨及交換資料，通常由集中式OMS與WMS系統管理。 訂單資料應儘快同步，因此REST API通常是最佳選項。 為獲得更好的效能，請考慮減少API呼叫的數量。 針對訂單狀態、出貨、退貨及交換資料，請考慮以小時或分鐘為單位排程REST批次更新API。

B2B資料通常是透過集中式CRM來管理。 即時API可用來驗證現有客戶並建立新客戶。 針對B2B，您可能需要引入更多API，以便在Adobe Commerce與您的CRM或CPQ之間同步不同的公司員工、群組和價目表。

還有其他系統整合，例如用於電子郵件行銷的eDM和用於商業資料分析的商業智慧，通常透過REST API或檔案匯出/匯入（通常由現有擴充功能支援）完成。
