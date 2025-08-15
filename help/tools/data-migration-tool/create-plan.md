---
title: 建立資料移轉計畫
description: 請依照下列步驟建立資料移轉計畫，以確保成功從Magento 1升級至Magento 2。
exl-id: a14237f3-c5fe-4f5f-86eb-ed4c39507bff
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 0%

---

# 建立資料移轉計畫

若要成功移轉並避免問題，您必須徹底規劃和測試移轉。

## 開始之前：請考慮升級

移轉是進行重大變更的絕佳時機，可讓您的網站準備好迎接下一層級的增長。 請思考您的新站台是需要設計更多硬體，還是需要更進階的拓撲，以及更優異的快取階層。

## 步驟1：檢閱目前網站上的擴充功能

* 您已安裝哪些擴充功能？

* 您是否確定新網站上是否需要所有這些擴充功能？ 可能有您可以安全移除的舊專案。

* 您是否確定您是否有擴充功能的Magento 2版本？ 請造訪[Commerce Marketplace]以尋找最新版本，或連絡您的擴充功能提供者。

* 您要移轉擴充功能中的哪些資料庫資產？

## 步驟2：建立並準備您的存放區以進行移轉

* 使用至少符合您現有Magento 1系統的拓撲和設計，設定Magento 2硬體系統

* 在符合[!DNL Data Migration Tool]系統需求[的系統上安裝Magento 2.x （包含此版本的所有模組）和](../../installation/system-requirements.md)

* 對[!DNL Data Migration Tool]程式碼進行自訂調整，以備您不需要移轉部分資料(如CMS Pages、Sales Rules)或想要在移轉期間轉換Magento自訂。 閱讀[!DNL Data Migration Tool]的[技術規格](technical-specification.md)，深入瞭解從內部移轉的運作方式

## 步驟3：試用

在生產環境中開始移轉之前，最好在測試環境中完成所有移轉步驟。

在此等移轉測試中，請遵循下列步驟：

* 將您的Magento 1存放區複製到暫存伺服器

* 將複製的Magento 1存放區完全移轉至Magento 2

* 徹底測試您的新商店

## 步驟4：開始移轉

1. 請確定[!DNL Data Migration Tool]具有網路存取權，可連線至Magento 1和Magento 2資料庫。 開啟防火牆中對應的連線埠。

1. 停止「Magento 1.x管理面板」中的所有活動（訂單管理除外），例如出貨、建立商業發票及銷退折讓單。 可調整[!DNL Data Migration Tool]中Delta模式的設定，以擴充允許的活動清單。

   >[!NOTE]
   >
   >在Magento 2商店上線之前，請勿繼續這些活動。

1. 我們建議您停止所有Magento 1.x cron工作。

   不過，如果移轉期間需要執行某些工作，請確定它們不會建立新的資料庫實體，或變更現有實體，使得差異模式無法處理這些實體。

   例如，`enterprise_salesarchive_archive_orders` cron工作會移動要封存的舊訂單。 在移轉期間執行此作業是安全的，因為Delta模式可辨識此作業，並正確處理已封存的訂單。

1. 使用[!DNL Data Migration Tool]移轉設定和網站。

1. 將您的Magento 1.x媒體檔案複製到Magento 2.x。

   您必須手動將這些檔案從`magento1-root/media`目錄複製到`magento2-root/pub/media`。

1. 使用[!DNL Data Migration Tool]將資料從Magento 1資料庫大量複製到Magento 2資料庫。

   如果部分擴充功能含有您要移轉的資料，您可能需要安裝這些適用於Magento 2的擴充功能。 如果擴充功能在Magento 2資料庫中有不同的結構，請使用[!DNL Data Migration Tool]提供的對應檔案。

1. 重新索引所有Magento 2.x索引子。 如需詳細資訊，請參閱[設定指南](../../configuration/cli/manage-indexers.md)中的&#x200B;_管理索引子_。

## 步驟5：視需要對移轉的資料進行變更

有時候，您可能想要讓Magento 2商店在移轉後提供不同的目錄結構、銷售規則和CMS頁面。

進行手動資料變更時，請務必謹慎操作。 錯誤會在後續的增量資料移轉步驟中建立錯誤。

例如，從Magento 2刪除的產品：已在即時Magento 1商店中購買且在您的Magento 2商店中無法再使用的產品。 在差異模式下執行[!DNL Data Migration Tool]時，傳輸有關此類購買的資料可能會導致錯誤。

## 步驟6：更新增量資料

在移轉資料後，您必須以增量方式擷取已在Magento 1存放區中新增的資料更新（例如新訂單、評論和客戶設定檔中的變更），並使用差異模式將這些更新傳輸到Magento 2存放區。

* 開始漸進式移轉；更新會持續執行。 您可以隨時按`Ctrl+C`來停止傳送更新。

* 在此期間，請測試您的Magento 2網站，以儘快發現任何問題。 如果發生問題，請按`Ctrl+C`停止累加移轉，並在解決問題後重新啟動。

>[!NOTE]
>
>如果您同時執行Magento 2網站測試及移轉程式，可能會出現大量檢查警告。 發生這種情況是因為在Magento 2中，您會建立在Magento 1例項中不存在的實體。

## 步驟7：上線

現在您的Magento 2網站已與Magento 1保持同步且正常運作，請執行以下動作以切換至新網站：

1. 將Magento 1系統置於維護模式（停機時間開始）。

1. 在移轉工具命令視窗中按下Control+C以停止增量更新。

1. 開始您的Magento 2 cron工作。

1. 在您的Magento 2系統中，重新索引股票索引器。 如需詳細資訊，請參閱[設定指南]。

1. 使用您選擇的工具，在Magento 2系統中點選頁面，以便在客戶使用您的店面之前快取頁面。

1. 對您的Magento 2網站執行任何最終驗證。

1. 變更DNS、負載平衡器等，以指向新的生產硬體(DOWNTIME ENDS)。

1. Magento 2商店現已準備就緒，可供使用。 您和您的客戶可以繼續所有活動。

<!-- LINK ADDRESSES -->

[Commerce Marketplace]: https://marketplace.magento.com
