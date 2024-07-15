---
title: 使用共用設定的範例
description: 請參閱範例，瞭解如何使用共用組態檔來變更開發系統中的設定。
exl-id: c980ec01-ca2d-43db-b68d-8e9435e07e6a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# 使用共用設定的範例

此範例說明如何在開發系統中變更下列設定、更新組建系統中的共用組態檔`config.php`，以及在生產系統中實作相同的設定：

- 時區
- 重量單位

這些設定可在&#x200B;**商店** >設定> **設定** >一般> **一般**&#x200B;中的管理員中使用。

您可以使用相同的程式來設定下列參照中任何非敏感的、非系統特定的設定：

- [其他設定路徑參考](../reference/config-reference-general.md)
- [付款設定路徑參考](../reference/config-reference-payment.md)
- [Commerce Enterprise B2B擴充功能設定路徑參考](../reference/config-reference-b2b.md)

## 開始之前

開始之前，請設定檔案系統許可權和擁有權，如[開發、建置和生產系統的先決條件](../deployment/prerequisites.md)中所述。

## 假設

本主題提供修改生產系統組態的範例。 您可以視需要選擇不同的組態選項。

在本範例中，我們假設如下：

- 您使用Git原始檔控制
- 開發系統可在名為`mconfig`的Git遠端存放庫中取得
- 您的Git工作分支名為`m2.2_deploy`

## 步驟1：在開發系統中設定設定

若要設定開發系統中的時區和加權單位：

1. 登入管理員。
1. 按一下&#x200B;**商店** >設定> **組態** >一般> **一般**。
1. 在右窗格中，展開&#x200B;**地區設定選項**。

   下圖顯示一個範例。

   ![在開發系統中設定地區設定選項](../../assets/configuration/split-deploy-set-locale.png)

1. 從&#x200B;**時區**&#x200B;清單，按一下&#x200B;**GMT+00:00 (UTC)**。
1. 清除&#x200B;**加權單位**&#x200B;欄位旁的&#x200B;**使用系統值**&#x200B;核取方塊。
1. 從&#x200B;**重量單位**&#x200B;清單，按一下&#x200B;**公斤**。
1. 按一下&#x200B;**儲存設定**。
1. 如果出現提示，請排清快取。

## 步驟2：更新共用設定

依照本節所述，在您的開發系統中產生共用組態檔`app/etc/config.php`，並使用原始檔控制將其傳輸至您的組建系統。

{{$include /help/_includes/config-save-config.md}}

## 步驟3：更新您的建置系統並產生檔案

現在您已確認將共用組態的變更提交至原始檔控制，您可以在建置系統中提取這些變更、編譯程式碼，並產生靜態檔案。 最後一個步驟是將這些變更提取至您的生產系統。 因此，您的生產系統的設定將與您的開發系統相符。

{{$include /help/_includes/config-update-build-system.md}}

## 步驟4：更新生產系統

該流程的最後一步是從原始檔控制更新您的生產系統。 這會提取您在開發和建立系統時所做的所有變更，這表示您的生產系統完全處於最新狀態。

{{$include /help/_includes/config-update-prod-system.md}}

### 驗證管理員中的變更

**若要確認這些設定在Admin**&#x200B;中不可編輯：

1. 登入管理員。
1. 按一下&#x200B;**商店** >設定> **組態** >一般> **一般**。
1. 在右窗格中，展開&#x200B;**地區設定選項**。

   您剛才設定的選項顯示如下：

   在Admin](../../assets/configuration/split-deploy-not-editable.png)中無法編輯![設定選項

>[!INFO]
>
>若要變更在Admin中鎖定的設定，請使用[`magento config:set --lock`命令](../cli/set-configuration-values.md)。
