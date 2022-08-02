---
title: 在管理員中設定多個網站、商店和商店視圖
description: 在Commerce Admin中配置其他網站、商店和商店視圖。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '1016'
ht-degree: 0%

---


# 在管理員中設定多個視圖

此任務要求您為每個儲存建立根類別（如果需要，還需要建立其他類別）。 本主題中討論的任務提供了設定多個儲存的一種方法。 有關其他資訊，請參閱《Commerce User Guide》中的以下資源：

- [類別](https://docs.magento.com/user-guide/catalog/categories.html)
- [添加網站](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [儲存URL](https://docs.magento.com/user-guide/stores/store-urls.html)
- [內容](https://docs.magento.com/user-guide/cms/content-menu.html)

>[!INFO]
>
>例如，我們僅使用帶有網站代碼的法文網站 `french` 在此主題中。 有關逐步教程，請參見 [教程：使用Apache設定多個網站](ms-apache.md) 和 [教程：使用nginx設定多個網站](ms-nginx.md)

## 步驟1:建立根類別

建立根類別是可選的，但我們在本教程中介紹了如何 [事件](https://glossary.magento.com/event) 您希望每個網站都具有唯一的根類別。 如果您選擇，可以建立附加類別。

要建立根類別，請執行以下操作：

1. 以有權建立類別的用戶身份登錄到管理員。
1. 按一下 **目錄** > **類別**。
1. 按一下 **添加根類別**。
1. 在 **類別名稱** 欄位，輸入唯一名稱以標識此類別。
1. 確保將「啟用類別」設定為 **是**。

   有關此頁上其他選項的資訊，請參見 [根類別](https://docs.magento.com/user-guide/catalog/category-root.html)。

   下圖顯示了一個示例。

   ![建立並啟用根類別](../../assets/configuration/add-root-category.png)

1. 按一下 **保存**。
1. 根據需要多次重複這些任務，以為儲存建立根類別。

## 步驟2:建立網站

要建立網站：

1. 以有權建立網站、商店和商店視圖的用戶身份登錄到管理員。
1. 按一下 **商店** > **設定** > **所有商店**。
1. 在 _商店_ 的 **建立網站**。

   - **名稱** — 輸入標識網站的名稱。
   - **代碼** — 輸入唯一代碼；例如，如果您有一家法國商店，則可以 `french`
   - **排序順序** — 輸入可選的數字排序順序。

   下圖顯示了一個示例。

   ![添加網站](../../assets/configuration/multi-site-website.png)

1. 按一下 **保存網站**。
1. 在建立網站時，請根據需要重複這些任務多次。

## 第3步：建立商店

要建立儲存：

1. 在 _管理_ 面板，按一下 **商店** > **設定** > **所有商店**。
1. 在 _商店_ 的 **建立儲存**。

   - **網站** — 按一下要與此儲存關聯的網站名稱。
   - **名稱** — 輸入名稱以標識儲存。
   - **代碼** — 輸入唯一代碼以標識儲存。
   - **根類別** — 按一下此儲存的根類別的名稱。

   下圖顯示了一個示例。

   ![添加儲存](../../assets/configuration/multi-site-store.png)

1. 按一下 **保存儲存**。
1. 在建立儲存區時，請根據需要重複執行這些任務多次。

## 第4步：建立儲存視圖

要建立儲存視圖：

1. 在 _管理_ 面板，按一下 **商店** > **設定** > **所有商店**。
1. 在「儲存」頁面上，按一下 **建立儲存視圖**。

   - **儲存** — 按一下要與此儲存視圖關聯的儲存的名稱。
   - **名稱** — 輸入標識此儲存視圖的名稱。
   - **代碼** — 輸入唯一名稱以標識此儲存視圖。
   - **狀態** — 選擇 **已啟用**。

   下圖顯示了一個示例。

   ![添加儲存](../../assets/configuration/multi-site-storeview.png)

1. 按一下 **保存儲存視圖**。
1. 在建立儲存視圖時，根據需要重複這些任務多次。

## 第5步：更改網站基URL

使用唯一URL訪問網站，如 `http://french.magento.mg`，必須更改管理中每個站點的基URL。

要更改網站基URL:

1. 在 _管理_ 面板，按一下 **商店** > **設定** > **配置** > **常規** > **Web**。
1. 從 **儲存視圖** 清單中，按一下以下圖所示其中一個網站的名稱。

   ![選擇範圍](../../assets/configuration/multi-site-scope.png)

1. 在右窗格中，展開 **基本URL**。
1. 在 _基本URL_ 部分，清除 **使用系統值**。
1. 輸入 `http://french.magento.mg` 中的URL **基本URL** 和 **基本連結URL** 的子菜單。

1. 在 _基本URL（安全）_ 的子菜單。

   >[!INFO]
   >
   >如果要為在雲基礎架構上部署Adobe Commerce設定基本URL，則必須用三段線替換第一個時段。 例如，如果基URL是 `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`輸入 `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`。 如果要設定用於本地測試的基URL，請使用句點。

1. 按一下 **保存配置**。

1. 對其他網站重複這些任務。

## 步驟6:將儲存代碼添加到基本URL

Commerce為您提供了將儲存代碼添加到站點基URL的選項，這簡化了設定多個儲存的過程。 使用此選項，您不必在Commerce檔案系統上建立目錄來儲存 `index.php` 和 `.htaccess`。

這防止 `index.php` 和 `.htaccess` 從未來升級時與Commerce代碼不同步。

查看 [《 Commerce使用手冊》](https://docs.magento.com/user-guide/stores/store-urls.html)。

要將儲存代碼添加到基本URL:

1. 在 _管理_ 面板，按一下 **商店** > **設定** > **配置** > **常規** > **Web**。
1. 從 **儲存視圖** 清單，按一下 **預設配置** 如下圖所示。

   ![選擇預設配置範圍](../../assets/configuration/multi-site-default.png)

1. 在右窗格中，展開 **URL選項**。
1. 清除 **使用系統值** 複選框 _將儲存代碼添加到URL_。
1. 從 _將儲存代碼添加到URL_ 清單，按一下 **是**。

   ![將儲存代碼添加到儲存基URL](../../assets/configuration/multi-site-add-store-url.png)

1. 按一下 **保存配置**。
1. 如果出現提示，刷新快取。 (**系統** > **快取管理**)。

## 第7步：更改預設儲存視圖基URL

您必須最後執行此步驟，因為您將失去對管理員的訪問權限；設定虛擬主機後，訪問將返回，如Web伺服器特定主題中所述。

要更改預設儲存視圖基URL:

1. 在 _管理_ 面板，按一下 **商店** > **設定** > **配置** > **常規** > **Web**。

1. 從 _儲存視圖_ 清單，按一下 **預設配置**。

   ![選擇預設配置範圍](../../assets/configuration/multi-site-default.png)

1. 在右窗格中，展開 **基本URL**。
1. 在 _基本URL_ 部分，清除 **使用系統值**。
1. 輸入 `http://magento.mg` 中的URL **基本URL** 和 **基本連結URL** 的子菜單。

1. 在 **基本URL（安全）** 的子菜單。

   >[!INFO]
   >
   >如果要在雲基礎架構上為Adobe Commerce設定基本URL，則必須用三段線替換第一個句點。 例如，如果基URL是 `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`輸入 `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`

1. 按一下 **保存配置**。
