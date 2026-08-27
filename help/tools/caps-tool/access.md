---
title: 如何存取 [!DNL Adobe Commerce Patching Automation]
description: 瞭解如何存取及使用 [!DNL Adobe Commerce Patching Automation]
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 1%

---

# 如何存取[!DNL Adobe Commerce Patching Automation]

## 先決條件

[!DNL Patching Automation]使用Adobe Commerce Cloud中的角色型存取控制。 您在Cloud Console中的存取層級會決定您可以使用該服務做什麼。

### 可以使用[!DNL Patching Automation]的人

* **專案管理員** — 可以在所有環境中套用或還原修補程式
* **參與者** — 可以在其指派的環境上套用或還原修補程式
* **檢視器** — 只能檢視專案和環境，不允許任何動作

### 如何要求專案的存取權

如果您在[!DNL Patching Automation]使用者介面中未看到任何專案，請向適當的人員要求存取權：

* 聯絡專案的帳戶擁有者或專案管理員
* 他們將會透過Cloud Console授予您適當的角色
* 在授與存取權後，您可以登入Cloud Console來使用該服務

>[!NOTE]
>
>[!DNL Patching Automation]遵循與Adobe Commerce Cloud相同的許可權模式，因此您在Cloud Console中的存取層級會決定您可以如何使用此服務。

## 正在存取[!DNL Patching Automation]

[!DNL Patching Automation]可在[!DNL Site-Wide Analysis Tool]儀表板中作為索引標籤使用。 您可以在管理員側邊欄中前往&#x200B;**報表** > **系統深入分析** > **全網站分析工具**，從管理員面板存取它。 請參閱[如何存取全網站分析工具](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/site-wide-analysis-tool/access)，瞭解必要條件和許可權設定。

進入控制面板後：

1. 按一下介面中的[!UICONTROL Patching Automation]標籤。
1. 選取您要套用修補程式的專案和環境。
1. 檢閱可用的修補程式及其相容性狀態。
1. 選取要套用的修補程式或還原。

## 生產環境存取權

對於生產環境，預設會套用其他保護措施：

* **維護模式** — 必須啟用
* **Cron工作** — 必須停用
* **確認對話方塊** — 必須先完成，才能繼續

>[!IMPORTANT]
>
>修補生產環境需要適當的準備和防護措施，以防止意外中斷。

>[!NOTE]
>
>在UI (*[!UICONTROL I want to skip maintenance mode and cron checks before applying patches to production environment]*)中選取覆寫核取方塊，即可略過維護模式和cron-job檢查。 只有在您瞭解修補生產環境而不具備這些防護措施時，才使用此選項。

## 相關主題

* [修補自動化簡介](intro.md)
* [工作流程概觀](workflow.md)
* [GitHub整合](github-integration.md)
* [最佳實務](best-practices.md)
* [疑難排解](troubleshooting.md)
