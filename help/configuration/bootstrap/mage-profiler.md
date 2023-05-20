---
title: 啟用分析
description: 瞭解有關啟用MAGE Profiler與分析工具一起使用的詳細資訊。
exl-id: a46289ed-16dc-4a72-84ff-85fe825dac11
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# 啟用分析

使用Commerce配置檔案，您可以：

- 啟用內置探查器。

   您可以使用帶Commerce的內置Profiler執行分析效能等任務。 特徵分析的性質取決於您使用的分析工具。 我們支援多種格式，包括HTML。 啟用Profiler時， `var/profiler.flag` 檔案生成，指示已啟用Profiler和配置。 禁用後，此檔案將被刪除。

- 在Commerce頁上顯示依賴關係圖。

   A _依賴關係圖_ 是對象依賴項及其所有依賴項的清單，以及這些依賴項的所有依賴項等。

   你應該特別感興趣 _未使用的依賴項_，這些對象是由於在某些建構子中請求而建立的，但從未使用（即，未調用其任何方法）。 因此，浪費了用於建立這些依賴關係的處理器時間和記憶體。

Commerce提供中的基本功能 [`Magento\Framework\Profiler`][profiler]。

可以使用MAGE_PROFILER變數或命令行啟用和配置探查器。

## 設定MAGE_PROFILER

可以設定 `MAGE_PROFILER` 以中討論的任何方式 [設定引導參數的值](../bootstrap/set-parameters.md)。

`MAGE_PROFILER` 支援以下值：

- `1` 啟用特定探查器的輸出。

   可以使用以下值之一啟用特定探查器：

   - `csvfile` 使用 [`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`][csvfile]
   - 任何其他值(除 `2`)，包括空值，該值使用 [`Magento\Framework\Profiler\Driver\Standard\Output\Html`][html]

- `2` 啟用依賴關係圖。

   依賴關係圖通常顯示在頁面底部。 下圖顯示了輸出的一部分：

   ![依賴關係圖](../../assets/configuration/depend-graphs.png)

## CLI命令

可以使用CLI命令啟用或禁用Profiler:

- `dev:profiler:enable <type>` 啟用Profiler `type` 共 `html` （預設）或 `csvfile`。 啟用時，會顯示一個 `var/profiler.flag` 的子菜單。
- `dev:profiler:disable` 禁用探查器。 禁用時，flagfile `var/profiler.flag` 的子菜單。

要啟用依賴關係圖，請使用變數選項。

**啟用或禁用探查器**:

1. 登錄到Commerce伺服器。
1. 更改到Commerce安裝目錄。
1. 作為檔案系統所有者，啟用探查器：

   使用類型啟用探查器 `html` 並建立flagfile:

   ```bash
   bin/magento dev:profiler:enable html
   ```

   使用類型啟用探查器 `csvfile` 並建立flagfile:

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   輸出將保存到 `<project-root>/var/log/profiler.csv`。 的 `profiler.csv` 在每頁刷新時被覆蓋。

   要禁用探查器並刪除flagfile:

   ```bash
   bin/magento dev:profiler:disable
   ```

<!-- link definitions -->

[csvfile]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php
[html]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php
[profiler]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler.php
