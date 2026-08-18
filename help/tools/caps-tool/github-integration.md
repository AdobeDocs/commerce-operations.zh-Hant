---
title: 為 [!DNL CAPS]設定GitHub整合
description: 瞭解如何安裝 [!DNL Cloud Automation Patching Service (CAPS)] GitHub應用程式，以啟用GitHub連線Adobe Commerce Cloud專案的修補程式操作。
hide: true
source-git-commit: 2887956e8644ffbcaadde36b90a0fc984369008a
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 1%

---


# 為[!DNL CAPS]設定GitHub整合

如果您的Adobe Commerce Cloud專案已連線至GitHub存放庫，您必須先安裝[!DNL CAPS] GitHub應用程式，才能使用[!DNL Cloud Automation Patching Service] ([!DNL CAPS])套用或還原修補程式。 應用程式會授予[!DNL CAPS]必要的存取權，以代表您對存放庫進行變更。

## 先決條件

* 有效的Adobe Commerce Cloud訂閱
* 已針對您的Adobe Commerce Cloud專案設定[GitHub整合](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github)，並已啟用[`fetch-branches`選項](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration)。 [!DNL CAPS]會建立並推播暫時的整合環境分支，所以當此選項停用時，修補程式操作無法建立環境。
* 託管於[!DNL github.com]的存放庫。 不支援使用自訂網域設定的GitHub整合。
* GitHub組織或存放庫的所有者或管理員存取權

## 安裝[!DNL CAPS] GitHub應用程式

1. 開啟[CAPS GitHub應用程式安裝頁面](https://github.com/apps/adobe-commerce-patching-automation)。
1. 按一下&#x200B;**[!UICONTROL Install]**。
1. 選取擁有您Adobe Commerce存放庫的GitHub組織。
1. 在「**[!UICONTROL Repository access]**」下，選取「**[!UICONTROL Only select repositories]**」，然後為您的Adobe Commerce專案選擇存放庫。
1. 按一下&#x200B;**[!UICONTROL Install]**&#x200B;確認。

安裝後，[!DNL CAPS]會自動偵測您的GitHub連線，並將應用程式用於所有修補程式操作。 不需要進一步設定。

## 解除安裝[!DNL CAPS] GitHub應用程式

如果您不再希望[!DNL CAPS]存取您的存放庫：

1. 在GitHub中，開啟擁有安裝之帳戶的設定：
   * 針對&#x200B;**組織擁有的**&#x200B;存放庫： **[!UICONTROL Organization settings]** > **[!UICONTROL Third-party Access]** > **[!UICONTROL GitHub Apps]**。
   * 針對&#x200B;**個人**&#x200B;存放庫： **[!UICONTROL Settings]** > **[!UICONTROL Applications]** > **[!UICONTROL Installed GitHub Apps]**。
1. 尋找`adobe-commerce-patching-automation`並按一下&#x200B;**[!UICONTROL Configure]**。
1. 按一下&#x200B;**[!UICONTROL Uninstall]**&#x200B;並確認。

>[!WARNING]
>
>如果解除安裝GitHub應用程式時仍有任何套用大寫字元或還原作業正在進行中，這些作業可能會失敗。 解除安裝應用程式後，使用者也無法開始新的操作，因為動作按鈕會變成非使用中。

## 相關主題

* [大寫字介紹](intro.md)
* [如何存取](access.md)
* [工作流程概觀](workflow.md)
* [最佳實務](best-practices.md)
* [疑難排解](troubleshooting.md)
