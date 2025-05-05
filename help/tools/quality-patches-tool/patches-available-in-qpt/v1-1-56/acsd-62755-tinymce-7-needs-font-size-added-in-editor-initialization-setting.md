---
title: ACSD-62755： [!DNL TinyMCE] 7需要在編輯器初始化設定中新增字型大小和字型
description: 套用ACSD-62755修補程式以修正Adobe Commerce問題，其中 [!DNL TinyMCE] 7需要在編輯器初始化設定中特別新增*font size*和*font family*。
feature: Page Content, Page Builder, Admin Workspace
role: Admin, Developer
source-git-commit: 4aba81ea12cc08370881d3cc108e94ba410a2198
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# ACSD-62755： [!DNL TinyMCE] 7需要新增字型大小與字型到編輯器初始化設定

ACSD-62755修補程式修正[!DNL TinyMCE] 7需要在編輯器初始化設定中特別新增&#x200B;*字型大小*&#x200B;和&#x200B;*字型系列*&#x200B;選取器的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56時即可使用此修補程式。 修補程式ID為ACSD-62755。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.5-p10

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.4-p11、2.4.5-p10、2.4.6-p8、2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

[!DNL TinyMCE] 7需要在編輯器初始化設定中特別新增&#x200B;*字型大小*&#x200B;和&#x200B;*字型系列*&#x200B;選取器。

<u>要再現的步驟</u>：

前往「**[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Content]**」，然後選取「*[!UICONTROL Show Editor]*」。

<u>預期結果</u>：

在WYSIWYG編輯器中可以看到&#x200B;*字型大小*&#x200B;和&#x200B;*字型系列*&#x200B;選取器。

<u>實際結果</u>：

WYSIWYG編輯器中缺少&#x200B;*字型大小*&#x200B;選擇器。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
