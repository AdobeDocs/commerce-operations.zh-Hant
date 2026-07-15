---
title: '[!DNL Commerce Version Tool]'
description: 瞭解Adobe Commerce的 [!DNL Commerce Version Tool] ，並使用廠商/bin/patch-status來檢查每月的安全性修補程式狀態。
TQID: 'https://experienceleague.adobe.com/9lDQtCrcCSIFjt3jUJkqCo-rMlIhhy3tPTtPyT4wt1Q'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: f42e0a1a-0d79-488d-a83f-f2c30672b137
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 586
ht-degree: 0%

---

# [!DNL Commerce Version Tool]

Adobe Commerce的每月安全性修補程式為非累積式，必須依序套用。 [!DNL Commerce Version Tool] ([!DNL CVT])可協助商戶確認修補程式涵蓋範圍，方法是回報每個月安裝了哪些安全性修補程式、缺少哪些修補程式，以及安裝受到哪些CVE保護。

>[!IMPORTANT]
>
>[!DNL CVT]工具僅供參考。 它不會套用修補程式、還原修補程式或修改Adobe Commerce來源檔案。 它可以寫入快取檔案、暫存執行檔案和稽核記錄專案，以支援修補程式狀態報告。

## 工具概覽

[!DNL CVT]工具是每個每月Adobe Commerce安全性修補程式隨附的獨立可執行檔。 將修補程式套用至Adobe Commerce安裝時，工具安裝在`vendor/bin/patch-status`。 它需要PHP 8.1或更新版本，以及系統`patch`二進位。 它不需要Composer套件、非標準的PHP擴充功能、Adobe Commerce Bootstrap或單獨的安裝步驟。

[!DNL CVT]工具可協助您：

- 針對支援的Adobe Commerce安裝，偵測已套用的安全性修補程式。
- 識別每月隔離安全性修補程式序列中遺失的修補程式。
- 針對修補程式相關的常見弱點與暴露(CVE)記錄，報告受保護、易受攻擊或未知的安全性狀態。
- 產生機器可讀的輸出，例如JSON或CSV，以用於掃描器、儀表板和合規性報告。
- 偵測支援平台和元件的修補程式狀態。

## 可用性

當Adobe為修補程式登入檔案中所安裝的版本提供修補程式中繼資料時，[!DNL CVT]工具支援下列平台與元件的修補程式狀態報告。

| 平台或元件 | 可用性 |
| --- | --- |
| Adobe Commerce內部部署 | 支援 |
| [!DNL Magento Open Source] | 支援 |
| Adobe Commerce企業對企業(B2B) | 安裝時支援 |
| Adobe Commerce頁面產生器 | 安裝時支援 |
| Adobe Commerce詳細目錄 | 安裝時支援 |
| 從`composer.lock`偵測到其他元件 | 在修補程式登入檔案中表示時支援 |

{style="table-layout:auto"}

## 常見使用案例

當您需要以下動作時，請使用[!DNL CVT]工具：

- 檢查Adobe Commerce安裝是否包含必要的隔離安全性修補程式。
- 確認略過或不完整的修補程式集是否導致CVE涵蓋範圍不完整。
- 產生JSON或CSV輸出以供內部報告或自動掃描。
- 在開啟支援要求或計畫修正之前，提供修補程式狀態資訊。

## 使用結果的准則

將[!DNL CVT]工具輸出視為支援修補程式規劃和安全性檢閱的偵測資料。

請遵循下列准則：

- 針對穩定且受支援的Adobe Commerce安裝執行[!DNL CVT]工具。
- 請先檢閱遺失和未知的修補程式，再提出安全性狀態宣告。
- 保留JSON或CSV輸出，以提高可稽核性和自動化程度。
- 將掃描輸出視為與安全性相關的作業資料。
- 僅分享支援或修正所需的詳細資訊。

## 修補程式偵測

[!DNL CVT]工具會以兩個固定步驟執行偵測。 產生修補程式狀態報表時，這兩個步驟一律會執行。

- **Composer偵測：**&#x200B;工具會讀取`composer.lock`檔案，以判斷[!DNL Adobe Commerce]基本版本和已安裝的元件區域。 如果工具無法偵測基礎版本，則會退出並返回程式碼`1`。

- **試執行偵測：**&#x200B;針對每個適用的修補程式，工具會針對修補程式變更使用試執行檢查，以判斷是否已套用修補程式、未套用修補程式，或修補程式狀態是否未知。 此工具會在此檢查期間處理修補相依性，以便結果反映安裝的元件版本。

此報告僅包含套用至偵測到的安裝和已安裝元件的修補程式。 如果工具無法確認是否有適用的修補程式，則會將修補程式分類為未知。

## 開始使用[!DNL CVT]

請使用下列主題來產生、疑難排解及追蹤修補程式狀態報告：

- [產生修補程式狀態報告](generate-report.md)以執行[!DNL CVT]工具、檢閱命令選項並解譯報告結果。
- [[!DNL Commerce Version Tool] 疑難排解](troubleshooting.md)以解決非預期的結果或命令錯誤。
- [[!DNL Commerce Version Tool] 發行說明](release-notes.md)以檢閱發行更新。
