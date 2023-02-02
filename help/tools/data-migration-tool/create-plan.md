---
title: 建立資料遷移計畫
description: 請依照下列步驟建立資料移轉計畫，以確保從Magento1成功升級至Magento2。
source-git-commit: 2e1a06b59fda7db4a9b32d000e1b2a3ca88926d3
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 0%

---


# 建立資料遷移計畫

若要成功移轉並避免問題，您必須徹底規劃並測試您的移轉。

## 開始之前：考慮升級

遷移是進行重大更改並為您的站點做好準備以迎接下一級增長的最佳時機。 請考慮是否需要使用更多硬體或更高級的拓撲來設計您的新站點，以及更好的快取層。

## 步驟1:檢閱目前網站上的擴充功能

* 您已安裝哪些擴充功能？

* 您是否已識別是否需要新網站上的所有這些擴充功能？ 也許有些老的你可以安全地移除。

* 您是否已決定您的擴充功能是否有Magento2版本？ 瀏覽 [Commerce Marketplace] 若要尋找最新版本，或聯絡您的擴充功能提供者。

* 您要移轉擴充功能中的哪些資料庫資產？

## 步驟2:建置並準備您的儲存以進行移轉

* 使用拓撲和設計來設定Magento2硬體系統，至少與現有Magento1系統匹配

* 安裝Magento2.x（包含此版本的所有模組）和 [!DNL Data Migration Tool] 在符合 [系統需求](../../installation/system-requirements.md)

* 對 [!DNL Data Migration Tool] 代碼，以備您不需要遷移某些資料（如CMS頁面、銷售規則），或想在遷移期間轉換Magento自定義。 閱讀 [!DNL Data Migration Tool]&#39;s [技術規範](technical-specification.md) 更清楚了解移轉如何從內部

## 步驟3:乾跑

最好在您開始在生產環境中進行移轉之前，先在您的測試環境中執行所有移轉步驟。

在這些移轉測試中，請遵循下列步驟：

* 將Magento1儲存複製到中繼伺服器

* 將複製的Magento1儲存完全遷移到Magento2

* 徹底測試您的新商店

## 步驟4:開始移轉

1. 請確定 [!DNL Data Migration Tool] 具有連接到Magento1和Magento2資料庫的網路訪問權限。 在防火牆中開啟對應的埠。

1. 在「Magento1.x管理面板」（訂單管理除外）中停止所有活動，如發運、建立發票和貸項通知單。 可借由調整 [!DNL Data Migration Tool].

   >[!NOTE]
   >
   >在Magento2商店上線前，您不得繼續這些活動。

1. 建議停止所有Magento1.x cron作業。

   不過，如果遷移期間需要運行某些作業，請確保它們不建立新的資料庫實體，或更改現有的資料庫實體，使這些實體無法通過增量模式進行處理。

   例如， `enterprise_salesarchive_archive_orders` cron作業將舊訂單移至存檔。 在遷移期間運行此作業是安全的，因為增量模式可識別此作業並正確處理歸檔訂單。

1. 使用 [!DNL Data Migration Tool] 移轉設定和網站。

1. 將Magento1.x媒體檔案複製到Magento2.x。

   您必須從 `magento1-root/media` 目錄 `magento2-root/pub/media`.

1. 使用 [!DNL Data Migration Tool] 將資料從Magento1資料庫批量複製到Magento2資料庫。

   如果您的某些擴充功能有您要移轉的資料，則可能需要安裝這些適合Magento2的擴充功能。 如果擴充功能在Magento2資料庫中具有不同結構，請使用隨 [!DNL Data Migration Tool].

1. 重新索引所有Magento2.x索引器。 如需詳細資訊，請參閱 [管理索引器](../../configuration/cli/manage-indexers.md) 在 _設定指南_.

## 步驟5:對移轉的資料進行變更（如有需要）

有時候，遷移後，您可能會想要讓Magento2儲存區具有不同的目錄結構、銷售規則和CMS頁面。

在處理手動資料變更時，務必謹慎處理。 錯誤會在後續的增量資料移轉步驟中造成錯誤。

例如，從Magento2中刪除的產品：已在即時Magento1商店購買，且在Magento2商店中已無法再使用的。 傳輸此類購買的相關資料在執行 [!DNL Data Migration Tool] 在增量模式。

## 步驟6:更新增量資料

移轉資料後，您必須逐步擷取已新增至Magento1存放區的資料更新（例如新訂單、審核和客戶設定檔中的變更），並使用增量模式將這些更新傳輸至Magento2存放區。

* 啟動增量遷移；更新會持續執行。 您可以隨時按下以停止傳輸更新 `Ctrl+C`.

* 在此期間測試您的Magento2網站，以盡快找到任何問題。 遇到問題時按 `Ctrl+C` 要停止增量遷移，並在解決問題後重新啟動。

>[!NOTE]
>
>如果您對Magento2網站進行測試，並同時執行移轉程式，可能會出現大量檢查警告。 這會發生，因為在Magento2中，您建立了Magento1例項中不存在的實體。

## 步驟7:上線

現在，您的Magento2網站已與Magento1保持最新且正常運作，請執行下列操作以切換至新網站：

1. 將Magento1系統置於維護模式（停機開始）。

1. 在遷移工具命令窗口中按Control+C以停止增量更新。

1. 啟動Magento2 cron作業。

1. 在Magento2系統中，重新索引股票索引器。 如需詳細資訊，請參閱 [設定指南].

1. 使用您所選擇的工具，在Magento2系統中的頁面快取頁面，然後再使用您店面的客戶。

1. 對Magento2站點執行任何最終驗證。

1. 將DNS、負載平衡器等更改為指向新的生產硬體（停機結束）。

1. Magento2商店現已可供使用。 您和您的客戶可以繼續所有活動。

<!-- LINK ADDRESSES -->

[Commerce Marketplace]: https://marketplace.magento.com
