---
title: 配置資料庫探查器
description: 請參見如何配置資料庫探查器的輸出示例。
contributor_name: Atish Goswami
contributor_link: http://atishgoswami.com
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# 配置資料庫探查器

Commerce資料庫探查器顯示在頁面上實現的所有查詢，包括每個查詢的時間和應用了哪些參數。

## 步驟1:修改部署配置

修改 `<magento_root>/app/etc/env.php` 將以下引用添加到 [資料庫profiler類](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/DB/Profiler.php):

```php?start_inline=1
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
```

以下示例：

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

## 步驟2:配置輸出

在Commerce應用程式引導檔案中配置輸出；這可能 `<magento_root>/pub/index.php` 或者它可以位於Web伺服器虛擬主機配置中。

下面的示例在三清單中顯示結果：

- 總時間（顯示在頁面上運行所有查詢的總時間）
- SQL(顯示所有SQL查詢；行標題顯示查詢計數)
- 查詢參數（顯示每個SQL查詢的參數）

要配置輸出，請在 `$bootstrap->run($app);` 引導檔案中的行：

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

## 第3步：查看結果

轉到店面或管理員中的任何頁面以查看結果。 示例如下：

![示例資料庫探查器結果](../../assets/configuration/db-profiler-results.png)
