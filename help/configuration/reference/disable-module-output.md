---
title: 禁用模組輸出
description: 瞭解如何禁用模組輸出。
exl-id: af556bf5-8454-4d65-8ac8-4a64c108f092
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# 禁用模組輸出

預設情況下，所有模組都配置為可將模組輸出寫入視圖。 關閉輸出提供了一種方法，可從根本上禁用由於硬依賴而無法禁用的模組。

例如， `Customer` 模組取決於 `Review` 模組，所以 `Review` 無法禁用模組。 但是，如果您不希望客戶提供評論，則可以關閉 `Review` 中。

>[!INFO]
>
>如果商家使用管理員在以前的版本中禁用模組輸出，則必須手動配置系統以遷移這些設定。

「輸出禁用」在以下類中執行：

- [\Magento\Framework\View\Element\AbstractBlock::toHtml](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [\Magento\Backend\Block\Template::isOutputEnabled](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>禁用模組輸出不會禁用模組。 該模組仍處於啟用狀態且工作正常，但前端或後端上未呈現任何塊、頁或欄位。

## 在管道部署中禁用模組輸出

要在管道部署或任何其他部署中禁用模組輸出，請使用Commerce應用程式的多個實例：

1. 編輯 `Backend` 模組 `config.xml` 的子菜單。
1. 導出配置更改。

### 編輯 `Backend` 模組 `config.xml` 檔案

1. 存檔原始 `config.xml` 的子菜單。
1. 將類似以下行的行添加到 `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml` 檔案，直接在 `<default>` 元素：

   ```xml
   <advanced>
       <modules_disable_output>
           <Magento_Newsletter>1</Magento_Newsletter>
       </modules_disable_output>
   </advanced>
   ```

   這裡：

   - `<modules_disable_output>` 包含模組清單。
   - `<Magento_Newsletter></Magento_Newsletter>` 指定要禁用輸出的模組。
   - `1` 是禁用 `Magento_Newsletter` 中。

作為此配置的示例結果，客戶無法再註冊以接收新聞稿。

### 導出配置更改

運行以下命令以導出配置更改：

```bash
bin/magento app:config:dump
```

結果將寫入 `<Magento_install_dir>/app/etc/config.php` 的子菜單。

接下來，清除快取以啟用新設定：

```bash
bin/magento cache:clean config
```

請參閱 [導出配置](../cli/export-configuration.md)。

## 在簡單部署中禁用模組輸出

在單個Commerce實例上禁用模組輸出的過程更簡單，因為不必分發更改。

1. 存檔原始 `<Magento_install_dir>/app/etc/config.php` 的子菜單。
1. 添加 `advanced` 和 `modules_disable_output` 的 `config.php` 檔案（如果不存在）:

   ```php
   'system' =>
     array (
       'websites' =>
       array (
         'base' =>
         array (
           'advanced' =>
           array (
             'modules_disable_output' =>
             array (
               'Magento_Review' => '1',
             ),
           ),
         ),
       ),
     ),
   ```

在此示例中， `Magento_Review` 模組已禁用，客戶無法再查看產品。
要重新啟用輸出，請將值設定為 `0`。
