---
title: 模組更新失敗後回滾
description: 遇到模組更新錯誤後，疑難排解Adobe Commerce或Magento Open Source升級。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---


# 模組更新失敗後回滾

如果您的模組更新失敗，控制台記錄中會顯示類似下列的訊息：

```terminal
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

在上例中，沒有要回轉的元件版本。 請聯繫元件供應商或嘗試自行解決問題。

同時，您可以按一下「 」，回復成舊版 **回復**，即使您先前未進行備份，也會恢復資料。
