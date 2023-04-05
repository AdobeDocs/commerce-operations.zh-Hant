---
title: 驗證安裝
description: 請依照下列步驟，確認您的內部部署Adobe Commerce或Magento Open Source安裝是否成功。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---


# 驗證安裝

在網頁瀏覽器中前往店面。 例如，如果您的安裝基礎URL為 `http://www.example.com`，請在瀏覽器的位址或位置列中輸入。

下圖顯示了一個樣例的店面頁面。 如果顯示如下，表示您的安裝成功！

![有盧瑪主題的店面](../../assets/installation/install-success_store-luma.png)

## 驗證店面（無範例資料）

在網頁瀏覽器中前往店面。 例如，如果您的安裝基礎URL為 `http://www.example.com`，請在瀏覽器的位址或位置列中輸入。

下圖顯示了一個樣例的店面頁面。 如果顯示如下，表示您的安裝成功！

![驗證安裝成功的Storefront](../../assets/installation/install-success_store.png)

如果頁面顯示 `404 (Not Found)` 錯誤或未顯示樣式，請參閱 [疑難排解](https://support.magento.com/hc/en-us/articles/360032994352).

## 驗證管理員

在網頁瀏覽器中前往管理員。 例如，如果您的安裝基礎URL為 `http://www.example.com`，而管理URI為 `admin_au1nT`，輸入 `http://www.example.com/admin_au1nT` 位址或位置列。

(管理員URI由 `backend-frontname` 安裝參數)。

出現提示時，請以管理員身分登入。

下圖顯示了示例管理頁。 如果顯示如下，表示您的安裝成功！

![驗證安裝是否成功的管理員](../../assets/installation/install_success_admin.png)

如果頁面未顯示樣式，請參閱 [疑難排解](https://support.magento.com/hc/en-us/articles/360032994352).

如果您收到類似下列的404（找不到）錯誤，請參閱 [PHP版本錯誤或404在瀏覽器中存取Adobe Commerce時](https://support.magento.com/hc/en-us/articles/360033117152).

`The requested URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ was not found on this server.`
