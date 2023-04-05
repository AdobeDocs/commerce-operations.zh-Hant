---
title: 在管理員中設定多個網站、商店和儲存檢視
description: 在「商務管理員」中設定其他網站、商店和儲存檢視。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 在管理員中設定多個檢視

此任務要求您為每個儲存建立根類別(以及其他類別（如果需要）。 本主題中討論的任務提供了設定多個儲存的方法。 如需詳細資訊，請參閱商務使用手冊中的下列資源：

- [類別](https://docs.magento.com/user-guide/catalog/categories.html)
- [新增網站](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [儲存URL](https://docs.magento.com/user-guide/stores/store-urls.html)
- [內容](https://docs.magento.com/user-guide/cms/content-menu.html)

>[!INFO]
>
>僅為了例項目的目的，我們使用的是具有網站代碼的法文網站 `french` 中。 如需逐步教學課程，請參閱 [教學課程：使用Apache設定多個網站](ms-apache.md) 和 [教學課程：使用nginx設定多個網站](ms-nginx.md)

## 步驟1:建立根類別

建立根類別是選用的，但若您希望每個網站都有唯一的根類別，我們會在本教學課程中說明如何這麼做。 您可以選擇建立其他類別。

要建立根類別，請執行以下操作：

1. 以授權建立類別的使用者身分登入管理員。
1. 按一下 **目錄** > **類別**.
1. 按一下 **新增根類別**.
1. 在 **類別名稱** 欄位中輸入唯一名稱以標識此類別。
1. 確保「啟用類別」設定為 **是**.

   有關此頁上其他選項的資訊，請參見 [根類別](https://docs.magento.com/user-guide/catalog/category-root.html).

   下圖顯示了一個示例。

   ![建立並啟用根類別](../../assets/configuration/add-root-category.png)

1. 按一下 **儲存**.
1. 視需要重複執行這些工作，為您的商店建立根類別。

## 步驟2:建立網站

若要建立網站：

1. 以授權建立網站、儲存和儲存檢視的使用者身分登入管理員。
1. 按一下 **商店** > **設定** > **所有商店**.
1. 在 _商店_ 頁面，按一下 **建立網站**.

   - **名稱** — 輸入一個名稱以標識網站。
   - **程式碼** — 輸入唯一代碼；例如，如果您有法國商店，則可以輸入 `french`
   - **排序順序** — 輸入可選的數字排序順序。

   下圖顯示了一個示例。

   ![新增網站](../../assets/configuration/multi-site-website.png)

1. 按一下 **保存網站**.
1. 在建立網站時，請視需要重複執行這些工作。

## 步驟3:建立商店

建立商店：

1. 在 _管理_ 面板，按一下 **商店** > **設定** > **所有商店**.
1. 在 _商店_ 頁面，按一下 **建立商店**.

   - **網站** — 按一下要與此商店關聯的網站名稱。
   - **名稱** — 輸入標識商店的名稱。
   - **程式碼** — 輸入唯一代碼以標識商店。
   - **根類別** — 按一下此儲存的根類別的名稱。

   下圖顯示了一個示例。

   ![新增商店](../../assets/configuration/multi-site-store.png)

1. 按一下 **儲存商店**.
1. 在建立商店時，請視需要重複執行這些工作。

## 步驟4:建立商店檢視

要建立商店視圖，請執行以下操作：

1. 在 _管理_ 面板，按一下 **商店** > **設定** > **所有商店**.
1. 在「商店」頁面上，按一下 **建立商店視圖**.

   - **商店** — 按一下要與此儲存視圖關聯的儲存的名稱。
   - **名稱** — 輸入一個名稱以標識此儲存視圖。
   - **程式碼** — 輸入唯一名稱以標識此商店視圖。
   - **狀態** — 選取 **已啟用**.

   下圖顯示了一個示例。

   ![新增商店](../../assets/configuration/multi-site-storeview.png)

1. 按一下 **保儲存存視圖**.
1. 視需要重複執行這些工作，以建立商店檢視。

## 步驟5:變更網站基礎URL

若要使用不重複URL(如 `http://french.magento.mg`，您必須在「管理員」中變更每個網站的基本URL。

若要變更網站基礎URL:

1. 在 _管理_ 面板，按一下 **商店** > **設定** > **設定** > **一般** > **Web**.
1. 從 **商店檢視** 清單，按一下其中一個網站的名稱，如下圖所示。

   ![選擇範圍](../../assets/configuration/multi-site-scope.png)

1. 在右窗格中，展開 **基本URL**.
1. 在 _基本URL_ 部分，清除 **使用系統值**.
1. 輸入 `http://french.magento.mg` 中的URL **基本URL** 和 **基本連結URL** 欄位。

1. 在 _基本URL（安全）_ 區段。

   >[!INFO]
   >
   >如果您要在雲端基礎架構上為部署Adobe Commerce設定基本URL，則必須將第一個句號取代為三個破折號。 例如，如果您的基礎URL為 `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`，輸入 `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`. 如果您要設定本機測試的基礎URL，請使用句點。

1. 按一下 **儲存設定**.

1. 對其他網站重複執行這些任務。

## 步驟6:將存放區代碼新增至基本URL

商務可讓您選擇將商店代碼新增至網站基底URL，以簡化設定多個商店的程式。 使用此選項，您不必在Commerce檔案系統上建立目錄即可儲存 `index.php` 和 `.htaccess`.

這可防止 `index.php` 和 `.htaccess` 從未來升級時與商務程式碼基底不同步。

請參閱 [商務使用手冊](https://docs.magento.com/user-guide/stores/store-urls.html).

若要將存放區代碼新增至基本URL:

1. 在 _管理_ 面板，按一下 **商店** > **設定** > **設定** > **一般** > **Web**.
1. 從 **商店檢視** 清單，按一下 **預設設定** 如下圖所示。

   ![選擇預設配置範圍](../../assets/configuration/multi-site-default.png)

1. 在右窗格中，展開 **Url選項**.
1. 清除 **使用系統值** 複選框 _將儲存程式碼新增至Url_.
1. 從 _將儲存程式碼新增至Url_ 清單，按一下 **是**.

   ![將商店代碼添加到商店基本URL](../../assets/configuration/multi-site-add-store-url.png)

1. 按一下 **儲存設定**.
1. 如果出現提示，請刷新快取。 (**系統** > **快取管理**)。

## 步驟7:更改預設商店視圖基URL

您必須最後執行此步驟，因為您將失去管理員的存取權；在您設定虛擬主機後，將返回訪問權限，如Web伺服器特定主題中所述。

要更改預設儲存視圖基URL，請執行以下操作：

1. 在 _管理_ 面板，按一下 **商店** > **設定** > **設定** > **一般** > **Web**.

1. 從 _商店檢視_ 清單，按一下 **預設設定**.

   ![選擇預設配置範圍](../../assets/configuration/multi-site-default.png)

1. 在右窗格中，展開 **基本URL**.
1. 在 _基本URL_ 部分，清除 **使用系統值**.
1. 輸入 `http://magento.mg` 中的URL **基本URL** 和 **基本連結URL** 欄位。

1. 在 **基本URL（安全）** 區段。

   >[!INFO]
   >
   >如果您要在雲端基礎架構上為Adobe Commerce設定基本URL，必須將第一個句號取代為三個破折號。 例如，如果您的基礎URL為 `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`，輸入 `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`

1. 按一下 **儲存設定**.
