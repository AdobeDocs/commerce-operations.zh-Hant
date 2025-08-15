---
title: 最終驗證
description: 確認您的Varnish設定已正確設定為搭配Adobe Commerce應用程式使用。
feature: Configuration, Cache
exl-id: 01f28c93-75cd-4969-9142-b8dac0aa2adb
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# 清漆組態的最終驗證

現在您正使用Commerce為您產生的`default.vcl`，您可以執行一些最終驗證，以確認Varnish正常運作。

## 驗證HTTP回應標題

當您在網頁瀏覽器中瀏覽任何Commerce頁面時，請使用`curl`或其他公用程式來檢視HTTP回應標題。

首先，請確定您使用的是[開發人員模式](../cli/set-mode.md#change-to-developer-mode)；否則，您將不會看到標頭。

例如，

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

重要標題：

```
X-Magento-Cache-Control: max-age=86400, public, s-maxage=86400
Age: 0
X-Magento-Cache-Debug: MISS
```

>[!INFO]
>
>這個值也可以接受： `X-Magento-Cache-Debug: HIT`。

## 檢查頁面載入時間

如果Varnish正常運作，則任何具有可快取區塊的Commerce頁面應在150毫秒內載入。 此類頁面的範例是前門和店麵類別頁面。

使用瀏覽器檢測器來測量頁面載入時間。

例如，若要使用Chrome檢測器：

1. 存取Chrome中的任何可快取Commerce頁面。
1. 以滑鼠右鍵按一下頁面上的任何位置。
1. 從快顯功能表，按一下&#x200B;**[!UICONTROL Inspect Element]**
1. 在檢視窗窗格中，按一下&#x200B;**[!UICONTROL Network]**&#x200B;標籤。
1. 重新整理頁面。
1. 捲動至檢視窗窗窗格的頂端，以便檢視所檢視頁面的URL。

   下圖顯示載入`magento2`索引頁面的範例。

   ![按一下您正在檢視的頁面](../../assets/configuration/varnish-inspector.png)

   頁面載入時間會顯示在頁面URL旁。 在此情況下，載入時間為5毫秒。 這有助於確認Varnish已快取頁面。

1. 若要檢視HTTP回應標題，請按一下頁面URL （在「名稱」欄中）。

   您可以檢視HTTP標頭，驗證HTTP回應標頭一節中會詳細說明這些標頭。

## 驗證Commerce快取

確定`<magento_root>/var/page_cache`目錄是空的：

1. 登入您的Commerce伺服器，或切換到檔案系統擁有者。
1. 輸入下列命令：

   ```bash
   rm -rf <magento_root>/var/page_cache/*
   ```

1. 存取一或多個可快取的Commerce頁面。
1. 檢查`var/page_cache/`目錄。

   如果目錄是空的，恭喜您！ 您已成功設定Varnish與Commerce搭配運作！

1. 如果您已清除`var/page_cache/`目錄，請重新啟動Varnish。

>[!TIP]
>
>如果您遇到503 （後端擷取失敗）錯誤，請參閱[Adobe Commerce說明中心](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshooting-503-errors.html)中的&#x200B;_疑難排解503 （服務無法使用）錯誤_。
