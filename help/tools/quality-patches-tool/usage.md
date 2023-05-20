---
title: 用法
description: 瞭解如何使用 [!DNL Quality Patches Tool]。
exl-id: f9ad37e9-2d0f-4bc8-a98b-6d60b6f56d42
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 0%

---

# 用法

的 [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) 提供由Adobe和Magento Open Source社區開發的各個修補程式。 它允許您應用、還原和查看有關可用於已安裝版本的Adobe Commerce或Magento Open Source的所有單個修補程式的一般資訊。 您可以將修補程式應用於Adobe Commerce和Magento Open Source項目，而不管是誰開發了該修補程式。 例如，您可以將社區開發的修補程式應用到Adobe Commerce項目。


看這個 [技術視頻](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/tools/quality-patch-tool.html?lang=en) 並學習如何使用「質量補丁工具」(Quality Patches Tool forAdobe Commerce和Magento Open Source)。

>[!INFO]
>
>請參閱 [應用單個修補程式](#apply-individual-patches) 有關將修補程式應用到您的Adobe Commerce或Magento Open Source項目的說明。 請參閱 [[!DNL Quality Patches Tool]:搜索修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 查看已發佈修補程式的完整清單。

>[!WARNING]
>
>建議不要使用 [!DNL Quality Patches Tool] 應用大量修補程式，因為這會增加代碼的複雜性，並使升級到新版本更加困難。

## 安裝

>[!INFO]
>
>如果尚未安裝，則必須安裝 [[!DNL Git]](https://github.com/git-guides/install-git) 或 [修補程式](https://man7.org/linux/man-pages/man1/patch.1.html) 安裝前 [!DNL Quality Patches Tool]。 添加 `magento/quality-patches` 到您的合成器包 `composer.json` 檔案：

```bash
composer require magento/quality-patches
```

## 查看單個修補程式

要查看可用於您版本的Adobe Commerce或Magento Open Source的單個修補程式清單：

```bash
./vendor/bin/magento-patches status
```

您將看到與以下內容類似的輸出：

| ID | 標題 | 類型 | 狀態 | 詳細資訊 |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | FPC在部署期間被禁用 | 可選 | 未應用 | 受影響的元件：<br> -magento/module-page-cache |
| MCLOUD-5650 | 讀取檔案後保留部署配置 | 可選 | 未應用 | 受影響的元件：<br> -magento/framework |
| MCLOUD-5684 | 分頁無效 — product_list_limit=all | 可選 | 未應用 | 受影響的元件：- magento/module elasticsearch |
| MCLOUD-5837 | 修復負載平衡器問題 | 已棄用 | 已應用 | 建議更換：MC-1 <br> 受影響的元件：-magento/framework |
| BUNDLE-2554 | 設定付款資訊錯誤 | 可選 | 未應用 | 受影響的元件： <br>- amzn/amazon付費模組 |
| MC-1 | 修復問題1 | 可選 | 已應用 | 受影響的元件： <br> - magento/module cms |
| MC-2 | 修復問題2 | 可選 | 未應用 | 受影響的元件： <br> - magento/module cms |
| MC-3 | 修復問題3 | 可選 | 未應用 | 所需的修補程式：<br> - MC-2 <br>受影響的元件： <br>- magento/module cms |
| MC-3-V2 | 已更新問題3的修復程式，取代MC-3修補程式 | 可選 | 不適用 | 受影響的元件：  <br>- magento/module cms |

Adobe Commerce2.3.5

狀態表包括：

- **類型**:
   - `Optional`  — 來自的所有修補程式 [!DNL Quality Patches Tool] 和 [Commerce on Cloud Infrastructure指南>應用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 包是Adobe Commerce和Magento Open Source安裝的可選項。
   - `Deprecated` —Adobe已棄用單個修補程式。 如果已應用修補程式，建議您恢復該修補程式。 還原操作還會從狀態表中刪除修補程式。

- **狀態**:
   - `Applied`  — 已應用修補程式。
   - `Not applied`  — 尚未應用修補程式。
   - `N/A`  — 由於衝突，無法定義修補程式的狀態。

- **詳細資訊**:
   - `Affected components`  — 受影響模組的清單。
   - `Required patches`  — 必須應用的修補程式清單，以使指定的修補程式正常工作（依賴項）。
   - `Recommended replacement`  — 建議替換已過時修補程式的修補程式。

>[!INFO]
>
>升級到新版本的Adobe Commerce或Magento Open Source後，如果新版本中未包括修補程式，則必須重新應用修補程式。 請參閱 [升級後重新應用修補程式](#re-apply-patches-after-an-upgrade)。

## 應用單個修補程式 {#apply-individual-patches}

>[!WARNING]
>
>在部署到生產之前，最好先test過渡或開發環境中的所有修補程式。 還建議在應用修補程式之前備份資料。 請參閱 [備份和回滾檔案系統、介質和資料庫](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html)。

要應用單個修補程式，請運行以下命令，其中 `MAGETWO-XXXX` 是在狀態表中指定的修補程式ID:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

您還可以將每個附加的修補程式ID與一個空格分隔開來，以同時應用多個修補程式：

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

在應用修補程式後，必須清除快取，才能查看Adobe Commerce應用程式中的更改：

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>請考慮將應用的修補程式清單保留在單獨的位置。 升級到新版本的Adobe Commerce或Magento Open Source後，可能需要重新應用其中的一些。 請參閱 [升級後重新應用修補程式](#re-apply-patches-after-an-upgrade)。

## 還原單個修補程式

>[!WARNING]
>
>在部署到生產之前，最好先test過渡或開發環境中的所有修補程式。 還建議在應用修補程式之前備份資料。 請參閱 [備份和回滾檔案系統、介質和資料庫](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html)。

要恢復單個修補程式，請運行以下命令，其中 `MAGETWO-XXXX` 是在狀態表中指定的修補程式ID:

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX
```

此外，您還可以將每個附加的修補程式ID與一個空格分開，以同時還原多個修補程式：

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX MAGETWO-YYYY
```

要還原所有已應用的修補程式，請執行以下操作：

```bash
./vendor/bin/magento-patches revert --all
```

恢復修補程式後，必須清除快取，才能查看Adobe Commerce應用程式中的更改：

```bash
./bin/magento cache:clean
```

## 獲取更新

Adobe Commerce定期發佈新的單個修補程式。 必須更新 [!DNL Quality Patches Tool] 獲取新的單個修補程式：

```bash
composer update magento/quality-patches
```

查看添加的修補程式：

>[!TIP]
>
>新添加修補程式顯示在表的底部。

```bash
./vendor/bin/magento-patches status
```

## 升級後重新應用修補程式 {#re-apply-patches-after-an-upgrade}

升級到新版本的Adobe Commerce或Magento Open Source時，如果新版本中未包含修補程式，則必須重新應用修補程式。

要重新應用修補程式，請執行以下操作：

1. 更新 [!DNL Quality Patches Tool]:

   ```bash
   composer update magento/quality-patches.
   ```

1. 開啟以前應用的修補程式清單，建議在 [應用單個修補程式](#apply-individual-patches)。

1. 應用修補程式：

   ```bash
   ./vendor/bin/magento-patches apply MAGETWO-XXXX
   ```

   最佳做法是一次應用一個修補程式。

1. 清除快取：

   ```bash
   ./bin/magento cache:clean
   ```

   >[!INFO]
   >
   >運行 `status` 命令，新版本中包含的修補程式不再顯示在可用修補程式的表中。

## 記錄

的 [!DNL Quality Patches Tool] 記錄中的所有操作 `<Magento_root>/var/log/patch.log` 的子菜單。
