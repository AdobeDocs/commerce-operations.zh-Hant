---
title: 產生修補程式狀態報告
description: 瞭解如何使用 [!DNL Commerce Version Tool] 產生JSON或CSV格式的Adobe Commerce修補程式狀態報表。
TQID: 'https://experienceleague.adobe.com/-lC-20YMpbTM3tTZjbBO5zD5gb9n7cRah5Ycy8wQoyw'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: cb0391ae368b53a795535f3adb636628a339b963
workflow-type: tm+mt
source-wordcount: 590
ht-degree: 2%

---

# 產生修補程式狀態報告

使用[!DNL Commerce Version Tool] ([!DNL CVT])產生Adobe Commerce安裝的修補程式狀態報告。 此報表會識別已套用、遺失和未知的每月安全性修補程式，並依預設傳回JSON輸出。

## 先決條件

執行[!DNL CVT]之前，請確認：

- 目標安裝使用支援的Adobe Commerce版本和版本。
- `composer.lock`存在，並符合您要檢查的環境。
- PHP和系統`patch`二進位檔可以使用。
- 您可以從執行命令的環境中讀取專案檔案。
- 如果您想要快取檔案和稽核記錄專案，工具可以寫入`var/patch_metadata/`和`var/log/`。
- 如果軟體權利檔案修補程式套用至安裝，則可透過`COMPOSER_AUTH`或`auth.json`取得認證。

[!DNL CVT]工具會檢查`COMPOSER_AUTH`、Adobe Commerce專案`auth.json`以及全域撰寫器`auth.json`，以取得軟體權利控制的修補認證。

## 產生報表

從Adobe Commerce專案根目錄中，執行：

```bash
php vendor/bin/patch-status
```

若要檢查其他Adobe Commerce安裝，請使用`--root`選項：

```bash
php vendor/bin/patch-status --root=/path/to/commerce
```

## 命令選項

JSON是預設的輸出格式。 掃描器、儀表板和法規遵循報表支援CSV輸出。

| 選項 | 說明 |
| --- | --- |
| `--root=PATH` | 指定Adobe Commerce安裝根目錄的路徑。 預設值為目前目錄。 |
| `--format=json\|csv` | 設定輸出格式。 預設值為`json`。 |
| `--no-cache` | 略過登入和修補差異快取，強制新的遠端擷取，如果遠端登入無法使用，則會退出並出現錯誤。 |
| `--version`, `-V` | 列印工具版本。 |
| `--help`, `-h` | 列印說明訊息。 |

{style="table-layout:auto"}

## 檢閱JSON和CSV輸出

下列範例顯示預設的JSON輸出。

```bash
php vendor/bin/patch-status
```

```json
{
  "base_version": "2.4.7-p9",
  "installed_components": {
    "CE": "2.4.7-p9",
    "EE": "2.4.7-p9",
    "B2B": "1.5.2-p5"
  },
  "applied_patches": [
    "247p9-2026-05-001-CE",
    "247p9-2026-05-001-EE"
  ],
  "missing_patches": [
    "247p9-2026-06-001-CE",
    "247p9-2026-06-001-EE"
  ],
  "unknown_patches": [],
  "vulnerability_status": {
    "CVE-2026-12354": { "status": "PROTECTED" },
    "CVE-2026-67890": { "status": "VULNERABLE" }
  },
  "registry_source": "remote",
  "warnings": []
}
```

若要產生CSV輸出，請使用`--format=csv`選項：

```bash
php vendor/bin/patch-status --format=csv
```

CSV輸出在每個CVE中產生一列，適用於試算表、掃描器、儀表板和法規遵循工具。

## 瞭解報告結果

請先檢閱遺失和未知的修補程式，再提出安全性狀態宣告。

### 修補程式狀態值

修正程式狀態報表會依下列值將修正程式結果分組：

| 修補程式狀態 | 含義 |
| --- | --- |
| 已套用 | [!DNL CVT]工具會在Adobe Commerce程式碼基底中偵測每月安全性修補程式。 |
| 遺失 | 修補程式會套用至已安裝的Adobe Commerce版本或元件，但[!DNL CVT]工具並未偵測到它。 |
| 未知 | 工具無法從可用的登入、修補程式差異或偵測結果確認修補程式狀態。 |

{style="table-layout:auto"}

### CVE狀態值

JSON輸出以大寫報告CVE狀態值。

| CVE狀態 | 含義 |
| --- | --- |
| `PROTECTED` | 偵測到CVE或元件的適用修補程式。 |
| `VULNERABLE` | CVE或元件缺少適用的修補程式。 |
| `UNKNOWN` | [!DNL CVT]工具無法從可用的登入和偵測資料判斷CVE狀態。 |
| `NOT_APPLICABLE` | CVE會套用至未安裝的元件，例如Adobe Commerce Business-to-business (B2B)、Adobe Commerce Page Builder或Adobe Commerce Inventory。 |

{style="table-layout:auto"}

### 關鍵輸出欄位

報表可包含下列資訊：

- **基礎Adobe Commerce版本** — 從`composer.lock`偵測到已安裝的基礎版本。
- **登入來源** — 修補程式中繼資料是否來自`remote`、`cache`或`stale_cache`。
- **已安裝的元件** — 從`composer.lock`偵測到Adobe Commerce封裝區域。
- **已套用修補程式** - Adobe Commerce程式碼基底中偵測到每月的安全性修補程式。
- **遺失修補程式** — 每月會套用但無法偵測的安全性修補程式。
- **未知的修補程式** - [!DNL CVT]工具無法分類的修補程式。
- **CVE的弱點狀態** - CVE涵蓋範圍對應到受保護、易受攻擊、不適用或未知狀態。
- **警告** — 可能影響報告可靠性或完整性的條件。

## 修正登入和快取

修補程式登入檔案包含[!DNL CVT]工具用來判斷哪些修補程式套用至已安裝版本的修補程式中繼資料。 此工具會在可用時使用新的登入快取，必要時會擷取遠端登入，而且如果網路無法使用，則可以使用有警告的過時快取。 只有在您需要新的遠端擷取時才使用`--no-cache`。

## 相關主題

- [簡介](intro.md)
- [疑難排解](troubleshooting.md)
- [發行說明](release-notes.md)
