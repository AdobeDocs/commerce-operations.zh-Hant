---
title: ACSD-59967： JavaScript錯誤導致 [!DNL Google Maps] 無法正確呈現
description: 套用ACSD-59967修補程式以修正JavaScript錯誤導致 [!DNL Google Maps] 無法正確呈現的Adobe Commerce問題。
feature: Admin Workspace, Page Builder, CMS
role: Admin, Developer
exl-id: 2982857a-7adb-4163-be18-4d2caf0d645c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-59967： JavaScript錯誤導致[!DNL Google Maps]無法正確呈現

ACSD-59967修補程式修正JavaScript錯誤導致[!DNL Google Maps]無法正確呈現的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51時，即可使用此修補程式。 修補程式ID為ACSD-59967。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.4-p3

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

JavaScript錯誤導致[!DNL Google Maps]無法正確呈現。

<u>要再現的步驟</u>：

1. 產生有效的[!DNL Google Maps]金鑰。
1. 在[!DNL Google Maps] > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]**&#x200B;下設定&#x200B;**[!UICONTROL Content Management]** API金鑰。
1. 將您的[!DNL Google API Key]新增至&#x200B;**[!UICONTROL Google Maps API Key]**&#x200B;欄位並儲存設定。
1. 前往「**[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]** > **[!UICONTROL Create New Page]**」。
1. 新增&#x200B;**[!UICONTROL Row]**&#x200B;專案和&#x200B;**[!UICONTROL Maps]**&#x200B;專案。

<u>預期結果</u>：

主控台中沒有JavaScript錯誤，且地圖在&#x200B;*店面*&#x200B;和&#x200B;*管理員*&#x200B;上正確轉譯。

<u>實際結果</u>：

JavaScript錯誤會顯示在主控台中，且對應未正確轉譯。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
