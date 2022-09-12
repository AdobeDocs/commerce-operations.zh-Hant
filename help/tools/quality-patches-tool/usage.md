---
title: 使用狀況
description: 了解如何使用 [!DNL Quality Patches Tool].
source-git-commit: 356ee307e0199d70c0e391e0d903e8f2e1600e63
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 0%

---

# 使用狀況

此 [質量修補工具](https://github.com/magento/quality-patches) 提供由Adobe和Magento Open Source社區開發的單個補丁。 它允許您應用、恢復和查看有關所有單個修補程式的一般資訊，這些修補程式可用於已安裝的Adobe Commerce版本或Magento Open Source。 您可以將修補程式應用到Adobe Commerce和Magento Open Source項目，而不管誰開發了修補程式。 例如，您可以將社群開發的修補程式套用至Adobe Commerce專案。


>[!INFO]
> 
>請參閱 [應用單個修補程式](#apply-individual-patches) 以取得將修補程式套用至Adobe Commerce或Magento Open Source專案的說明。 請參閱 [可用修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 查看已發行修補程式的完整清單。

>[!WARNING]
>
>不建議使用 [!DNL Quality Patches Tool] 應用大量修補程式，因為它增加了代碼的複雜性，並使升級到新版本更加困難。

## 安裝

>[!INFO]
> 
>如果尚未安裝，則必須安裝 [Git](https://github.com/git-guides/install-git) 或 [修補程式](https://man7.org/linux/man-pages/man1/patch.1.html) 安裝之前 [!DNL Quality Patches Tool]. 新增 `magento/quality-patches` 撰寫器套件至您的 `composer.json` 檔案：

```bash
composer require magento/quality-patches
```

## 查看單個修補程式

要查看適用於您的Adobe Commerce或Magento Open Source版本的單個修補程式清單：

```bash
./vendor/bin/magento-patches status
```

您會看到類似下列的輸出：

| Id | 標題 | 類型 | 狀態 | 詳細資料 |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | 部署期間FPC已停用 | 可選 | 未應用 | 受影響的元件：<br> - magento/module-page-cache |
| MCLOUD-5650 | 從檔案讀取後保留部署配置 | 可選 | 未應用 | 受影響的元件：<br> - magento/framework |
| MCLOUD-5684 | 分頁無法運作 — product_list_limit=all | 可選 | 未應用 | 受影響的元件：- magento/module-elasticsearch |
| MCLOUD-5837 | 修正負載平衡器問題 | 已棄用 | 已套用 | 建議替換：MC-1 <br> 受影響的元件：- magento/framework |
| BUNDLE-2554 | 設定付款資訊錯誤 | 可選 | 未應用 | 受影響的元件： <br>- amzn/amazon-pay-module |
| MC-1 | 修正問題1 | 可選 | 已套用 | 受影響的元件： <br> - magento/module-cms |
| MC-2 | 修正問題2 | 可選 | 未應用 | 受影響的元件： <br> - magento/module-cms |
| MC-3 | 修正問題3 | 可選 | 未應用 | 所需的修補程式：<br> - MC-2 <br>受影響的元件： <br>- magento/module-cms |
| MC-3-V2 | 更新問題3的修正，取代MC-3修補程式 | 可選 | 不適用 | 受影響的元件：  <br>- magento/module-cms |

Adobe Commerce 2.3.5。

狀態表包括：

- **類型**:
   - `Optional`  — 來自 [!DNL Quality Patches Tool] 和 [雲修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) 套件是Adobe Commerce和Magento Open Source安裝的選用套件。
   - `Deprecated` —Adobe已棄用個別修補程式。 如果已應用修補程式，建議您恢復該修補程式。 還原操作還從狀態表中刪除了修補程式。

- **狀態**:
   - `Applied`  — 已應用修補程式。
   - `Not applied`  — 尚未應用修補程式。
   - `N/A`  — 由於衝突，無法定義修補程式的狀態。

- **詳細資料**:
   - `Affected components`  — 受影響模組的清單。
   - `Required patches`  — 必須應用的修補程式清單，以使指示的修補程式正常工作（依賴項）。
   - `Recommended replacement`  — 建議替換已廢止的修補程式的修補程式。

>[!INFO]
> 
>升級到新版本的Adobe Commerce或Magento Open Source後，如果新版本中未包含修補程式，則必須重新應用修補程式。 請參閱 [升級後重新應用修補程式](#re-apply-patches-after-an-upgrade).

## 應用單個修補程式 {#apply-individual-patches}

>[!WARNING]
>
>在部署到生產環境之前，最好先測試測試或開發環境中的所有修補程式。 還建議在應用修補程式之前備份資料。 請參閱 [備份並回滾檔案系統](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

要應用單個修補程式，請運行以下命令，其中 `MAGETWO-XXXX` 是在狀態表中指定的修補程式ID:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

您還可以將每個附加修補程式ID與一個空格分開，以同時應用多個修補程式：

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

套用修補程式後，您必須清除快取，才能查看Adobe Commerce應用程式中的變更：

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>請考慮將應用的修補程式清單保留在單獨的位置。 升級至新版Adobe Commerce或Magento Open Source後，您可能需要重新套用其中一部分。 請參閱 [升級後重新應用修補程式](#re-apply-patches-after-an-upgrade).

## 恢復單個修補程式

>[!WARNING]
>
>在部署到生產環境之前，最好先測試測試或開發環境中的所有修補程式。 還建議在應用修補程式之前備份資料。 請參閱 [備份並回滾檔案系統](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

要恢復單個修補程式，請運行以下命令，其中 `MAGETWO-XXXX` 是在狀態表中指定的修補程式ID:

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX
```

此外，您還可以將每個附加修補程式ID與一個空格分開，以同時還原多個修補程式：

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX MAGETWO-YYYY
```

要恢復所有應用的修補程式：

```bash
./vendor/bin/magento-patches revert --all
```

還原修補程式後，您必須清除快取，才能查看Adobe Commerce應用程式中的變更：

```bash
./bin/magento cache:clean
```

## 取得更新

Adobe Commerce會定期發行新的個別修補程式。 您必須更新 [!DNL Quality Patches Tool] 要獲取新的單個修補程式，請執行以下操作：

```bash
composer update magento/quality-patches
```

查看添加的修補程式：

>[!TIP]
>
>新的添加修補程式顯示在表的底部。

```bash
./vendor/bin/magento-patches status
```

## 升級後重新應用修補程式 {#re-apply-patches-after-an-upgrade}

升級到新版本的Adobe Commerce或Magento Open Source時，如果新版本中未包含補丁程式，則必須重新應用補丁程式。

要重新應用修補程式，請執行以下操作：

1. 更新 [!DNL Quality Patches Tool]:

   ```bash
   composer update magento/quality-patches.
   ```

1. 開啟先前應用的修補程式清單，該清單建議於 [應用單個修補程式](#apply-individual-patches).

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
   >當您執行 `status` 命令，則新版本中包含的修補程式不再顯示在可用修補程式表中。

## 記錄

此 [!DNL Quality Patches Tool] 記錄 `<Magento_root>/var/log/patch.log` 檔案。
