---
title: 資料遷移後續工作
description: 瞭解如何驗證您的Magento1到Magento2資料遷移是否成功，以及所有功能是否按預期工作。
exl-id: a55f357b-6c95-49d6-b2f1-c2e403a8c85f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# 資料遷移後續工作

Magento1的某些行為和邏輯在Magento2中得到了不同的實施。 的 [!DNL Data Migration Tool] 好好照顧。 您應該瞭解一些遷移方面，有時您必須執行一些小步驟，才能使某些功能在遷移後順利工作。

## 資訊

### 不支援拆分資料庫

的 [!DNL Data Migration Tool] 不支援剝離資料庫。

### 組價格轉換為層價格

在遷移期間，所有組價格將自動轉換為層價格。

### 銷售實體的新編號

訂單、發票、發運、貸項通知單和RMA的參考編號按原樣遷移。 遷移後，將應用新的Magento2編號分配規則。 新銷售實體的數值不同。

## 步驟

### 重新保存客戶細分 [僅Adobe Commerce]

遷移後，必須從「管理面板」中恢復客戶段，以使其啟動並運行。

### 配置時區

該工具不遷移時區設定，因此在遷移後必須手動配置時區 **商店** > **配置** > **區域設定選項** > **時區**。

預設情況下，Magento將時間資料儲存在資料庫的UTC-0區域中，並根據當前時區設定顯示它。 如果時間資料已保存在UTC-0以外的區域的資料庫中，則必須使用 [!DNL Data Migration Tool]`s `\Migration\Handler\Timezone` 處理程式。

在以下示例中，Magento1在資料庫的UTC-7區域中錯誤地節省了時間（例如，由於第三方擴展有故障）。 要在遷移時將客戶帳戶建立時間正確轉換為UTC-0區域，請執行以下步驟：

1. 複製 `map-customer.xml.dist` 的相應目錄下的配置檔案 [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`) `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml` 的子菜單。

1. 更新 `<customer_map_file>` 節點 `config.xml` 並刪除 `.dist` 擴展 `map-customer.xml.dist`

1. 將以下規則添加到 `map-customer.xml` 檔案：

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
