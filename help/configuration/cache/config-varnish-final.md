---
title: 最終驗證
description: 確認您的清漆設定已正確設定，以便與Adobe Commerce應用程式搭配使用。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---


# 清漆結構的最終驗證

現在您使用 `default.vcl` 由商務產生，您可以執行一些最終驗證，以確保清漆正常運作。

## 驗證HTTP回應標題

使用 `curl` 或其他公用程式，以在您於網頁瀏覽器中瀏覽任何商務頁面時檢視HTTP回應標題。

首先，請確定您使用 [開發人員模式](../cli/set-mode.md#change-to-developer-mode);否則，您將看不到標題。

例如，

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

重要標題：

```terminal
X-Magento-Cache-Control: max-age=86400, public, s-maxage=86400
Age: 0
X-Magento-Cache-Debug: MISS
```

>[!INFO]
>
>此值也是可接受的值： `X-Magento-Cache-Debug: HIT`.

## 檢查頁面載入時間

如果清漆正常運作，任何具有可快取區塊的商務頁面都應在150毫秒內載入。 此類頁面的示例包括前門和店麵類別頁。

使用瀏覽器檢查器來測量頁面載入時間。

例如，要使用Chrome檢查器：

1. 存取Chrome中的任何可快取商務頁面。
1. 按一下右鍵頁面上的任意位置。
1. 在快顯功能表中，按一下 **[!UICONTROL Inspect Element]**
1. 在檢查器窗格中，按一下 **[!UICONTROL Network]** 標籤。
1. 重新整理頁面。
1. 滾動到檢查器窗格的頂部，以便查看所查看頁的URL。

   下圖顯示載入 `magento2` 索引頁。

   ![按一下您正在檢視的頁面](../../assets/configuration/varnish-inspector.png)

   頁面載入時間會顯示在頁面URL旁。 在這種情況下，載入時間為5毫秒。 這有助於確認已快取頁面的清漆。

1. 若要檢視HTTP回應標題，請按一下頁面URL（位於「名稱」欄中）。

   您可以檢視HTTP標題，有關詳細說明，請參閱驗證HTTP回應標題區段。

## 驗證商務快取

請確定 `<magento_root>/var/page_cache` 目錄為空：

1. 登入您的Commerce伺服器，或切換至檔案系統擁有者。
1. 輸入以下命令：

   ```bash
   rm -rf <magento_root>/var/page_cache/*
   ```

1. 存取一或多個可快取的商務頁面。
1. 檢查 `var/page_cache/` 目錄。

   如果目錄空，恭喜！ 您已成功配置清漆和商務功能，以便協同工作！

1. 如果清除 `var/page_cache/` 目錄，重新啟動清漆。

>[!TIP]
>
>如果您遇到503（後端擷取失敗）錯誤，請參閱 [疑難排解503（服務無法使用）錯誤](https://support.magento.com/hc/en-us/articles/360034631211) 在 _Adobe Commerce說明中心_.
