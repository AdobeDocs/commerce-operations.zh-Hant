---
title: '[!DNL Commerce Version Tool]疑難排解'
description: 瞭解如何疑難排解 [!DNL Commerce Version Tool] Composer偵測、內部試執行檢查、登入快取、JSON輸出和稽核記錄問題。
TQID: 'https://experienceleague.adobe.com/JwRSy7pfM89WoifYUzTVPhR-WrDIvj2A2B8SaEnmyWM'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 1222
ht-degree: 0%

---

# [!DNL Commerce Version Tool]疑難排解

使用此頁面來疑難排解Composer偵測、登入載入、內部執行修補程式偵測、輸出產生和稽核記錄等常見[!DNL Commerce Version Tool] ([!DNL CVT])問題。

## 快速疑難排解步驟

如果[!DNL CVT]工具未傳回預期的修補程式狀態報告：

- 確認目標安裝使用支援的Adobe Commerce版本和版本。
- 確認`composer.lock`存在，並符合您要檢查的環境。
- 確認PHP和系統`patch`二進位檔是否可用。
- 確認[!DNL CVT]可以讀取修補程式登入檔。
- 檢閱輸出中的`warnings`、`missing_patches`和`unknown_patches`。
- 如果記錄檔已建立，請檢查`var/log/patch_status.log`以取得執行的稽核摘要。

>[!TIP]
>
> 如果您需要瞭解修補程式為何無法分類，記錄檔將最有幫助。 對於每個未知的修補程式，記錄檔會記錄正向和反向練習的原始輸出，包括任何錯誤或棧積失敗。
>
> 如果您無法擷取登入或修補程式檔案，請檢查報告中的警告欄位。 這些詳細資料不會顯示在記錄中。

## 常見問題與解決方案

### 無法偵測基本版本

如果[!DNL CVT]工具找不到Adobe Commerce基本版本，請檢查下列條件：

**檢查：**

- `composer.lock`遺失。
- `patch-status`命令在Adobe Commerce專案根目錄之外執行（或`--root`指向錯誤的路徑），因此找不到`composer.lock`。
- `composer.lock`存在但不是有效的JSON，或無法讀取。
- `composer.lock`不包含任何可辨識的基本套件(`magento/product-enterprise-edition`、`magento/product-community-edition`、`magento/magento2-base`)。

**警告訊息：**

如果`composer.lock`存在但無法讀取、無法剖析，或不包含可辨識的基本封裝，則工具會在警告輸出欄位中發出下列其中一個字串：

```shell-session
No recognized Commerce base package found in composer.lock
composer.lock exists but could not be read
composer.lock could not be parsed as JSON
```

>[!NOTE]
>
> 如果完全遺失`composer.lock`，工具會報告`base_version: "unknown"`，但完全沒有&#x200B;**警告訊息**。 一律直接檢查輸出中的`base_version`。 不要依賴警告的存在來尋找此問題。

上述任何條件都表示工具無法偵測基礎版本。 工具結束，程式碼為`1`，且未執行修補程式偵測。

**動作：**

- 從[!DNL Adobe Commerce]專案根目錄執行`patch-status`命令，或傳遞正確的`--root`。
- 確認`composer.lock`存在、目前且有效的JSON。
- 確認安裝使用支援的Adobe Commerce版本，因此`composer.lock`包含其中一個可辨識的基本套件。

### 安裝的版本沒有套用任何修補程式

如果[!DNL CVT]報告有效的`base_version`，但`applied_patches`、`missing_patches`和`unknown_patches`是空的，則目前的修補程式登入不會涵蓋已安裝的版本。

**檢查：**

- 安裝的[!DNL Adobe Commerce]版本未顯示在修補程式登入檔案中。 例如，比登入的最新專案更新的版本。

**警告訊息：**

```shell-session
No patches found in registry for installed component versions (CE=2.4.7-p9)
```

此警告與「無法偵測基礎版本」不同。 `base_version`正確，工具結束`0`，登入中沒有可比較的專案。

**動作：**

- 確認輸出中的`base_version`符合您的預期。
- 確認`registry_source`是`remote`或最近的`cache`，而不是舊的。
- 如果應該涵蓋此版本，請聯絡Adobe Commerce支援。

### 無法擷取修補程式登入

如果[!DNL CVT]工具無法擷取最新的修補程式登入檔，請檢查網路和快取設定：

**檢查：**

- 網路無法使用。
- Adobe修補程式端點請求逾時。
- 已使用`--no-cache`，無法連線到遠端登入。
- `PATCH_REGISTRY_URL`指向無法使用的登入或不是有效的HTTPS URL。
- 如果[!DNL CVT]工具無法擷取最新的修補程式登入檔，請檢查網路和快取設定：

>[!NOTE]
>
>如果登入檔遺失或過期，工具會從遠端主機下載最新的登入檔。

**警告訊息：**

此工具會在此案例的警告輸出欄位中發出下列字串：

```shell-session
Remote registry fetch failed (HTTP 403). Check PATCH_REGISTRY_URL (if set) and network connectivity.
Remote registry response was not valid JSON; ignoring.
Could not load remote registry. Using cached registry (3 hours old). CVE coverage may be incomplete.
Patch registry could not be loaded.
Could not fetch remote registry and --no-cache was set; aborting.
```

過時的快取訊息包含以小時為單位的實際存留時間，例如`(3 hours old)`。

`patch registry could not be loaded`和`could not fetch remote registry`警告表示工具已結束，但未執行修補程式偵測。

**動作：**

- 網路連線可用時重新執行`patch-status`命令。
- 如果掃描可接受過時快取警告，則允許[!DNL CVT]工具使用快取登入。
- 移除`--no-cache`，除非您需要新的遠端擷取。
- 若要重複使用登入快取，請確認[!DNL CVT]工具可以寫入`var/patch_metadata/`。

### 無法擷取或驗證修補程式差異

如果[!DNL CVT]工具無法測試一或多個適用的修補程式，請檢查patch-diff存取：

**檢查：**

- 無法從Adobe修補程式端點下載修補程式diff。
- 已驗證修補程式下載所需的認證遺失或無效。
- `PATCH_DIFF_BASE_URL`指向無法使用的patch-diff來源或不是有效的HTTPS URL。
- 快取的修補程式差異遺失或無法讀取。
- 下載的修補程式差異導致SHA-256驗證失敗。
- [!DNL CVT]工具無法寫入`var/patch_metadata/.patch_diffs/`。

**警告訊息：**

此工具會在此案例的警告輸出欄位中發出下列字串：

```shell-session
Patch 247p9-2026-05-001-EE requires authentication. Set credentials via COMPOSER_AUTH or auth.json.
Could not fetch patch 247p9-2026-05-001-EE (HTTP 401). Check credentials (COMPOSER_AUTH / auth.json).
Could not fetch patch 247p9-2026-05-001-EE (HTTP 404).
Could not fetch or verify patch 247p9-2026-05-001-EE. Check network connectivity and credentials (COMPOSER_AUTH / auth.json).
Could not fetch patch file for 247p9-2026-05-001-EE.
SHA-256 verification failed for patch 247p9-2026-05-001-EE; discarding download.
```

每個訊息中的修補程式識別碼都是實際的登入專案識別碼，例如`247p9-2026-05-001-EE`。 `SHA-256 verification failed`表示新下載的修補程式檔案與其預期的總和檢查碼不符。 工具會在不快取的情況下捨棄該修補程式，並將修補程式`unknown`分類以用於此執行。 偵測到損毀的&#x200B;*本機*&#x200B;快取專案，並在相同的執行中無警告地自動重新擷取。 在這兩種情況下，都不需要手動清除快取。

**動作：**

- 請確認網路連線並重試該命令。
- 確認已設定驗證修補程式下載所需的認證。
- 確認[!DNL CVT]工具可以寫入`var/patch_metadata/.patch_diffs/`。
- 如果修補程式仍分類為未知，則保留警告和輸出詳細資訊。

### 報告遺失或未知的修補程式

如果報告包含非預期的`missing_patches`或`unknown_patches`值，請檢閱安裝和輸出詳細資料：

**檢查：**

- 每月套用的修補程式不按順序套用。
- 元件專用修補程式(例如Adobe Commerce Business-to-business (B2B)或Adobe Commerce Page Builder)遺失。
- `composer.lock`報告需要修補程式的已安裝元件版本。
- 修補程式差異無法使用或偵測結果無結論。

**警告訊息：**

此工具會在此案例的警告輸出欄位中發出下列字串：

```shell-session
No file_name or sha256 for 247p9-2026-05-001-EE
Registry entry '247p9-2026-05-001-EE' requires unknown patch '247p9-2026-04-001-EE'; skipping.
descendant diffs unavailable for 247p9-2026-06-001-EE; dry-run for 247p9-2026-05-001-EE may be inaccurate
Failed to reverse-apply 247p9-2026-06-001-EE when preparing dry-run for 247p9-2026-05-001-EE; result may be inaccurate
Failed to forward-apply prerequisite 247p9-2026-04-001-EE when preparing dry-run for 247p9-2026-05-001-EE; result may be inaccurate
```

當您在警告中遇到`may be inaccurate`時，模擬執行檢查仍會執行，但信賴度會降低。 修補程式仍可在`applied_patches`或`missing_patches`中分類，不一定是`unknown_patches`。

特別針對未知的修補程式，`var/log/patch_status.log`會記錄原始修補程式試執行輸出（正向和反向），以指出哪些檔案和區塊不相符。

如果您遇到「找不到修補程式」警告，請參考[沒有修補程式套用至已安裝的版本](#no-patches-apply-to-the-installed-version)以取得指引。

**動作：**

- 檢閱`applied_patches`、`missing_patches`和`unknown_patches`欄位。
- 確認遺失的修補程式是否適用於已安裝的版本和元件。
- 將結果與相關安全性修補程式發行說明進行比較。
- 確認檢查過的程式碼基底符合您要報告的部署環境。
- 如果未知狀態封鎖補救計畫，請聯絡Adobe Commerce支援。

### 未產生輸出

如果[!DNL CVT]工具完成，但缺少預期的JSON或CSV輸出，請檢查命令語法和終端機輸出：

**動作：**

- 如果不需要輸出CSV，則使用預設JSON輸出。
- 使用`--format=csv`產生CSV輸出。
- 確認執行[!DNL CVT]工具的Shell、指令碼或掃描器並未重新導向或捨棄命令輸出。
- 檢查`stderr`以取得`patch-status:`則錯誤訊息。
- 如果將輸出重新導向至檔案，例如`patch-status > report.json`，請確認殼層具有該目的地的寫入許可權。 工具只會寫入`stdout`。
- 確認[!DNL CVT]工具可以寫入`var/log/patch_status.log`。
- 重新執行命令並擷取終端機輸出以進行疑難排解。

## 取得協助

聯絡Adobe Commerce支援時，僅提供調查問題所需的詳細資訊。

包括：

- Adobe Commerce版本和版本
- [!DNL CVT]工具版本
- [!DNL CVT]工具輸出的登入來源
- 相關的`applied_patches`、`missing_patches`和`unknown_patches`值
- 相關警告
- 錯誤訊息或命令輸出

請勿在共用的記錄或附件中包含秘密、認證、私密金鑰或不相關的客戶資料。

## 相關主題

- [簡介](intro.md)
- [產生修補程式狀態報告](generate-report.md)
- [發行說明](release-notes.md)
