---
title: 模組更新失敗後回滾
description: 遇到模組更新錯誤後，對Adobe Commerce或Magento Open Source升級進行故障排除。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---


# 模組更新失敗後回滾

如果模組更新失敗，則類似於控制台日誌中顯示的消息：

```terminal
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

在上例中，沒有要回滾的元件版本。 與元件供應商聯繫或嘗試自行解決問題。

同時，您可以通過按一下 **回滾**，即使您以前沒有備份，也可恢復資料。
