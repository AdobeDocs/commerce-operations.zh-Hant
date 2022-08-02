---
title: 拆分資料庫效能解決方案
description: 閱讀有關Adobe Commerce和Magento Open Source的拆分資料庫解決方案。
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---


# 拆分資料庫解決方案概述

{#ee-only}

{{deprecate-split-db}}

Adobe Commerce提供了幾項可擴充性優勢，包括能夠為Commerce應用程式的不同功能區使用三個獨立的主資料庫。

簽出、訂單和產品資料都可以使用單獨的主資料庫，您可以選擇複製該主資料庫。 此分離可根據您的需要獨立擴展從網站簽出、訂單管理活動、網站瀏覽和促銷活動中的負載。 這些更改在如何擴展資料庫層方面提供了相當大的靈活性。

>[!INFO]
>
>Adobe Commerce在雲基礎架構方面 _不_ 支援此功能。

的 `ResourceConnections` 類提供到Commerce應用程式的統一MySQL資料庫連接。 對於主資料庫的查詢，我們實現了命令查詢責任分離(CQRS)資料庫模式。 此模式處理將讀和寫查詢路由到相應資料庫的邏輯。 開發人員不需要知道正在使用哪種配置，也沒有單獨的讀和寫資料庫連接。

如果設定了可選的資料庫複製，您將獲得以下優勢：

- 資料備份
- 資料分析而不影響主資料庫
- 可擴充性

MySQL資料庫非同步複製，這意味著從屬資料庫不需要永久連接來從主資料庫接收更新。

下圖顯示了此功能的工作原理。

![Adobe Commerce使用不同的資料庫儲存表](../../assets/configuration/split-db-diagram-ee.png)

在Magento Open Source中，僅使用一個主資料庫。

Adobe Commerce使用三個主資料庫和可配置數量的從資料庫進行複製。 Adobe Commerce有一個用於資料庫連接的單一介面，因此效能更快，可擴充性更好。

## 配置選項

由於剝離資料庫效能解決方案的設計方式，您的自定義代碼和安裝的元件 _不能_ 執行下列任何操作：

- 直接寫入資料庫(而必須使用Adobe Commerce資料庫介面)
- 使用影響銷售或 [報價](https://glossary.magento.com/quote) 資料庫
- 在簽出、銷售或主資料庫中使用表的外鍵

>[!WARNING]
>
>與元件開發人員聯繫，以驗證其元件是否執行前面的任何操作。 如果是，則只能選擇以下選項之一：
>
>- 請元件開發人員更新其元件。
>- 按原樣使用元件 _無_ 拆分資料庫解決方案。
>- 刪除元件，以便您可以使用拆分資料庫解決方案。


這也意味著您可以：

- 配置剝離資料庫解決方案 _先_ 把商業投入生產。

   Adobe建議在安裝Commerce軟體後盡快配置剝離資料庫。

- [手動配置](multi-master-manual.md) 拆分資料庫解決方案。

   如果已安裝元件或Commerce已在生產中，則必須執行此任務。 (_不要_ 更新生產系統；在開發系統中進行更新，並在測試更改後同步更改。)

   >[!WARNING]
   >
   >必須手動備份另外兩個資料庫實例。 Commerce只備份主資料庫實例。 的 [`magento setup:backup --db`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html) 命令和管理選項不備份其他表。

## 先決條件

拆分資料庫要求您在任何主機上設定三個MySQL主資料庫（Commerce伺服器上的所有三個資料庫、單獨伺服器上的每個資料庫，等等）。 這些是 _主_ 資料庫，其使用方式如下：

- 一個主資料庫 [簽出](https://glossary.magento.com/checkout) 表
- 一個用於銷售表的主資料庫(也稱為 _訂單管理系統_&#x200B;或 _OMS_，表格
- Commerce 2應用程式表其餘部分的一個主資料庫

此外，您還可以選擇設定任意數量的 _從_ 用作負載平衡器和備份的資料庫。

本指南討論如何僅設定主資料庫。 如果您願意，我們將提供設定從資料庫的示例配置和參考。

在本指南中，三個主資料庫命名為：

- `magento_quote`
- `magento_sales`
- `magento`

（您可以為資料庫命名任何您想要的名稱。）
