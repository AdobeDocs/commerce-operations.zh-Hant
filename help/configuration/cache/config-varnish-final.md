---
title: 最終驗證
description: 驗證清漆配置是否已正確設定以與Adobe Commerce應用程式配合使用。
exl-id: 01f28c93-75cd-4969-9142-b8dac0aa2adb
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# 清漆結構的最終驗證

現在您正在使用 `default.vcl` Commerce為您生成的清漆，您可以執行一些最終驗證以確保清漆正在工作。

## 驗證HTTP響應標頭

使用 `curl` 或另一個實用程式，用於在您訪問Web瀏覽器中的任何Commerce頁時查看HTTP響應標頭。

首先，確保您使用 [開發者模式](../cli/set-mode.md#change-to-developer-mode);否則，您將看不到標題。

比如說，

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
>此值也可接受： `X-Magento-Cache-Debug: HIT`。

## 檢查頁載入時間

如果清漆正在工作，則任何具有可快取塊的Commerce頁面都應在150毫秒內載入。 此類頁面的示例包括前門和店麵類別頁面。

使用瀏覽器檢查器來測量頁面載入時間。

例如，要使用Chrome檢查器：

1. 訪問Chrome中任何可快取的Commerce頁。
1. 按一下右鍵頁面上的任意位置。
1. 在彈出菜單中，按一下 **[!UICONTROL Inspect Element]**
1. 在檢查器窗格中，按一下 **[!UICONTROL Network]** 頁籤。
1. 刷新頁面。
1. 滾動到檢查器窗格的頂部，以便您可以查看正在查看的頁面的URL。

   下圖顯示了載入 `magento2` 的子菜單。

   ![按一下您正在查看的頁面](../../assets/configuration/varnish-inspector.png)

   頁面載入時間顯示在頁面URL旁邊。 在這種情況下，載入時間為5毫秒。 這有助於確認清漆是否快取了頁面。

1. 要查看HTTP響應頭，請按一下頁URL（在「名稱」列中）。

   您可以在「驗證HTTP響應標頭」部分中查看詳細討論的HTTP標頭。

## 驗證Commerce快取

確保 `<magento_root>/var/page_cache` 目錄為空：

1. 登錄到Commerce伺服器或切換到檔案系統所有者。
1. 輸入以下命令：

   ```bash
   rm -rf <magento_root>/var/page_cache/*
   ```

1. 訪問一個或多個可快取的Commerce頁。
1. 檢查 `var/page_cache/` 的子菜單。

   如果目錄為空，恭喜！ 您已成功配置清漆和Commerce以協同工作！

1. 如果你清除了 `var/page_cache/` 目錄，重新啟動清漆。

>[!TIP]
>
>如果遇到503（後端提取失敗）錯誤，請參見 [排除503（服務不可用）錯誤](https://support.magento.com/hc/en-us/articles/360034631211) 的 _Adobe Commerce幫助中心_。
