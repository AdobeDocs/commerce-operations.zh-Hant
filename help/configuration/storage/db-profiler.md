---
title: 配置資料庫探查器
description: 請參見有關如何配置資料庫探查器輸出的示例。
badge: label="由Atish Goswami貢獻" type="Informity" url="https://github.com/atishgoswami" tooltip="Atish Goswami"
source-git-commit: bcb995ea417423b0cbc59c035ba5fdedbce3310e
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---


# 配置資料庫探查器

Commerce資料庫探查器顯示頁面上實現的所有查詢，包括每個查詢的時間以及應用了哪些參數。

## 步驟1:修改部署配置

修改 `<magento_root>/app/etc/env.php` 將以下引用添加到 [資料庫探查器類](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/DB/Profiler.php):

```php?start_inline=1
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
```

以下範例：

```php?start_inline=1
 'db' =>
  array (
    'table_prefix' => '',
    'connection' =>
    array (
      'default' =>
      array (
        'host' => 'localhost',
        'dbname' => 'magento',
        'username' => 'magento',
        'password' => 'magento',
        'model' => 'mysql4',
        'engine' => 'innodb',
        'initStatements' => 'SET NAMES utf8;',
        'active' => '1',
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
      ),
    ),
  ),
```

## 步驟2:設定輸出

在您的商務應用程式引導檔案中設定輸出；可能是 `<magento_root>/pub/index.php` 或者，它可以位於web伺服器虛擬主機配置中。

以下範例顯示三欄表格中的結果：

- 總時間（顯示在頁面上執行所有查詢的總時間量）
- SQL(顯示所有SQL查詢；列標題顯示查詢的計數)
- 查詢參數（顯示每個SQL查詢的參數）

若要設定輸出，請在 `$bootstrap->run($app);` 引導檔案中的行：

```php?start_inline=1
/** @var \Magento\Framework\App\ResourceConnection $res */
$res = \Magento\Framework\App\ObjectManager::getInstance()->get('Magento\Framework\App\ResourceConnection');
/** @var Magento\Framework\DB\Profiler $profiler */
$profiler = $res->getConnection('read')->getProfiler();
echo "<table cellpadding='0' cellspacing='0' border='1'>";
echo "<tr>";
echo "<th>Time <br/>[Total Time: ".$profiler->getTotalElapsedSecs()." secs]</th>";
echo "<th>SQL [Total: ".$profiler->getTotalNumQueries()." queries]</th>";
echo "<th>Query Params</th>";
echo "</tr>";
foreach ($profiler->getQueryProfiles() as $query) {
    /** @var Zend_Db_Profiler_Query $query*/
    echo '<tr>';
    echo '<td>', number_format(1000 * $query->getElapsedSecs(), 2), 'ms', '</td>';
    echo '<td>', $query->getQuery(), '</td>';
    echo '<td>', json_encode($query->getQueryParams()), '</td>';
    echo '</tr>';
}
echo "</table>";
```

## 步驟3:查看結果

前往店面或管理員中的任何頁面檢視結果。 範例如下：

![資料庫探查器結果示例](../../assets/configuration/db-profiler-results.png)
