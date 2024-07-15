---
title: 啟用設定檔分析
description: 深入瞭解如何讓MAGE Profiler搭配您的分析工具使用。
exl-id: a46289ed-16dc-4a72-84ff-85fe825dac11
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# 啟用設定檔分析

使用Commerce設定檔時，您可以：

- 啟用內建分析工具。

  您可以使用內建的效能分析工具搭配Commerce來執行分析效能等工作。 輪廓的性質取決於您使用的分析工具。 我們支援多種格式，包括HTML。 當您啟用效能分析工具時，會產生`var/profiler.flag`檔案，指出效能分析工具已啟用且已進行設定。 停用時，會刪除此檔案。

- 在Commerce頁面上顯示相依性圖表。

  _相依性圖形_&#x200B;是物件相依性及其所有相依性的清單，以及這些相依性的所有相依性等等。

  您應該特別關注&#x200B;_未使用相依性_&#x200B;的清單，這些物件是因為某些建構函式要求而建立的，但是從未使用過（亦即，未呼叫任何方法）。 因此，建立這些相依性所花費的處理器時間和記憶體都會被浪費。

Commerce在[`Magento\Framework\Profiler`][profiler]中提供基礎功能。

您可以使用MAGE_PROFILER變數或命令列來啟用及設定效能評測器。

## 設定MAGE_PROFILER

您可以使用[中討論的任何方法來設定`MAGE_PROFILER`的值。請設定啟動程式引數的值](../bootstrap/set-parameters.md)。

`MAGE_PROFILER`支援下列值：

- `1`以啟用特定分析工具的輸出。

  您可以使用下列其中一個值來啟用特定的效能評測器：

   - 使用[`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`][csvfile]的`csvfile`
   - 任何其他值（除了`2`），包括使用[`Magento\Framework\Profiler\Driver\Standard\Output\Html`][html]的空白值

- `2`以啟用相依性圖形。

  相依性圖表通常顯示在頁面底部。 下圖顯示輸出的部分：

  ![相依性圖表](../../assets/configuration/depend-graphs.png)

## CLI命令

您可以使用CLI指令來啟用或停用效能評測器：

- `dev:profiler:enable <type>`會啟用`html`的`type` （預設）或`csvfile`的效能評測器。 啟用時，會建立flagfile `var/profiler.flag`。
- `dev:profiler:disable`停用效能分析工具。 停用時，會移除flagfile `var/profiler.flag`。

若要啟用相依性圖形，請使用變數選項。

**若要啟用或停用效能分析工具**：

1. 登入您的Commerce伺服器。
1. 變更至Commerce安裝目錄。
1. 以檔案系統擁有者的身分，啟用效能分析工具：

   若要使用型別`html`啟用效能分析工具並建立flagfile：

   ```bash
   bin/magento dev:profiler:enable html
   ```

   若要使用型別`csvfile`啟用效能分析工具並建立flagfile：

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   輸出已儲存到`<project-root>/var/log/profiler.csv`。 每次重新整理頁面時都會覆寫`profiler.csv`。

   若要停用效能分析工具並移除flagfile：

   ```bash
   bin/magento dev:profiler:disable
   ```

<!-- link definitions -->

[csvfile]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php
[html]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php
[profiler]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler.php
