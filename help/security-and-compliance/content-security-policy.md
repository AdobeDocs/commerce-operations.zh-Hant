---
title: 內容安全性原則概觀
description: 瞭解如何使用內容安全性原則來改善Adobe Commerce存放區的安全性狀態。
exl-id: 81070a09-5f8f-48b1-b542-1443dbd43f5f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# 內容安全性原則概觀

內容安全性原則(CSP)可協助偵測及緩解跨網站指令碼(XSS)和相關資料插入攻擊，為Adobe Commerce安裝提供額外的防禦層。 這個常見的攻擊向量是透過插入惡意內容來運作，這些內容會不實地聲稱來自網站。 惡意內容載入並執行後，可能會起始未經授權的資料傳輸。

CSP提供一組標準化的指示，告訴瀏覽器哪些內容資源可以信任，哪些應該封鎖。 使用謹慎定義的原則，CSP可以限制瀏覽器內容，使其只允許列入白名單的資源顯示。

## 設定

為避免干擾網站作業，CSP可分階段實施。 CSP有兩個基本操作模式： `report-only mode`和`restrict mode`。

**僅報告模式**：指示瀏覽器報告原則違規，但不強制執行。 每次請求的資源違反CSP時，瀏覽器都會將產生的錯誤記錄到主控台。 然後可以使用主控台記錄來調查每個違規的原因。

請務必檢閱所有CSP錯誤，並調整原則，直到所有必要資源都列入白名單為止。 當沒有其他錯誤發生時，切換至`restrict mode`是安全的。 否則，未妥善設定的CSP可能會導致瀏覽器顯示含有大量主控台錯誤的空白頁面。 正確設定的CSP可傳送列入白名單的內容，而不會對效能造成任何影響。

**限制模式**：指示瀏覽器強制執行所有內容原則，並將發佈限制在白名單上的資源。

Adobe Commerce CSP實作的第一個階段已在Adobe Commerce 2.3.5中推出，並依預設在`report-only mode`中提供CSP。  在Adobe Commerce 2.4.7及更新版本中，CSP預設會針對店面和管理區域中的付款頁面設定為`restrict-mode`，而針對所有其他頁面則設定為`report-only`模式。 對應的CSP標頭在付款頁面的`script-src`指示詞內未包含`unsafe-inline`關鍵字。 此外，只允許列入白名單的內嵌指令碼。

由於CSP是從伺服器（而非管理員）設定，因此大多數商家需要系統整合商或開發人員的協助才能正確設定。 請參閱&#x200B;_Commerce PHP開發人員指南_&#x200B;中的[內容安全性原則](https://developer.adobe.com/commerce/php/development/security/content-security-policies/)。


## 報告

依預設，CSP會將錯誤傳送至瀏覽器主控台，但可設定為透過HTTP要求收集錯誤記錄。 此外，您有數個第三方服務可用來監視、收集和報告CSP違規。 透過從管理員或自訂模組的`config.xml`檔案新增URI，可以將CSP違規報告至集合的端點。  請參閱&#x200B;_Commerce PHP擴充功能開發人員指南_&#x200B;中的[報表URI組態](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#report-uri-configuration)。

[報告URI](https://report-uri.io/)是一項監視CSP違規並在儀表板中顯示結果的服務。 商戶和開發人員都可以使用此服務，在發生CSP違規時接收報表。
