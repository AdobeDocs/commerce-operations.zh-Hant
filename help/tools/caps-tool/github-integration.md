---
title: 為 [!DNL Adobe Commerce Patching Automation]設定GitHub整合
description: 瞭解如何安裝 [!DNL Adobe Commerce Patching Automation] GitHub應用程式，以啟用GitHub連線Adobe Commerce Cloud專案的修補程式操作。
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---


# 為[!DNL Patching Automation]設定GitHub整合

如果您的Adobe Commerce Cloud專案已連線至GitHub存放庫，您必須先安裝[!DNL Patching Automation] GitHub應用程式，才能使用服務套用或還原修補程式。 應用程式會授予服務代表您變更存放庫所需的存取權。

## 先決條件

* 有效的Adobe Commerce Cloud訂閱
* 已針對您的Adobe Commerce Cloud專案設定[GitHub整合](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github)，並已啟用[`fetch-branches`選項](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration)。 [!DNL Patching Automation]會建立並推播暫時的整合環境分支，所以當此選項停用時，修補程式操作無法建立環境。
* 託管於[!DNL github.com]的存放庫。 不支援使用自訂網域設定的GitHub整合。
* GitHub組織或存放庫的所有者或管理員存取權

## 安裝[!DNL Patching Automation] GitHub應用程式

您可以按一下UI中的&#x200B;**[!UICONTROL Install GitHub App]** （會將您重新導向至安裝頁面），或直接導覽至安裝頁面，從[!DNL Patching Automation]開始安裝。

1. 開啟[修補自動化GitHub應用程式安裝頁面](https://github.com/apps/adobe-commerce-patching-automation)。
1. 按一下&#x200B;**[!UICONTROL Install]**。
1. 選取擁有您Adobe Commerce存放庫的GitHub組織。
1. 在「**[!UICONTROL Repository access]**」下，選取「**[!UICONTROL Only select repositories]**」，然後為您的Adobe Commerce專案選擇存放庫。
1. 按一下&#x200B;**[!UICONTROL Install]**&#x200B;確認。

安裝後，此服務會自動偵測您的GitHub連線，並將應用程式用於所有修補程式操作。 不需要進一步設定。

## 檢查並管理連線狀態

[!DNL Patching Automation] UI會顯示GitHub連線的目前狀態，並根據該狀態提供動作：

* **[!UICONTROL Refresh]** / **[!UICONTROL Refresh status]** — 重新檢查連線狀態而不做任何變更。
* **[!UICONTROL Reinstall]** — 在安裝不再有效時顯示（例如，安裝已暫停，或連線至您雲端專案的存放庫已變更）。 啟動上述相同的安裝流程。
* **[!UICONTROL Unlink GitHub App]** — 移除[!DNL Patching Automation]與GitHub應用程式的已儲存連線。 這&#x200B;**不會**&#x200B;從您的GitHub存放庫解除安裝應用程式 — 若要完全移除存取權，請參閱下方的「解除安裝」一節。

## 解除安裝[!DNL Patching Automation] GitHub應用程式

如果您不想再讓服務存取您的存放庫：

1. 在GitHub中，開啟擁有安裝之帳戶的設定：
   * 針對&#x200B;**組織擁有的**&#x200B;存放庫： **[!UICONTROL Organization settings]** > **[!UICONTROL Third-party Access]** > **[!UICONTROL GitHub Apps]**。
   * 針對&#x200B;**個人**&#x200B;存放庫： **[!UICONTROL Settings]** > **[!UICONTROL Applications]** > **[!UICONTROL Installed GitHub Apps]**。
1. 尋找`adobe-commerce-patching-automation`並按一下&#x200B;**[!UICONTROL Configure]**。
1. 按一下&#x200B;**[!UICONTROL Uninstall]**&#x200B;並確認。

>[!WARNING]
>
>解除安裝GitHub應用程式後，如果有任何套用或還原作業仍在進行中，這些作業可能會失敗。 解除安裝應用程式後，使用者也無法開始新的操作，因為動作按鈕會變成非使用中。

## 相關主題

* [修補自動化簡介](intro.md)
* [如何存取](access.md)
* [工作流程概觀](workflow.md)
* [最佳實務](best-practices.md)
* [疑難排解](troubleshooting.md)
