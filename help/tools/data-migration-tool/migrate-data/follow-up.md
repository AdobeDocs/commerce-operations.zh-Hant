---
title: 資料移轉後續追蹤
description: 瞭解如何驗證您的Magento1到Magento2資料移轉是否成功，以及所有功能是否如預期般運作。
exl-id: a55f357b-6c95-49d6-b2f1-c2e403a8c85f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# 資料移轉後續追蹤

Magento1的某些行為和邏輯在Magento2中的實施方式不同。 此 [!DNL Data Migration Tool] 會處理好的。 有些移轉方面您應有所瞭解，有時您必須採取次要步驟，才能讓某些功能在移轉後順暢運作。

## 資訊

### 不支援分割資料庫

此 [!DNL Data Migration Tool] 不支援分割資料庫。

### 群組價格轉換為階層價格

所有群組價格都會在移轉期間自動轉換為層級價格。

### 銷售實體的新編號

訂單、商業發票、出貨、銷退折讓單及RMA的參考編號依原樣移轉。 移轉後，將套用新的Magento2編號指派規則。 新銷售實體的數字不同。

## 步驟

### 重新儲存客戶區段 [僅限Adobe Commerce]

移轉後，必須從「管理面板」重新儲存客戶區段，才能使其啟動並執行。

### 設定時區

工具不會移轉時區設定，因此您必須在移轉後手動設定時區。 **商店** > **設定** > **地區設定選項** > **時區**.

依預設，Magento會將時間資料儲存在資料庫的UTC-0區域中，並根據目前的時區設定加以顯示。 如果時間資料已經儲存在UTC-0以外的資料庫區域中，您必須使用 [!DNL Data Migration Tool]的 `\Migration\Handler\Timezone` 處理常式。

在下列範例中，Magento1在資料庫的UTC-7區域中儲存的時間不正確（例如，由於第三方擴充功能發生錯誤）。 若要在移轉時正確地將客戶帳戶建立時間轉換為UTC-0區域，請執行下列步驟：

1. 複製 `map-customer.xml.dist` 組態檔的適當目錄 [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`)至 `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml` 檔案。

1. 更新 `<customer_map_file>` 中的節點 `config.xml` 並移除 `.dist` 擴充功能來自 `map-customer.xml.dist`

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
