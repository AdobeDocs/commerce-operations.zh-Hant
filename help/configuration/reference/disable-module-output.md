---
title: 停用模組輸出
description: 瞭解如何停用模組輸出。
exl-id: af556bf5-8454-4d65-8ac8-4a64c108f092
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# 停用模組輸出

依預設，所有模組都設定為可將模組輸出寫入檢視。 關閉輸出可讓您基本上停用因硬性相依性而無法停用的模組。

例如，`Customer`模組相依於`Review`模組，因此無法停用`Review`模組。 但是，如果您不希望客戶提供評論，則可關閉`Review`模組的輸出。

>[!INFO]
>
>如果商家使用管理員在舊版中停用模組輸出，您必須手動設定系統以移轉這些設定。

停用輸出功能會在下列類別中執行：

- [\Magento\Framework\View\Element\AbstractBlock：：toHtml](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [\Magento\Backend\Block\Template：：isOutputEnabled](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>停用模組輸出並不會停用模組。 此模組保持已啟用狀態並運作，但前端或後端不會轉譯任何區塊、頁面或欄位。

## 停用管道部署中的模組輸出

若要在具有Commerce應用程式的多個執行個體的管道部署或任何其他部署中停用模組輸出：

1. 編輯`Backend`模組的`config.xml`檔案。
1. 匯出組態變更。

### 編輯`Backend`模組`config.xml`檔案

1. 封存原始`config.xml`檔案。
1. 將類似下列的行新增至`<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml`檔案，直接在`<default>`元素下方：

   ```xml
   <advanced>
       <modules_disable_output>
           <Magento_Newsletter>1</Magento_Newsletter>
       </modules_disable_output>
   </advanced>
   ```

   此處：

   - `<modules_disable_output>`包含模組清單。
   - `<Magento_Newsletter></Magento_Newsletter>`指定要停用輸出的模組。
   - `1`是停用`Magento_Newsletter`模組輸出的旗標。

此設定的範例結果是，客戶無法再註冊接收電子報。

### 匯出設定變更

執行以下命令以匯出組態變更：

```bash
bin/magento app:config:dump
```

結果會寫入`<Magento_install_dir>/app/etc/config.php`檔案。

接下來，清除快取以啟用新設定：

```bash
bin/magento cache:clean config
```

請參閱[匯出組態](../cli/export-configuration.md)。

## 在簡單部署中停用模組輸出

在Commerce的單一例項上停用模組輸出的程式較簡單，因為變更不一定要散發。

1. 封存原始`<Magento_install_dir>/app/etc/config.php`檔案。
1. 將`advanced`和`modules_disable_output`區段新增至`config.php`檔案（如果這兩個區段不存在）：

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

在此範例中，`Magento_Review`模組的輸出已停用，客戶無法再檢閱產品。
若要重新啟用輸出，請將值設為`0`。
