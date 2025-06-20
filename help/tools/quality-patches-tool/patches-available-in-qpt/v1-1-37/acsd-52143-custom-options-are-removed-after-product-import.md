---
title: ACSD-52143：產品匯入後會移除自訂選項
description: 套用ACSD-52143修補程式來修正Adobe Commerce問題，此問題發生在產品匯入後，自訂選項遭到移除。
feature: Data Import/Export
role: Admin, Developer
exl-id: 630fffa7-012c-4539-9745-9a34571bd2eb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-52143：產品匯入後會移除自訂選項

ACSD-52143修補程式修正了產品匯入後移除自訂選項的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.37時，即可使用此修補程式。 修補程式ID為ACSD-52143。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

自訂選項會在產品匯入後移除。

<u>要再現的步驟</u>：

1. 前往&#x200B;**[!UICONTROL Store]** > **[!UICONTROL All Stores]**，並設定多商店執行個體（一個網站具有兩個商店檢視）。
1. 前往「**[!UICONTROL Catalog]** > **[!UICONTROL Products]**」，建立兩個具有[!UICONTROL Customizable Options]的產品。
1. 在每個產品中新增[!UICONTROL Customizable Option]。
1. 切換到第二個商店檢視，並修改每個產品的產品名稱。
1. 前往「**[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**」，並匯出您建立的兩個產品。
1. 下載CSV檔案。
1. 前往「**[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**」並重新匯入檔案。
1. 檢查兩個產品。

<u>預期結果</u>：

匯入產品後不會移除自訂選項。

<u>實際結果</u>：

產品匯入後會移除海關選項。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
