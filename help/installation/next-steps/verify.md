---
title: 驗證安裝
description: 按照以下步驟確認您的本地Adobe Commerce或Magento Open Source安裝成功。
exl-id: 0bd7ec01-c616-4384-ae26-db2ce3668caf
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# 驗證安裝

在Web瀏覽器中轉到店面。 例如，如果安裝基URL為 `http://www.example.com`，在瀏覽器的地址或位置欄中輸入。

下圖顯示了一個樣例的店面頁面。 如果按如下所示顯示，則您的安裝成功！

![有盧瑪主題的店面](../../assets/installation/install-success_store-luma.png)

## 驗證儲存前端（無示例資料）

在Web瀏覽器中轉到店面。 例如，如果安裝基URL為 `http://www.example.com`，在瀏覽器的地址或位置欄中輸入。

下圖顯示了一個樣例的店面頁面。 如果按如下所示顯示，則您的安裝成功！

![驗證安裝成功的Storefront](../../assets/installation/install-success_store.png)

如果頁面顯示 `404 (Not Found)` 錯誤或不顯示樣式，請參閱 [疑難解答](https://support.magento.com/hc/en-us/articles/360032994352)。

## 驗證管理員

在Web瀏覽器中轉到Admin。 例如，如果安裝基URL為 `http://www.example.com`，並且管理URI為 `admin_au1nT`輸入 `http://www.example.com/admin_au1nT` 地址或位置欄。

(管理URI由 `backend-frontname` 安裝參數。)

出現提示時，以管理員身份登錄。

下圖顯示了「管理員」頁面示例。 如果按如下所示顯示，則您的安裝成功！

![驗證成功安裝的管理員](../../assets/installation/install_success_admin.png)

如果頁面不顯示樣式，請參閱 [故障排除](https://support.magento.com/hc/en-us/articles/360032994352)。

如果遇到與以下內容類似的404（未找到）錯誤，請參閱 [在瀏覽器中訪問Adobe Commerce時PHP版本錯誤或404](https://support.magento.com/hc/en-us/articles/360033117152)。

`The requested URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ was not found on this server.`
