---
title: 使用共用配置的示例
description: 請參見如何更改開發系統中具有共用配置檔案的設定的示例。
exl-id: c980ec01-ca2d-43db-b68d-8e9435e07e6a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# 使用共用配置的示例

此示例說明如何在開發系統中更改以下設定、更新共用配置檔案、 `config.php`，並在生產系統中實現相同的設定：

- 時區
- 重量單位

這些設定在中的管理員中可用 **商店** >設定> **配置** >常規> **常規**。

可以使用同一過程在以下參考中配置任何非敏感、非系統特定的設定：

- [其他配置路徑引用](../reference/config-reference-general.md)
- [付款配置路徑引用](../reference/config-reference-payment.md)
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

要在開發系統中設定時區和重量單位，請執行以下操作：

1. 登錄到管理員。
1. 按一下 **商店** >設定> **配置** >常規> **常規**。
1. 在右窗格中，展開 **區域設定選項**。

   下圖顯示了一個示例。

   ![在開發系統中設定區域設定選項](../../assets/configuration/split-deploy-set-locale.png)

1. 從 **時區** 清單，按一下 **GMT+00:00(UTC)**。
1. 清除 **使用系統值** 複選框 **重量單位** 的子菜單。
1. 從 **重量單位** 清單，按一下 **索格**。
1. 按一下 **保存配置**。
1. 如果出現提示，刷新快取。

## 步驟2:更新共用配置

生成共用配置檔案， `app/etc/config.php`，並使用原始碼管理將其傳輸到構建系統，如本節所述。

{{$include /help/_includes/config-save-config.md}}

## 第3步：更新生成系統並生成檔案

現在，您已將對共用配置所做的更改提交到原始碼管理，您可以在生成系統中提取這些更改、編譯代碼並生成靜態檔案。 最後一步是將這些更改拉入生產系統。 因此，生產系統的配置將與開發系統相匹配。

{{$include /help/_includes/config-update-build-system.md}}

## 第4步：更新生產系統

流程中的最後一步是從原始碼管理更新生產系統。 這將拉動您在開發和構建系統上所做的所有更改，這意味著您的生產系統是完全最新的。

{{$include /help/_includes/config-update-prod-system.md}}

### 驗證管理員中的更改

**要驗證這些設定是否在管理員中不可編輯**:

1. 登錄到管理員。
1. 按一下 **商店** >設定> **配置** >常規> **常規**。
1. 在右窗格中，展開 **區域設定選項**。

   您剛才設定的選項如下所示：

   ![配置選項在管理中不可編輯](../../assets/configuration/split-deploy-not-editable.png)

>[!INFO]
>
>要更改在管理員中鎖定的設定，請使用 [`magento config:set --lock` 命令](../cli/set-configuration-values.md)。
