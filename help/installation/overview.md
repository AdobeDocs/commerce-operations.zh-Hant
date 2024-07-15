---
title: 內部部署安裝概述
description: 了解 Adobe Commerce 內部部署的安裝程序。
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 7%

---

# 內部部署安裝概述

>[!NOTE]
>
>下圖提供Adobe Commerce中&#x200B;_**內部部署**_&#x200B;安裝的高階概觀：

![安裝的運作方式](../assets/installation/install-diagram-24.svg)

一般安裝流程如下：

1. 設定您的伺服器環境。

   安裝先決條件軟體，包括PHP、Apache、MySQL和搜尋引擎。 如需詳細資訊，請參閱[系統需求](system-requirements.md)。

1. 取得Commerce Composer存放庫的[驗證金鑰](prerequisites/authentication-keys.md)。

1. 取得Adobe Commerce軟體。

   * （建議）取得[Composer中繼套件](composer.md)以管理模組及其相依性。

   * 如果您想要貢獻Magento Open Source程式碼基底或自訂應用程式，請[複製](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) GitHub存放庫。 此方法需要同時熟悉GitHub和Composer。

1. 使用命令列安裝應用程式。

   如果步驟因未正確設定先決條件軟體而失敗，請檢閱[先決條件](prerequisites/overview.md)。

1. [檢視您的店面和管理員，以驗證](next-steps/verify.md)安裝。
