---
title: 本地安裝概述
description: 瞭解Adobe Commerce和Magento Open Source的內部部署安裝過程。
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# 本地安裝概述

>[!NOTE]
>
>下圖提供了對 _**本地**_ Adobe Commerce和Magento Open Source安裝：

![安裝的工作原理](../assets/installation/install-diagram-24.svg)

一般安裝流程如下：

1. 設定伺服器環境。

   安裝必備軟體，包括PHP、Apache、MySQL和搜索引擎。 查看 [系統要求](system-requirements.md) 的子菜單。

1. 獲取 [身份驗證密鑰](prerequisites/authentication-keys.md) 到Commerce Composer儲存庫。

1. 獲取Adobe Commerce或Magento Open Source軟體。

   * （推薦）獲取 [作曲家集合](composer.md) 管理模組及其依賴關係。

   * 如果要為Magento Open Source代碼庫或自定義應用程式， [克隆](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) GitHub儲存庫。 此方法需要熟悉GitHub和Composer。

1. 使用命令行安裝應用程式。

   如果步驟因未正確設定必備軟體而失敗，請查看 [先決條件](prerequisites/overview.md)。

1. [驗證](next-steps/verify.md) 通過查看您的店面和管理員進行安裝。
