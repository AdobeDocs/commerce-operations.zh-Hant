---
title: 使用CLI命令的示例
description: 請參見如何使用命令行在開發系統中設定共用值、系統特定值和敏感值的示例。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 0%

---


# 使用CLI命令的示例

此示例說明如何在開發系統中設定共用值、系統特定值和敏感值，然後將這些值部署到生產系統。
這是通過使用共用配置組合( `config.php` 檔案和Commerce CLI命令。

此示例使用以下配置設定：

- **增值稅編號** 和 **儲存名稱** 的子菜單。

   這些在 **商店** >設定> **配置** >常規> **常規**。

- **將電子郵件發送到** 為敏感配置值。

   在 **商店** >設定> **配置** >常規> **聯繫人**。

- **預設電子郵件域** 特定於系統的配置值。

   在 **商店** >設定> **配置** >客戶> **客戶配置** > **建立新帳戶選項**。

可以使用本示例中所示的相同過程來配置以下參照中的任何設定：

- [敏感和特定於系統的配置路徑參考](../reference/config-reference-sens.md)
- [付款配置路徑引用](../reference/config-reference-payment.md)
- [其他配置路徑引用](../reference/config-reference-general.md)
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
1. 如有必要，請清除 **使用預設值** 複選框 **增值稅編號** 和 **儲存名稱** 的子菜單。
1. 在欄位中輸入數字(例如， `12345`)。
1. 在 **儲存名稱** 欄位，輸入值(如 `My Store`)。
1. 按一下 **保存配置**。
1. 在左導航的「General（常規）」下，按一下 **聯繫人**。
1. 在右窗格中，展開 **電子郵件選項**。
1. 如有必要，請清除 **使用預設值** 複選框 **將電子郵件發送到** 的子菜單。
1. 在欄位中輸入電子郵件地址。
1. 按一下 **保存配置**。
1. 使用 **儲存視圖** 清單 **預設配置** 如下圖所示。

   ![切換到預設配置](../../assets/configuration/split-deploy-default-config.png)

1. 在左窗格中，按一下「Customers（客戶）」> **客戶配置**。
1. 在右窗格中，展開 **建立新帳戶選項**。
1. 如有必要，請清除 **使用系統值** 複選框 **預設電子郵件域** 的子菜單。
1. 在欄位中輸入域名。
1. 按一下 **保存配置**。
1. 如果出現提示，刷新快取。

## 步驟2:更新配置

現在您已在管理中更改了配置，請按照以下步驟將共用配置寫入檔案：

{{$include /help/_includes/config-save-config.md}}

即使 `app/etc/env.php` （系統特定的配置）已更新，請勿將其簽入原始碼管理。
稍後，您將在此過程中在生產系統上建立相同的配置設定。

## 第3步：更新生成系統並生成檔案

現在，您已將對共用配置所做的更改提交到原始碼管理，您可以將這些更改拉入生成系統、編譯代碼並生成靜態檔案。

{{$include /help/_includes/config-update-build-system.md}}

## 第4步：更新生產系統

此過程中的最後一步是更新生產系統。 必須分兩部分完成：

- 更新敏感和系統特定的設定
- 更新共用設定

### 更新敏感和系統特定的設定

要使用環境變數設定敏感和系統特定的設定，必須知道以下內容：

- 每個設定的作用域

   如果您遵循步驟1中的說明，則 **將電子郵件發送到** 是網站和範圍 **預設電子郵件域** 為全局（即預設配置範圍）。

   您需要網站代碼來設定 **將電子郵件發送到** 配置值。

   有關查找此值的詳細資訊，請參閱： [使用環境變數覆蓋配置設定](../reference/override-config-settings.md#environment-variables)。

- 此示例中使用的設定的配置路徑：

   | 設定名稱 | 配置路徑 |
   | -------------------- | -------------------------------------- |
   | 將電子郵件發送到 | `contact/email/recipient_email` |
   | 預設電子郵件域 | `customer/create_account/email_domain` |

   有關所有敏感和系統特定的配置路徑，請參閱： [敏感和特定於系統的配置路徑參考](../reference/config-reference-sens.md)。

### 使用CLI命令設定變數

使用以下CLI命令設定系統特定和敏感的配置設定：

- `magento config:set` 系統特定設定
- `magento config:sensitive:set` 用於敏感設定

設定系統特定的設定 **預設電子郵件域**，在預設範圍中，使用以下命令：

```bash
bin/magento config:set customer/create_account/email_domain <email domain>
```

您不需要使用命令中的作用域，因為它是預設作用域。

設定值 **將電子郵件發送到**&#x200B;但是，您必須知道範圍類型(`website`)和範圍代碼，這可能在每個站點上都不同。

示例：

```unix
bin/magento config:sensitive:set contact/email/recipient_email --scope=website --scope-code=<website code> <email address>
```

### 更新共用設定

本節討論如何將您在開發過程中所做的所有更改並構建系統到生產環境中，以更新共用配置設定（儲存名稱和增值稅號）。

{{$include /help/_includes/config-update-prod-system.md}}

### 驗證管理員中的配置設定

要驗證配置設定：

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
