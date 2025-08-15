---
title: 內部部署安裝概述
description: 了解 Adobe Commerce 內部部署的安裝程序。
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: 7cc77a204d2a3c0773e6a0ab60e57e6e35f12091
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 3%

---


# 內部部署安裝概述

本頁提供在您自己的基礎架構上安裝Adobe Commerce的概觀。 安裝程式包括設定伺服器環境、取得必要的軟體與認證，以及執行安裝命令。

您可以在大約30到60分鐘內安裝Adobe Commerce軟體。 不過，安裝前設定伺服器環境所需的時間會因您的經驗及您選取的技術而異。

>[!TIP]
>
>您應該具備中級技術知識和伺服器存取權才能成功繼續。

安裝會建立功能齊全的Adobe Commerce商店，其中包含[客戶對面的店面](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/start/storefront/storefront)和[系統管理面板](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/start/admin/admin)。 在開始程式之前，您必須準備好您的資料庫認證、網域資訊和驗證金鑰。

## 工作流程

下圖說明為內部部署環境安裝Adobe Commerce的主要步驟：

![安裝的運作方式](../assets/installation/on-premises-install.drawio.svg)

### 設定您的伺服器環境

根據[必要條件](prerequisites/overview.md)安裝並設定PHP、Web伺服器、資料庫和搜尋引擎。

### 取得驗證金鑰

從Commerce Marketplace產生新的[驗證金鑰](prerequisites/authentication-keys.md) （或複製現有的金鑰），以存取Adobe Commerce Composer套件。

### 取得Adobe Commerce軟體

使用[Composer](prerequisites/commerce.md) （建議）下載或從GitHub複製以取得開發貢獻。

如果您想要參與Magento Open Source程式碼基底或自訂應用程式，請[複製](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) GitHub存放庫。 此方法需要同時熟悉GitHub和Composer。

### 安裝應用程式

使用您的特定組態執行安裝命令。 如需完整範例，請參閱[快速入門](composer.md)。

>[!NOTE]
>
>如果步驟因未正確設定先決條件軟體而失敗，請檢閱[先決條件](prerequisites/overview.md)。

### 驗證安裝

[測試](next-steps/verify.md)您的店面和管理面板，確保一切正常運作。

## 常見安裝問題

- **許可權錯誤**：請確定檔案系統擁有權和許可權正確
- **資料庫連線失敗**：驗證資料庫認證與網路連線
- **驗證金鑰錯誤**：確認您的Commerce Marketplace金鑰有效且有效
- **記憶體限制**：請確定足夠的PHP記憶體配置（建議至少2GB）
