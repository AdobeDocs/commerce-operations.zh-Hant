---
title: 在管理員中設定多個網站、商店和商店檢視
description: 在Commerce管理員中設定其他網站、商店和商店檢視。
exl-id: e6b4d14d-7504-48f9-a2e1-7e9a1bc76ab9
source-git-commit: f7c82844fd6d006e4ebbcf56f6e10338f67d0bdd
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 0%

---

# 在管理員中設定多個檢視

此工作需要您為每個存放區建立根類別(以及其他類別（如有需要）。 本主題中討論的任務提供設定多個存放區的方法。 如需詳細資訊，請參閱Commerce使用手冊中的下列資源：

- [類別](https://docs.magento.com/user-guide/catalog/categories.html)
- [新增網站](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [儲存URL](https://docs.magento.com/user-guide/stores/store-urls.html)
- [內容](https://docs.magento.com/user-guide/cms/content-menu.html)

>[!INFO]
>
>在此主題中，我們使用法文網站搭配網站代碼`french`，僅供範例使用。 如需逐步教學課程，請參閱[教學課程：使用Apache](ms-apache.md)設定多個網站[教學課程：使用nginx](ms-nginx.md)設定多個網站

## 步驟1：建立根類別

建立根目錄類別為選用，但在本教學課程中，我們將說明如何在您希望每個網站都有唯一根目錄類別的情況下執行此操作。 您可以選擇建立其他類別。

若要建立根類別，請執行下列動作：

1. 以獲授權建立類別的使用者身分登入管理員。
1. 按一下&#x200B;**目錄** > **類別**。
1. 按一下&#x200B;**新增根類別**。
1. 在&#x200B;**類別名稱**&#x200B;欄位中，輸入唯一名稱以識別此類別。
1. 確定啟用類別設定為&#x200B;**是**。

   如需此頁面上其他選項的相關資訊，請參閱[根類別](https://docs.magento.com/user-guide/catalog/category-root.html)。

   下圖顯示一個範例。

   ![建立並啟用根類別](../../assets/configuration/add-root-category.png)

1. 按一下&#x200B;**儲存**。
1. 視需要重複這些工作多次，以建立存放區的根類別。

## 步驟2：建立網站

若要建立網站：

1. 以獲授權建立網站、商店和商店檢視的使用者身分登入「管理員」 。
1. 按一下&#x200B;**商店** > **設定** > **所有商店**。
1. 在&#x200B;_商店_&#x200B;頁面上，按一下&#x200B;**建立網站**。

   - **名稱** — 輸入名稱以識別網站。
   - **代碼** — 輸入唯一代碼；例如，如果您有法式商店，則可輸入`french`
   - **排序順序** — 輸入選用的數字排序順序。

   下圖顯示一個範例。

   ![新增網站](../../assets/configuration/multi-site-website.png)

1. 按一下&#x200B;**儲存網站**。
1. 視需要多次重複這些工作，以建立您的網站。

## 步驟3：建立存放區

若要建立存放區：

1. 在&#x200B;_管理員_&#x200B;面板中，按一下&#x200B;**商店** > **設定** > **所有商店**。
1. 在&#x200B;_商店_&#x200B;頁面上，按一下&#x200B;**建立商店**。

   - **網站** — 按一下要與此商店關聯的網站名稱。
   - **名稱** — 輸入名稱以識別存放區。
   - **代碼** — 輸入唯一代碼以識別商店。
   - **根類別** — 按一下此存放區的根類別名稱。

   下圖顯示一個範例。

   ![新增存放區](../../assets/configuration/multi-site-store.png)

1. 按一下&#x200B;**儲存存放區**。
1. 視需要多次重複這些工作以建立您的存放區。

## 步驟4：建立存放區檢視

若要建立商店檢視：

1. 在&#x200B;_管理員_&#x200B;面板中，按一下&#x200B;**商店** > **設定** > **所有商店**。
1. 在商店頁面上，按一下&#x200B;**建立商店檢視**。

   - **存放區** — 按一下要與此存放區檢視關聯的存放區名稱。
   - **名稱** — 輸入名稱以識別此存放區檢視。
   - **代碼** — 輸入唯一名稱以識別此存放區檢視。
   - **狀態** — 選取&#x200B;**已啟用**。

   下圖顯示一個範例。

   ![新增存放區](../../assets/configuration/multi-site-storeview.png)

1. 按一下&#x200B;**儲存存放區檢視**。
1. 視需要重複這些工作多次，以建立您的商店檢視。

## 步驟5：變更網站基底URL

若要使用`http://french.magento.mg`之類的唯一URL存取網站，您必須變更Admin中每個網站的基底URL。

若要變更網站基底URL：

1. 在&#x200B;_管理員_&#x200B;面板中，按一下&#x200B;**商店** > **設定** > **組態** > **一般** > **網頁**。
1. 從頁面頂端的&#x200B;**商店檢視**&#x200B;清單中，按一下您其中一個網站的名稱，如下圖所示。

   ![選取範圍](../../assets/configuration/multi-site-scope.png)

1. 在右窗格中，展開&#x200B;**基礎URL**。
1. 在&#x200B;_基底URL_&#x200B;區段中，清除&#x200B;**使用系統值**。
1. 在&#x200B;**基底URL**&#x200B;和&#x200B;**基底連結URL**&#x200B;欄位中輸入`http://french.magento.mg` URL。

1. 重複&#x200B;_基礎URL （安全）_&#x200B;區段中的上一步。

   >[!INFO]
   >
   >如果您正在設定雲端基礎結構上部署Adobe Commerce的基礎URL，則必須將第一個句號取代為三個破折號。 例如，如果您的基底URL是`french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`，請輸入`http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`。 如果您設定基底URL以進行本機測試，請使用句點。

1. 按一下&#x200B;**儲存設定**。

1. 對其他網站重複這些工作。

## 步驟6：將商店程式碼新增至基底URL

Commerce提供將商店程式碼新增至網站基底URL的選項，可簡化設定多個商店的程式。 使用此選項，您不必在Commerce檔案系統上建立目錄來儲存`index.php`和`.htaccess`。

這可防止`index.php`和`.htaccess`在未來的升級中與Commerce程式碼基底不同步。

請參閱[Commerce使用手冊](https://docs.magento.com/user-guide/stores/store-urls.html)。

若要將商店程式碼新增至基底URL：

1. 在&#x200B;_管理員_&#x200B;面板中，按一下&#x200B;**商店** > **設定** > **組態** > **一般** > **網頁**。
1. 從頁面頂端的&#x200B;**存放區檢視**&#x200B;清單中，按一下&#x200B;**預設設定**，如下圖所示。

   ![選取預設設定範圍](../../assets/configuration/multi-site-default.png)

1. 在右窗格中，展開&#x200B;**Url選項**。
1. 清除&#x200B;_將存放區代碼新增至Url_&#x200B;旁的&#x200B;**使用系統值**&#x200B;核取方塊。
1. 從&#x200B;_新增存放區代碼至Url_&#x200B;清單，按一下&#x200B;**是**。

   ![將商店代碼新增至商店基底URL](../../assets/configuration/multi-site-add-store-url.png)

1. 按一下&#x200B;**儲存設定**。
1. 如果出現提示，請排清快取。 （**系統** > **快取管理**）。

## 步驟7：變更預設商店檢視基底URL

您必須在最後執行此步驟，因為您將失去管理員的存取權；您的存取權會在您設定虛擬主機後傳回，如網頁伺服器特定主題中所述。

若要變更預設商店檢視基底URL：

1. 在&#x200B;_管理員_&#x200B;面板中，按一下&#x200B;**商店** > **設定** > **組態** > **一般** > **網頁**。

1. 從頁面頂端的&#x200B;_存放區檢視_&#x200B;清單中，按一下&#x200B;**預設設定**。

   ![選取預設設定範圍](../../assets/configuration/multi-site-default.png)

1. 在右窗格中，展開&#x200B;**基礎URL**。
1. 在&#x200B;_基底URL_&#x200B;區段中，清除&#x200B;**使用系統值**。
1. 在&#x200B;**基底URL**&#x200B;和&#x200B;**基底連結URL**&#x200B;欄位中輸入`http://magento.mg` URL。

1. 重複&#x200B;**基礎URL （安全）**&#x200B;區段中的上一步。

   >[!INFO]
   >
   >如果您在雲端基礎結構上設定Adobe Commerce的基本URL，則必須將第一個句號取代為三個破折號。 例如，如果您的基底URL是`french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`，請輸入`http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`

1. 按一下&#x200B;**儲存設定**。

>[!INFO]
>
>網站、商店和商店檢視代碼只能包含字母（a-z或A-Z）、數字(0-9)和底線(_)。 此外，第一個字元必須是字母。 如果使用大寫或駝峰式大小寫，內部比對不區分大小寫，以透過環境變數來適應設定覆寫。 請參閱[使用環境變數覆寫組態設定](../reference/override-config-settings.md#environment-variables)。