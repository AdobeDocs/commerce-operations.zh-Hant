---
title: ACSD-60811：修正將訂單狀態更新為自訂值的限制
description: 套用ACSD-60811修補程式以修正Adobe Commerce的問題，亦即唯有當目前狀態為「處理中」或「詐騙」時，才能使用自訂值或註解更新訂單狀態。
feature: Orders, Admin Workspace
role: Admin, Developer
source-git-commit: 099c4d25978aebe1eefbdcd4c3317b804da456b8
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---


# ACSD-60811：修正將訂單狀態更新為自訂值的限制

ACSD-60811修補程式修正了使用自訂值或註解來更新訂單狀態的問題，而此問題只有在目前狀態為&#39;[!UICONTROL Processing]&#39;或&#39;[!UICONTROL Suspected Fraud]&#39;時才能進行。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56時，即可使用此修補程式。 修補程式ID為ACSD-60811。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7。 2.4.7-p1， 2.4.7-p2， 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

只有在目前狀態為&#x200B;*正在處理*&#x200B;或&#x200B;*詐騙*&#x200B;時，才能使用自訂值或註解更新訂單狀態。 選擇並提交新狀態時，訂單狀態保持不變。

<u>要再現的步驟</u>：

1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Order Status]**」，在管理面板中建立自訂訂單狀態。
1. 按一下&#x200B;**[!UICONTROL Assign Status to State]**&#x200B;將自訂狀態指派給訂購狀態。
1. 從管理面板的訂單檢視頁面變更訂單狀態。

<u>預期結果</u>：

管理員使用者應該能夠在管理員面板中將訂單狀態變更為自訂訂單狀態。

<u>實際結果</u>：

選取並提交新訂單狀態時，訂單狀態會維持不變。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
