---
title: 開發環境建議
description: 瞭解Adobe Commerce中的開發環境建議。 探索實作指引和最佳化策略。
exl-id: f57396c0-86be-4933-8066-eb51c42fb9e4
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%
---
# 開發環境建議

此頁面提供Commerce開發環境的建議。

## 清除快取而非停用

許多開發人員傾向於在其開發人員執行個體上停用所有快取。 我們建議只清除快取，不要停用所有快取。 當您[清除快取](../configuration/cli/manage-cache.md#clean-and-flush-cache-types)而不是完全停用它們時，[!DNL Commerce]會更有效率地執行。 大部分型別的快取在開發期間很少會失效。

如果您[停用快取](../configuration/cli/manage-cache.md#enable-or-disable-cache-types)，我們建議只在開發執行個體中停用頁面和封鎖快取。 請記得在測試期間啟用所有快取。

## 在開發模式中要避免的命令

在開發模式中，請勿執行編譯、程式碼產生和靜態內容部署的命令。 這些指令是專為生產模式而建置的。

**請勿在開發模式中執行**&#x200B;生產命令：

* `setup:di:compile`會產生自動產生的類別和最佳化的設定快取。

  ```shell
  bin/magento setup:di:compile
  ```

  在開發模式中，Magento會隨選執行產生功能；您不需要執行此功能。 如果您修改了類別的簽章，而且需要重新產生其自動產生的`factories/proxies/interceptors`，請移除這些類別或&#x200B;_產生的_&#x200B;資料夾。

* `setup:static-content:deploy`為存放區部署靜態內容。

  ```shell
  bin/magento setup:static-content:deploy
  ```

  在開發模式中，Magento會隨選執行；您不需要執行。

## 虛擬機器器上的正常頁面載入時間

如果您在VM上進行開發，且載入Magento頁面需要超過2秒的時間，請檢閱您的環境設定。
