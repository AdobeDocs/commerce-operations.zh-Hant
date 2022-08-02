---
title: 使用環境變數的示例
description: 請參見如何使用環境變數在開發系統中設定共用值、系統特定值和敏感值的示例。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '1085'
ht-degree: 0%

---


# 使用環境變數的示例

此示例說明如何在開發系統中設定共用值、系統特定值和敏感值，然後使用共用配置的組合來設定生產系統中的所有值， `config.php`和PHP環境變數。

這些配置設定可以在開發系統和生產系統之間共用：

增值稅編號和商店名稱 **商店** >設定> **配置** >常規> **常規**

這些配置設定是特定於系統的或敏感的，如所示：

- 將電子郵件發送到（敏感） **商店** >設定> **配置** >常規> **聯繫人**
- 預設電子郵件域（系統特定） **商店** >設定> **配置** >客戶> **客戶配置** > **建立新帳戶選項**

可以使用同一過程配置以下參照中的任何設定：

- [敏感和特定於系統的配置路徑參考](../reference/config-reference-sens.md)
- [付款配置路徑引用](../reference/config-reference-payment.md)
- [常規配置路徑引用](../reference/config-reference-general.md)
- [Commerce Enterprise B2B擴展配置路徑參考](../reference/config-reference-b2b.md)

## 開始之前

開始之前，請設定檔案系統權限和所有權，如中所述 [開發、構建和生產系統的先決條件](../deployment/prerequisites.md)。

## 假設

本主題提供了修改生產系統配置的示例。 如果需要，可以選擇不同的配置選項。

在本示例中，我們假定：

- 您使用Git原始碼管理
- 開發系統可在名為Git的遠程儲存庫中使用 `mconfig`
- 您的Git工作分支已命名 `m2.2_deploy`

## 步驟1:在開發系統中設定配置

要在開發系統中設定預設的區域設定和重量單位，請執行以下操作：

1. 登錄到管理員。
1. 按一下 **商店** >設定> **配置** >常規> **常規**。
1. 如果您有多個網站可用，請使用 **儲存視圖** 清單中，可切換到其他網站，如下圖所示。

   ![切換網站](../../assets/configuration/split-deploy-switch-website.png)

1. 在右窗格中，展開 **儲存資訊**。
1. 如有必要，請清除 **使用預設值** 複選框 **增值稅編號** 的子菜單。
1. 在欄位中輸入數字(例如， `12345`)。
1. 在 **儲存名稱** 欄位，輸入值(如 `My Store`)。
1. 按一下 **保存配置**。
1. 使用 **儲存視圖** 清單 **預設配置** 如下圖所示。

   ![切換到預設配置](../../assets/configuration/split-deploy-default-config.png)

1. 在左導航的「General（常規）」下，按一下 **聯繫人**。
1. 清除 **使用預設值** 複選框 **將電子郵件發送到** 的子菜單。
1. 在欄位中輸入電子郵件地址。
1. 按一下 **保存配置**。
1. 在左窗格中，按一下「Customers（客戶）」> **客戶配置**。
1. 在右窗格中，展開 **建立新帳戶選項**。
1. 清除 **使用系統值** 複選框 **預設電子郵件域** 的子菜單。
1. 在欄位中輸入域名。
1. 按一下 **保存配置**。
1. 如果出現提示，刷新快取。

## 步驟2:更新配置

現在您已更改了管理中的配置，請將共用配置寫入檔案，如本節所述。

{{$include /help/_includes/config-save-config.md}}

注意，即使 `app/etc/env.php` （系統特定的配置）已更新，請勿將其簽入原始碼管理。 稍後，您將在此過程中在生產系統上建立相同的配置設定。

## 第3步：更新生成系統並生成檔案

現在，您已將對共用配置所做的更改提交到原始碼管理，您可以在生成系統中提取這些更改、編譯代碼並生成靜態檔案。 最後一步是將這些更改拉入生產系統。

{{$include /help/_includes/config-update-build-system.md}}

## 第4步：更新生產系統

此過程中的最後一步是更新生產系統。 必須分兩部分完成：

- 更新敏感和系統特定的設定
- 更新共用設定

### 更新敏感和系統特定的設定

要使用環境變數設定敏感和系統特定的設定，必須知道以下內容：

- 每個設定的作用域

   如果按照步驟1中的說明操作，則「將電子郵件發送到」的範圍是全局的（即預設配置範圍），「預設電子郵件域」的範圍是網站。

   您必須知道網站的代碼才能設定預設電子郵件域配置值。 請參閱 [使用環境變數覆蓋配置設定](../reference/override-config-settings.md#environment-variables) 的子菜單。

- 每個設定的配置路徑

   本示例中使用的配置路徑如下：

   | 設定名稱 | 配置路徑 |
   |--------------|--------------|
   | 將電子郵件發送到 | `contact/email/recipient_email` |
   | 預設電子郵件域 | `customer/create_account/email_domain` |

   您可以在中找到所有敏感和特定於系統的配置路徑 [敏感和特定於系統的配置路徑參考](../reference/config-reference-sens.md)。

#### 將配置路徑轉換為變數名

如中所述 [使用環境變數覆蓋配置設定](../reference/override-config-settings.md#environment-variables)，變數格式為：

```text
<SCOPE>__<SYSTEM__VARIABLE__NAME>
```

值 `<SCOPE>` 是 `CONFIG__DEFAULT__` 用於全局範圍或 `CONFIG__WEBSITES__<WEBSITE CODE>` 的子菜單。

查找的值 `<SYSTEM__VARIABLE__NAME>`替換 `/` 配置路徑中的字元，帶有兩個下划線。

變數名稱如下：

| 名稱 | 配置路徑 | 變數名稱 |
|--------------|--------------|--------------|
| 將電子郵件發送到 | `contact/email/recipient_email` | `CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL` |
| 預設電子郵件域 | `customer/create_account/email_domain` | `CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN` |

>[!INFO]
>
>上表有網站代碼示例， `BASE`，用於預設電子郵件域配置設定。 替換 `BASE` 你商店的相應網站代碼。

#### 使用環境變數設定變數

可以在 `index.php` 使用以下格式：

```php
$_ENV['VARIABLE'] = 'value';
```

**設定變數值**:

1. 以檔案系統所有者身份或切換到檔案系統所有者身份登錄到生產系統。
1. 開啟 `<Commerce root dir>/pub/index.php` 的子菜單。
1. 位於 `index.php`，為類似於以下內容的變數設定值：

   ```php
   $_ENV['CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL'] = 'myname@example.com';
   $_ENV['CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN'] = 'magento.com';
   ```

1. 將更改保存到 `pub/index.php` 並退出文本編輯器。
1. 繼續下一節。

### 更新共用設定

本節討論如何獲取您在開發和構建系統上所做的所有更改，這些更改將更新共用配置設定（儲存名和增值稅號）。

{{$include /help/_includes/config-update-prod-system.md}}

### 驗證管理員中的配置設定

本節討論如何在生產系統管理中驗證配置設定。

**驗證配置設定**:

1. 登錄到生產系統的Admin。
1. 按一下 **商店** >設定> **配置** >常規> **常規**。
1. 使用 **儲存視圖** 清單，以切換到其他網站。

   在開發系統中設定的共用配置選項如下所示。

   ![檢查生產系統中的設定](../../assets/configuration/split-deploy-verify-storeinfo.png)

   >[!INFO]
   >
   >的 **儲存名稱** 欄位在網站範圍中是可編輯的，但如果切換到預設配置範圍，則不可編輯。 這是您在開發系統中設定選項的結果。 值 **增值稅編號** 在網站範圍中不可編輯。

1. 如果尚未這樣做，請切換到預設配置作用域。
1. 在左導航的「General（常規）」下，按一下 **聯繫人**。

   的 **將電子郵件發送到** 欄位不可編輯，如下圖所示。 這是敏感設定。

   ![檢查生產系統中的設定](../../assets/configuration/split-deploy-verify-contacts.png)

1. 在左窗格中，按一下「Customers（客戶）」> **客戶配置**。
1. 在右窗格中，展開 **建立新帳戶選項**。

   的值 **預設電子郵件域** 的下界。 這是特定於系統的設定。

   ![檢查生產系統中的設定](../../assets/configuration/split-default-domain.png)
