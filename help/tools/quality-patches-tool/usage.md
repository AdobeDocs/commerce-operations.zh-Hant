---
title: 使用狀況
description: 瞭解如何使用 [!DNL Quality Patches Tool]。
exl-id: f9ad37e9-2d0f-4bc8-a98b-6d60b6f56d42
feature: Configuration, Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '845'
ht-degree: 0%

---

# 使用狀況

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches)提供由Adobe和Magento Open Source社群開發的個別修補程式。 它可讓您套用、還原和檢視已安裝的Adobe Commerce版本可用的所有個別修補程式的一般資訊。 無論修補程式的開發者是誰，您都可以將修補程式套用至Adobe Commerce專案。 例如，您可以將社群開發的修補程式套用至Adobe Commerce專案。

觀看此[技術影片](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/tools/quality-patch-tool.html?lang=en)，瞭解如何使用Adobe Commerce的Quality Patches Tool。

>[!INFO]
>
>如需將修補程式套用至您的Adobe Commerce專案的指示，請參閱[套用個別修補程式](#apply-individual-patches)。 請參閱[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)，以檢視已發行修補程式的完整清單。

>[!WARNING]
>
>不建議使用[!DNL Quality Patches Tool]套用大量修補程式，因為這會增加程式碼的複雜性，並使得升級至新版本的難度增加。

## 安裝

>[!INFO]
>
>如果尚未安裝，您必須先安裝[[!DNL Git]](https://github.com/git-guides/install-git)或[修補程式](https://man7.org/linux/man-pages/man1/patch.1.html)，才能安裝[!DNL Quality Patches Tool]。 將`magento/quality-patches` Composer套件新增至您的`composer.json`檔案：

```bash
composer require magento/quality-patches
```

## 檢視個別修補程式

若要檢視適用於您Adobe Commerce版本的個別修補程式清單：

```bash
./vendor/bin/magento-patches status
```

您會看到類似下列的輸出：

| Id | 標題 | 型別 | 狀態 | 詳細資料 |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | FPC在部署期間遭到停用 | 可選 | 未套用 | 受影響的元件：<br> - magento/module-page-cache |
| MCLOUD-5650 | 從檔案讀取後保留部署設定 | 可選 | 未套用 | 受影響的元件：<br> - magento/framework |
| MCLOUD-5684 | 分頁無法運作 — product_list_limit=all | 可選 | 未套用 | 受影響的元件： - magento/module-elasticsearch |
| MCLOUD-5837 | 修正負載平衡器問題 | 已棄用 | 已套用 | 建議的取代： MC-1 <br>受影響的元件： - magento/framework |
| BUNDLE-2554 | 設定付款資訊錯誤 | 可選 | 未套用 | 受影響的元件： <br>- amzn/amazon-pay-module |
| MC-1 | 修正問題1 | 可選 | 已套用 | 受影響的元件： <br> - magento/module-cms |
| MC-2 | 修正問題2 | 可選 | 未套用 | 受影響的元件： <br> - magento/module-cms |
| MC-3 | 修正問題3 | 可選 | 未套用 | 必要的修補程式： <br> - MC-2 <br>受影響的元件： <br>- magento/module-cms |
| MC-3-V2 | 更新問題3的修正，取代MC-3修補程式 | 可選 | 不適用 | 受影響的元件： <br>- magento/module-cms |

Adobe Commerce 2.3.5。

狀態表格包括：

- **型別**：
   - Commerce `Optional` — [!DNL Quality Patches Tool]和[雲端基礎結構指南>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)套件中的所有修補程式都是Adobe Commerce安裝的選用專案。
   - `Deprecated` —Adobe已棄用個別修補程式。 如果您已套用修補程式，建議您還原修補程式。 還原作業也會從狀態表中移除修正程式。

- **狀態**：
   - `Applied` — 已套用修補程式。
   - `Not applied` — 尚未套用修補程式。
   - `N/A` — 由於發生衝突，無法定義修補程式的狀態。

- **詳細資料**：
   - `Affected components` — 受影響模組的清單。
   - `Required patches` — 必須套用才能讓指定的修補程式正常運作（相依性）的修補程式清單。
   - `Recommended replacement` — 建議用來取代已棄用修補程式的修補程式。

>[!INFO]
>
>升級至新版Adobe Commerce後，如果新版本未包含修補程式，您必須重新套用修補程式。 請參閱[升級後重新套用修補程式](#re-apply-patches-after-an-upgrade)。

## 套用個別修補程式 {#apply-individual-patches}

>[!WARNING]
>
>最佳實務是在部署至生產環境之前，先在中繼或開發環境中測試所有修補程式。 也建議您在套用修補程式前先備份資料。 請參閱[備份及復原檔案系統、媒體及資料庫](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html)。

若要套用單一修補程式，請執行以下命令，其中`MAGETWO-XXXX`是狀態表格中指定的修補程式ID：

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

您也可以在同時套用數個修補程式，方法是用空格分隔每個額外的修補程式ID：

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

套用修補程式後，您必須清除快取，才能檢視Adobe Commerce應用程式中的變更：

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>請考慮將已套用的修補程式清單儲存在不同的位置。 升級至新版Adobe Commerce後，您可能需要重新套用其中部分功能。 請參閱[升級後重新套用修補程式](#re-apply-patches-after-an-upgrade)。

## 還原個別修補程式

>[!WARNING]
>
>最佳實務是在部署至生產環境之前，先在中繼或開發環境中測試所有修補程式。 也建議您在套用修補程式前先備份資料。 請參閱[備份及復原檔案系統、媒體及資料庫](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html)。

若要還原單一修補程式，請執行以下命令，其中`MAGETWO-XXXX`是狀態表格中指定的修補程式ID：

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX
```

此外，您也可以將每個額外的修補程式ID分隔為空格，以便同時還原數個修補程式：

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX MAGETWO-YYYY
```

若要還原所有套用的修補程式：

```bash
./vendor/bin/magento-patches revert --all
```

還原修補程式後，您必須清除快取，才能檢視Adobe Commerce應用程式中的變更：

```bash
./bin/magento cache:clean
```

## 取得更新

Adobe Commerce會定期發行新的個別修補程式。 您必須更新[!DNL Quality Patches Tool]以取得新的個別修補程式：

```bash
composer update magento/quality-patches
```

檢視新增的修補程式：

>[!TIP]
>
>新的新增修補程式會顯示在表格底部。

```bash
./vendor/bin/magento-patches status
```

## 升級後重新套用修補程式 {#re-apply-patches-after-an-upgrade}

升級至新版Adobe Commerce時，如果新版本未包含修補程式，則必須重新套用修補程式。

若要重新套用修補程式：

1. 更新[!DNL Quality Patches Tool]：

   ```bash
   composer update magento/quality-patches.
   ```

1. 開啟先前套用的修補程式清單（建議在[套用個別修補程式](#apply-individual-patches)中進行）。

1. 套用修補程式：

   ```bash
   ./vendor/bin/magento-patches apply MAGETWO-XXXX
   ```

   最佳實務是一次套用一個修補程式。

1. 清除快取：

   ```bash
   ./bin/magento cache:clean
   ```

   >[!INFO]
   >
   >當您執行`status`命令時，新版本中包含的修補程式將不再顯示在可用修補程式表格中。

## 記錄

[!DNL Quality Patches Tool]會在`<Magento_root>/var/log/patch.log`檔案中記錄所有作業。
