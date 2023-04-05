---
title: 資料移轉後續行動
description: 了解如何驗證Magento1到Magento2的資料移轉是否成功，且所有功能皆如預期般運作。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 資料移轉後續行動

Magento1的某些行為和邏輯在Magento2中已不同實作。 此 [!DNL Data Migration Tool] 照顧好它。 您應了解一些移轉方面，有時您必須執行微幅步驟，讓部分功能在移轉後能順利運作。

## 資訊

### 不支援拆分資料庫

此 [!DNL Data Migration Tool] 不支援拆分資料庫。

### 轉換為層價的組價

在遷移期間，所有組價格都會自動轉換為層價格。

### 銷售實體的新編號

訂單、發票、發運、貸項通知單和RMA的參考編號按原樣遷移。 遷移後，將應用新的Magento2編號分配規則。 新銷售實體的數值不同。

## 步驟

### 儲存客戶區段 [僅限Adobe Commerce]

移轉後，必須從「管理面板」移除客戶區段，才能順利啟動並執行。

### 配置時區

此工具不會移轉時區設定，因此您在移轉後必須手動配置時區，位置為 **商店** > **設定** > **地區選項** > **時區**.

預設情況下，Magento將時間資料儲存在資料庫的UTC-0區域中，並根據當前時區設定顯示它。 如果時間資料已儲存在UTC-0以外的區域，則必須使用 [!DNL Data Migration Tool]&#39;s `\Migration\Handler\Timezone` 處理常式。

在以下範例中，Magento1在資料庫的UTC-7區域內（例如，由於有錯誤的第三方擴充功能）不正確地節省時間。 要在遷移時將客戶帳戶建立時間正確轉換為UTC-0區域，請執行以下步驟：

1. 複製 `map-customer.xml.dist` 配置檔案(位於 [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`)進入 `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml` 檔案。

1. 更新 `<customer_map_file>` 節點 `config.xml` 並移除 `.dist` 延伸功能 `map-customer.xml.dist`

1. 將下列規則新增至 `map-customer.xml` 檔案：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="../map.xsd">
  <!--...-->
  <destination>
      <field_rules>
          <!--...-->
          <transform>
              <field>customer_entity.created_at</field>
              <handler class="\Migration\Handler\Timezone">
                  <param name="offset" value="-7" />
              </handler>
          </transform>
      </field_rules>
  </destination>
</map>
```
