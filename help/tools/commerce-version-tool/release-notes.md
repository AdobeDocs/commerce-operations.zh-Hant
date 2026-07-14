---
title: '[!DNL Commerce Version Tool]發行說明'
description: 瞭解 [!DNL Commerce Version Tool] 版本，包括新的修補程式狀態報告、CVE保護狀態、CSV輸出和快取行為。
feature: Release Notes
TQID: 'https://experienceleague.adobe.com/38I3U5y9rmurP5gVhalfUq7DlcUb-JpF5eUam1nwEyk'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: f42e0a1a-0d79-488d-a83f-f2c30672b137
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 180
ht-degree: 2%

---

# [!DNL Commerce Version Tool]發行說明

這些發行說明說明[!DNL Commerce Version Tool] ([!DNL CVT])的更新。

## 1.0.0版 — 2026年6月 {#version-1-0-0}

### 新功能

- **修補程式狀態報告** — 報告Adobe Commerce安全性修補程式每月套用、遺失或無法分類以安裝Adobe Commerce的修補程式。
- **CVE保護狀態** — 將修補程式結果對應到每個CVE保護狀態值： `PROTECTED`、`VULNERABLE`、`UNKNOWN`和`NOT_APPLICABLE`。
- **多元件支援** — 偵測來自`composer.lock`的已安裝Adobe Commerce元件，包括Adobe Commerce企業對企業(B2B)、Adobe Commerce Page Builder、Adobe Commerce Inventory以及修補程式登入檔案中代表的其他元件。
- **JSON和CSV輸出** — 依預設為試算表、掃描器、儀表板和法規遵循工具提供JSON輸出，以供程式化使用和CSV輸出。
- **適合離線使用的快取行為** — 每次擷取成功後，都會在本機快取修補程式登入檔案。 如果遠端登入無法使用，[!DNL CVT]工具可以使用快取登入並出現警告。
- **隨附傳遞** — 隨附於每月的Adobe Commerce安全性修補程式檔案。 套用修補程式會在`vendor/bin/patch-status`安裝[!DNL CVT]，不需要個別的安裝步驟。

## 相關主題

- [簡介](intro.md)
- [產生修補程式狀態報告](generate-report.md)
- [疑難排解](troubleshooting.md)
