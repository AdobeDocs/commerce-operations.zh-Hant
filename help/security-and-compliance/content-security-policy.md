---
title: 內容安全策略概述
description: 瞭解如何使用內容安全策略改進Adobe Commerce或Magento Open Source儲存的安全狀態。
exl-id: 81070a09-5f8f-48b1-b542-1443dbd43f5f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# 內容安全策略概述

內容安全策略(CSP)可以通過幫助檢測和減少跨站點指令碼(XSS)和相關資料注入攻擊，為Adobe Commerce和Magento Open Source安裝提供額外的防禦層。 此常見攻擊向量通過注入惡意內容而起作用，這些惡意內容錯誤地聲稱來自網站。 在載入並執行惡意內容後，可以啟動未授權的資料傳輸。

CSP提供了一套標準指令，告訴瀏覽器哪些內容資源可以信任，哪些內容應被阻止。 使用精心定義的策略，CSP可以限制瀏覽器內容，以僅允許顯示白名單資源。

## 配置

為避免干擾站點操作，CSP可分階段實現。 CSP有兩種基本的操作模式： `report-only mode` 和 `restrict mode`。 Adobe Commerce公2.3.5的推出標誌著我們實施的第一階段，並使CSP在 `report-only mode` 預設值。 在未來的發行版中， `restrict mode` 預設情況下啟用附加的開箱保護。

**僅報告模式**:系統指示瀏覽器報告策略違規，但不強制執行這些違規。 每次請求的資源違反CSP時，瀏覽器都會將產生的錯誤記錄到控制台中。 然後，可以使用控制台日誌來調查每個違規的原因。

在CSP錯誤發生時檢查所有錯誤並細化策略，直到所有必要資源都白名列出。 切換到 `restrict mode` 不再發生錯誤時。 否則，配置不當的CSP可能會導致瀏覽器顯示一個空白頁面，並出現大量控制台錯誤。 正確配置的CSP允許提供白名單內容，而不會對效能產生任何明顯影響。

**限制模式**:系統指示瀏覽器強制實施所有內容策略並將發佈限制為白名單資源。 由於CSP是從伺服器而非管理員配置的，因此大多數商家需要系統整合商或開發人員的幫助才能正確配置。 請參閱 [內容安全策略](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) 的 _Commerce PHP擴展_ 的子菜單。

## 報告

預設情況下，CSP會向瀏覽器控制台發送錯誤，但可以配置為按HTTP請求收集錯誤日誌。 此外，您還可以使用幾個第三方服務來監視、收集和報告CSP違規。

[報告URI](https://report-uri.io/) 是監視CSP違規並在儀表板中顯示結果的服務。 無論是商家還是開發商，只要發生CSP違規，都可以使用該服務來接收報告。
