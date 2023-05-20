---
title: 建立資料遷移計畫
description: 按照以下步驟建立資料遷移計畫，以確保成功從Magento1升級到Magento2。
exl-id: a14237f3-c5fe-4f5f-86eb-ed4c39507bff
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 0%

---

# 建立資料遷移計畫

要成功遷移並避免問題，您需要徹底規劃和test遷移。

## 開始前：考慮升級

遷移是進行認真更改並讓您的站點準備好迎接下一級增長的完美時刻。 考慮是否需要使用更多硬體設計新站點，還是需要使用更高級的拓撲來設計更好的快取層。

## 步驟1:查看當前站點上的擴展

* 您安裝了哪些擴展？

* 您是否確定是否需要新站點上的所有這些擴展？ 可能有些舊的，你可以安全地移除。

* 是否確定是否存在Magento2版的擴展？ 訪問 [Commerce Marketplace] 查找最新版本，或與擴展提供商聯繫。

* 您要遷移擴展中的哪些資料庫資產？

## 步驟2:構建並準備儲存以進行遷移

* 使用拓撲和設計設定至少與現有Magento1系統匹配的Magento2硬體系統

* 安裝Magento2.x（包含此版本的所有模組）和 [!DNL Data Migration Tool] 在一個符合 [系統要求](../../installation/system-requirements.md)

* 對 [!DNL Data Migration Tool] 代碼，以防您不需要遷移某些資料（如CMS頁、銷售規則）或在遷移期間轉換Magento定制。 閱讀 [!DNL Data Migration Tool]`s [技術規格](technical-specification.md) 更好地瞭解遷移是如何從內部

## 第3步：乾跑

在生產環境上開始遷移之前，最好先完成測試環境上的所有遷移步驟。

在此類遷移測試中，請執行以下步驟：

* 將Magento1儲存複製到登台伺服器

* 將複製的Magento1儲存完全遷移到Magento2

* 徹底test新商店

## 第4步：開始遷移

1. 確保 [!DNL Data Migration Tool] 具有連接到Magento1和Magento2資料庫的網路訪問權限。 開啟防火牆中的相應埠。

1. 停止Magento1.x管理面板中的所有活動（訂單管理除外），例如發運、建立發票和貸項通知單。 通過調整「增量」模式的設定，可以擴展允許的活動清單 [!DNL Data Migration Tool]。

   >[!NOTE]
   >
   >在您的Magento2商店投入使用之前，不能繼續這些活動。

1. 建議停止所有Magento1.x cron作業。

   不過，如果遷移期間需要運行某些作業，請確保它們不會建立新資料庫實體或更改現有資料庫實體，而這些實體無法通過增量模式進行處理。

   例如， `enterprise_salesarchive_archive_orders` cron作業將舊訂單移至存檔。 在遷移期間運行此作業是安全的，因為增量模式可識別此作業並正確處理歸檔訂單。

1. 使用 [!DNL Data Migration Tool] 遷移設定和網站。

1. 將Magento1.x媒體檔案複製到Magento2.x。

   您必須從 `magento1-root/media` 目錄 `magento2-root/pub/media`。

1. 使用 [!DNL Data Migration Tool] 將資料從Magento1資料庫批量複製到Magento2資料庫。

   如果某些擴展包含要遷移的資料，則可能需要安裝適合Magento2的擴展。 如果擴展在Magento2資料庫中具有不同結構，請使用隨 [!DNL Data Migration Tool]。

1. 重新索引所有Magento2.x索引器。 有關詳細資訊，請參閱 [管理索引器](../../configuration/cli/manage-indexers.md) 的 _配置指南_。

## 第5步：對遷移的資料進行更改（如果需要）

有時，您可能希望在遷移後讓Magento2儲存具有不同的目錄結構、銷售規則和CMS頁面。

在手動更改資料時，必須謹慎行事。 錯誤會在後續的增量資料遷移步驟中產生錯誤。

例如，從Magento2中刪除的產品：在您的即時Magento1商店中購買的，在您的Magento2商店中不再可用。 傳輸有關此類採購的資料可能會在運行 [!DNL Data Migration Tool] 的雙曲餘切值。

## 步驟6:更新增量資料

遷移資料後，您必須增量捕獲已添加到Magento1儲存中的資料更新（如新訂單、審閱和客戶配置檔案的更改），並使用增量模式將這些更新傳輸到Magento2儲存。

* 啟動增量遷移；更新會持續運行。 您可以通過按鍵隨時停止傳輸更新 `Ctrl+C`。

* 在此期間test您的Magento2站點，以盡快捕獲任何問題。 遇到問題，按 `Ctrl+C` 停止增量遷移並在解決問題後重新啟動。

>[!NOTE]
>
>如果您對Magento2站點進行測試並同時運行遷移過程，則可能會出現卷檢查警告。 這是因為在Magento2中，您建立了Magento1實例中不存在的實體。

## 第7步：上線

現在，您的Magento2站點已與Magento1保持最新，並且正常工作，請執行以下操作以切換到新站點：

1. 將Magento1系統置於維護模式(DOWNTIME STARTS)。

1. 在遷移工具命令窗口中按Ctrl+C可停止增量更新。

1. 開始Magento2cron作業。

1. 在Magento2系統中，重新為股票索引器編製索引。 有關詳細資訊，請參見 [配置指南]。

1. 使用您選擇的工具，在Magento2系統中按頁以在使用您店面的客戶之前快取頁。

1. 對Magento2站點執行任何最終驗證。

1. 更改DNS、負載平衡器等，以指向新的生產硬體(DOWNTIME ENDS)。

1. Magento2商店現在可以使用。 您和您的客戶可以恢復所有活動。

<!-- LINK ADDRESSES -->

[Commerce Marketplace]: https://marketplace.magento.com
