---
title: ACSD-48813：搜尋未根據屬性的搜尋權重顯示相關結果
description: 套用ACSD-48813修補程式，修正Adobe Commerce搜尋未根據屬性的搜尋權重顯示相關結果的問題。
feature: Admin Workspace, Attributes, Search
role: Admin
exl-id: 98ef7eb1-c13e-4c56-9a25-8e61cfb5fade
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-48813：搜尋未根據屬性的搜尋權重顯示相關結果

ACSD-48813修補程式修正搜尋未根據屬性的搜尋權重顯示相關結果的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29時，即可使用此修補程式。 修補程式ID為ACSD-48813。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

搜尋未根據屬性的搜尋權重顯示相關結果。

<u>要再現的步驟</u>：

1. 安裝Adobe Commerce並搭配範例資料。
1. 將搜尋引擎設為[!DNL Elasticsearch]。
1. 以管理員身分登入。
1. 前往&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Products]**。
1. 開啟&#x200B;*名稱*&#x200B;屬性。
1. 開啟店面&#x200B;*[!UICONTROL Properties]*&#x200B;標籤。
1. 從下拉式清單值中選取[!UICONTROL Search Weight] = *10*。
1. 按一下&#x200B;**[!UICONTROL Save Attribute]**。
1. 現在請開啟店面並搜尋&#x200B;*Back*&#x200B;這個字。

<u>預期結果</u>：

揹包產品會傳回搜尋結果頂端。

<u>實際結果</u>：

搜尋結果中間會傳回揹包產品。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
