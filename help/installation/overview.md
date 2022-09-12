---
title: 內部部署安裝概述
description: 了解Adobe Commerce和Magento Open Source的內部部署安裝程式。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---


# 內部部署安裝概述

>[!NOTE]
>
>下圖提供 _**內部**_ Adobe Commerce和Magento Open Source的安裝：

![安裝如何運作](../assets/installation/install-diagram-24.svg)

一般安裝流程如下：

1. 設定您的伺服器環境。

   安裝必備軟體，包括PHP、Apache、MySQL和搜索引擎。 請參閱 [系統需求](system-requirements.md) 以取得更多資訊。

1. 取得 [驗證金鑰](prerequisites/authentication-keys.md) 至商務撰寫器存放庫。

1. 取得Adobe Commerce或Magento Open Source軟體。

   * （建議）取得 [撰寫器暗語](composer.md) 管理模組及其相依性。

   * 如果您想要貢獻Magento Open Source程式碼基底或自訂應用程式， [克隆](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) GitHub存放庫。 此方法需要熟悉GitHub和撰寫器。

1. 使用命令行安裝應用程式。

   如果步驟因未正確設定先決條件軟體而失敗，請檢閱 [必要條件](prerequisites/overview.md).

1. [驗證](next-steps/verify.md) 檢視您的店面和管理員以進行安裝。

