---
title: ACSD-66118：更新[!UICONTROL Store View Code]會在未重新整理[!UICONTROL Design Configuration]時清除[!UICONTROL Configuration Cache]設定
description: 套用ACSD-66118修補程式以修正Adobe Commerce問題，其中如果[!UICONTROL Store View Code]未正確重新整理，更新[!UICONTROL Design Configuration]會清除[!UICONTROL Configuration Cache] （主題和自訂設定）。
feature: Cache, Configuration, Themes
role: Admin, Developer
type: Troubleshooting
exl-id: ecfdff54-99e0-4dbe-a0bb-80f60aafc7b6
source-git-commit: 468c780f355c99cf06d557e530e81c414a01961e
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# ACSD-66118：更新&#x200B;**[!UICONTROL Store View Code]**&#x200B;會在未重新整理&#x200B;**[!UICONTROL Design Configuration]**&#x200B;時清除&#x200B;**[!UICONTROL Configuration Cache]**&#x200B;設定

ACSD-66118修補程式修正了&#x200B;**[!UICONTROL Store View Code]**&#x200B;未重新整理時更新&#x200B;**[!UICONTROL Design Configuration]**&#x200B;會清除&#x200B;**[!UICONTROL Configuration Cache]**&#x200B;設定的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67時，即可使用此修補程式。 修補程式ID為ACSD-66118。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果&#x200B;**[!UICONTROL Design Configuration]**&#x200B;未重新整理，則在更新&#x200B;**[!UICONTROL Store View Code]**&#x200B;欄位時會清除&#x200B;**[!UICONTROL Configuration Cache]**&#x200B;設定（例如主題和自訂設定）。

<u>要再現的步驟</u>：

1. 登入&#x200B;**[!UICONTROL Admin]**&#x200B;面板。
2. 導覽至&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL All Stores]**。
3. 編輯在&#x200B;**[!UICONTROL Content]** > *[!UICONTROL Design]* > **[!UICONTROL Configuration]**&#x200B;中設定自訂佈景主題的商店檢視。
4. 變更&#x200B;**[!UICONTROL Code]**&#x200B;欄位（例如，從`storeview_1`變更為`storeview_main`）。
5. 按一下&#x200B;**[!UICONTROL Save Store View]**&#x200B;以儲存變更。
6. 重新整理或重新開啟已更新&#x200B;**[!UICONTROL Content]**&#x200B;的&#x200B;*[!UICONTROL Design]* > **[!UICONTROL Configuration]** > **[!UICONTROL Store View]**&#x200B;頁面，將不選取任何主題。

<u>預期結果</u>：

更新&#x200B;**[!UICONTROL Store View Code]**&#x200B;後，**[!UICONTROL Design Configuration]** （包括主題和自訂設定）應保持不變。

<u>實際結果</u>：

**[!UICONTROL Design Configuration]**&#x200B;已清除。 主題會回覆為預設值，自訂設定也會遺失。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
