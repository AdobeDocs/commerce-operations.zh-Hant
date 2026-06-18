---
title: 雲端版本升級執行原則
description: 瞭解Adobe Commerce在雲端上的版本升級實作 — 為何Adobe會實作升級、實作日期、淘汰和必要的動作。 請參閱生命週期政策，了解轉換規定和移轉路徑。
nudge: false
source-git-commit: 797f067de451c8b1b4d735e82de66a3fd9b56563
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---


# 雲端上Adobe Commerce的版本升級執行原則

Adobe Commerce版本的一般支援和延伸支援結束時，Adobe保留在仍在執行不受支援版本的雲端環境上停用Adobe Commerce的權利。 版本升級強制執行僅適用於雲端環境上的Adobe Commerce ；內部部署客戶管理自己的基礎結構。

您必須移至支援的Adobe Commerce版本，或移轉至[!DNL Adobe Commerce as a Cloud Service]，發佈行的[延伸支援結束](lifecycle-policy.md#end-of-support-dates)日期之前。

以下章節說明為何Adobe會強制升級、如何計算強制日期，以及在強制日期會發生什麼事。 如需版本特定的執行日期，請參閱生命週期原則中的[支援結束日期](lifecycle-policy.md#end-of-support-dates)表格。

>[!NOTE]
>
>本主題僅涵蓋雲端升級實作。 如需支援層定義，[支援結束日期](lifecycle-policy.md#end-of-support-dates)表格、[僅限安全性轉換規定](lifecycle-policy.md#security-only-transitional-period)、[協力廠商軟體相依性](lifecycle-policy.md#platform-dependencies)、[PHP結束與PCI法規遵循](lifecycle-policy.md#php-end-of-life-and-pci-compliance)以及[升級與移轉選項](lifecycle-policy.md#upgrade-and-migration-options)，請參閱[生命週期原則](lifecycle-policy.md)。 除了升級至支援的Adobe Commerce版本外，Adobe還要求您在主動支援的版本上保留協力廠商軟體的相依性。

## Adobe為何要推出此政策

Adobe負責雲端客戶執行Adobe Commerce時託管平台基礎架構的安全性和合規性。 這包括讓所有基礎軟體相依性保持最新狀態、套用安全性修補程式，以及符合客戶所仰賴的法規標準（例如PCI）。

當供應商正式終止基礎軟體相依性的安全性支援時，Adobe將無法再提供必要的安全性涵蓋範圍和平台支援。 如果繼續在不支援的基礎建設上經營商店，客戶、購物者和Adobe將面臨無法接受的風險。 因此，Adobe將推出正式的版本升級執行原則，以定義何時將執行不支援Commerce版本的雲端環境上的Adobe Commerce解除委任。

## 如何計算升級執行日期

對於每個Adobe Commerce發行行，升級強制日期的計算方式如下：

**升級強制日期** =一般可用性日期+ 3年定期支援+最多1年延長支援

延長支援即將針對每個發行版本線宣佈終止定期支援。

## 在版本升級執行日期發生什麼情況

在發佈的升級強制日期，Adobe將停止維護仍在執行受影響發行版本的雲端環境上的所有Adobe Commerce，並保留解除其委任的權利。 您將會在版本升級執行日期之前的關鍵里程碑收到進階通知。 Adobe會在環境停用前提供資料匯出視窗，讓您擷取資料。

此原則下的第一個執行日期是&#x200B;**2027年6月1日**，針對在該日期之前達到延長支援結束的發行專案。 如需特定版本的強制日期，請參閱[支援結束日期](lifecycle-policy.md#end-of-support-dates)表格。
