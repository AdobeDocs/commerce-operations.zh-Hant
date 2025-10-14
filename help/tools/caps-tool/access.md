---
title: 如何存取 [!DNL Cloud Automation Patching Service (CAPS)]
description: 瞭解如何存取及使用 [!DNL Cloud Automation Patching Service (CAPS)]
hide: true
hidefromtoc: true
source-git-commit: ca388bd78affd4def19a5539d8529f2563d35e8c
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 1%

---

# 如何存取[!DNL Cloud Automation Patching Service (CAPS)]

## 先決條件

[!DNL CAPS]使用Adobe Commerce Cloud中的角色型存取控制。 您在Cloud Console中的存取層級決定您可以對[!DNL CAPS]執行的操作。

### 可以使用[!DNL CAPS]的人

* **專案管理員** — 可以在所有環境中套用或還原修補程式
* **參與者** — 可以在其指派的環境上套用或還原修補程式
* **檢視器** — 只能檢視專案和環境，不允許任何動作

### 如何要求專案的存取權

如果您在[!DNL CAPS]使用者介面中未看到任何專案，則需要向適當的人員請求存取權：

* 聯絡專案的帳戶擁有者或專案管理員
* 他們將會透過Cloud Console授予您適當的角色
* 在授與存取權後，您可以登入Cloud Console以使用[!DNL CAPS]

>[!NOTE]
>
>[!DNL CAPS]遵循與Adobe Commerce Cloud相同的許可權模型，因此您在Cloud Console中的存取層級會決定您可以對[!DNL CAPS]執行的操作。

## 正在存取[!DNL CAPS]

CAPS工具可從全網站分析工具儀表板取得，網址為[https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/)。 在「自動修補」標籤下，您可以選取專案和環境。

1. 瀏覽至[https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/)的全網站分析工具。
1. 按一下介面中的[!UICONTROL Patching Automation]標籤。
1. 選取您要套用修補程式的專案和環境。
1. 檢閱可用的修補程式及其相容性狀態。
1. 選取要套用的修補程式或還原。

## 生產環境存取權

對於生產環境，可套用其他保護措施：

* **維護模式** — 必須啟用
* **Cron工作** — 必須停用
* **確認對話方塊** — 必須先完成，才能繼續

>[!IMPORTANT]
>
>修補生產環境需要適當的準備和防護措施，以防止意外中斷。

## 相關主題

* [大寫字介紹](intro.md)
* [工作流程](workflow.md)
* [最佳實務](best-practices.md)
* [疑難排解](troubleshooting.md)
