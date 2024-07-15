---
title: 驗證安裝
description: 請依照下列步驟，確認您內部部署的Adobe Commerce安裝成功。
exl-id: 0bd7ec01-c616-4384-ae26-db2ce3668caf
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# 驗證安裝

使用網頁瀏覽器前往店面。 例如，如果您的安裝基底URL是`http://www.example.com`，請在瀏覽器的位址或位置列中輸入它。

下圖顯示一個店面頁面的範例。 如果它顯示如下，表示您的安裝成功！

![使用Luma佈景主題的店面](../../assets/installation/install-success_store-luma.png)

## 驗證店面（無範例資料）

使用網頁瀏覽器前往店面。 例如，如果您的安裝基底URL是`http://www.example.com`，請在瀏覽器的位址或位置列中輸入它。

下圖顯示一個店面頁面的範例。 如果它顯示如下，表示您的安裝成功！

![驗證成功安裝的店面](../../assets/installation/install-success_store.png)

如果頁面顯示`404 (Not Found)`錯誤或不顯示樣式，請參閱[疑難排解](https://support.magento.com/hc/en-us/articles/360032994352)。

## 驗證管理員

在網頁瀏覽器中前往「管理員」。 例如，如果您的安裝基底URL是`http://www.example.com`，而管理員URI是`admin_au1nT`，請在瀏覽器的位址或位置列輸入`http://www.example.com/admin_au1nT`。

（`backend-frontname`安裝引數的值指定了管理員URI。）

出現提示時，請以管理員身分登入。

下圖顯示管理頁面的範例。 如果它顯示如下，表示您的安裝成功！

![驗證成功安裝的管理員](../../assets/installation/install_success_admin.png)

如果頁面未顯示樣式，請參閱[疑難排解](https://support.magento.com/hc/en-us/articles/360032994352)。

如果您收到類似下列的404 （找不到）錯誤，請參閱[在瀏覽器](https://support.magento.com/hc/en-us/articles/360033117152)中存取Adobe Commerce時發生PHP版本錯誤或404。

`The requested URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ was not found on this server.`
