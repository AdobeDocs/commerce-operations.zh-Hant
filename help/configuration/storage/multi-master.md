---
title: 分割資料庫效能解決方案
description: 閱讀Adobe Commerce的分割資料庫解決方案。
recommendations: noCatalog
exl-id: 922a9af7-2c46-4bf3-b1ad-d966f5564ec0
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# 分割資料庫解決方案概觀

{{ee-only}}

{{deprecate-split-db}}

Adobe Commerce提供數個擴充性優勢，包括能夠針對Commerce應用程式的不同功能區域使用三個不同的主資料庫。

結帳、訂購和產品資料都可以使用個別的master資料庫，您可以選擇複製這些資料庫。 此分離會根據您的需求，獨立調整網站結帳、訂單管理活動、網站瀏覽和銷售活動的負載。 這些變更在如何擴充資料庫層級方面提供了相當大的彈性。

>[!INFO]
>
>雲端基礎結構上的Adobe Commerce _不_&#x200B;支援此功能。

`ResourceConnections`類別提供與Commerce應用程式的統一MySQL資料庫連線。 針對主要資料庫的查詢，我們實作命令查詢職責劃分(CQRS)資料庫模式。 此模式會處理將讀取和寫入查詢路由到適當資料庫的邏輯。 開發人員不需要知道使用的是哪個設定，而且沒有單獨的讀取和寫入資料庫連線。

如果您設定可選的資料庫複製，您會獲得下列優點：

- 資料備份
- 在不影響master資料庫的情況下進行資料分析
- 擴充性

MySQL資料庫會以非同步方式復寫，這表示從屬端不需要永久連線，即可接收主端的更新。

下圖說明此功能的運作方式。

![Adobe Commerce使用不同的資料庫來儲存資料表](../../assets/configuration/split-db-diagram-ee.png)

在Magento Open Source中，僅使用一個master資料庫。

Adobe Commerce使用三個主要資料庫和可供設定的從屬資料庫數量進行複製。 Adobe Commerce提供單一介面用於資料庫連線，因此可加快效能並提升擴充能力。

## 設定選項

因為分割資料庫效能解決方案的設計方式，您的自訂程式碼和已安裝的元件&#x200B;_無法_&#x200B;執行下列任一動作：

- 直接寫入資料庫(您必須改用Adobe Commerce資料庫介面)
- 使用影響銷售或報價資料庫的JOIN
- 在簽出、銷售或主要資料庫中使用資料表的外部索引鍵

>[!WARNING]
>
>請聯絡元件開發人員以確認其元件是否執行前述任何操作。 若是如此，您只能選擇下列其中一項：
>
>- 要求元件開發人員更新其元件。
>- 依原樣&#x200B;_使用元件，但不使用_&#x200B;分割資料庫解決方案。
>- 移除元件，以便使用分割資料庫解決方案。

這也表示您可以：

- 在將Commerce投入生產之前&#x200B;_設定分割資料庫解決方案_。

  Adobe建議您在安裝Commerce軟體後，儘快設定分割資料庫。

- [手動設定](multi-master-manual.md)分割資料庫解決方案。

  如果您已安裝元件，或Commerce已在生產環境中，則必須執行此工作。 （_不要_&#x200B;更新生產系統；在開發系統中進行更新，並在您測試變更之後同步化變更。）

  >[!WARNING]
  >
  >您必須手動備份另外兩個資料庫執行處理。 Commerce僅備份主要資料庫執行個體。 [`magento setup:backup --db`](../../installation/tutorials/backup.md)命令和Admin選項不會備份其他表格。

## 必要條件

分割資料庫需要您在任一主機上設定三個MySQL master資料庫(全部三個Commerce伺服器上，每個資料庫在個別伺服器上，依此類推)。 這些是&#x200B;_master_&#x200B;資料庫，使用方式如下：

- 一個用於簽出表格的主資料庫
- 一個銷售資料表(也稱為&#x200B;_Order Management System_&#x200B;或&#x200B;_OMS_&#x200B;資料表)的主資料庫
- 一個用於Commerce 2應用程式表格的其餘主要資料庫

此外，您可以選擇設定任何數目的&#x200B;_從屬_&#x200B;資料庫，做為負載平衡器和備份。

本指南僅討論如何設定主資料庫。 我們提供範例組態和參考，供您視需要設定從屬資料庫。

在本指南中，三個主要資料庫命名為：

- `magento_quote`
- `magento_sales`
- `magento`

（您可以隨意命名資料庫。）
