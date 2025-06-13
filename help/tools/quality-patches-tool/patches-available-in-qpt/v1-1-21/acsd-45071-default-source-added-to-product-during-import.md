---
title: ACSD-45071：匯入期間新增到產品的預設來源
description: ACSD-45071修補程式可解決匯入期間將預設來源新增至產品的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21時，即可使用此修補程式。 修補程式ID為ACSD-45071。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
feature: Data Import/Export, Products
role: Admin
exl-id: d28cbfb1-ad6b-4ccf-a877-6db763cea61b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-45071：匯入期間新增到產品的預設來源

ACSD-45071修補程式可解決匯入期間將預設來源新增至產品的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21時，即可使用此修補程式。 修補程式ID為ACSD-45071。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.3-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

產品匯入後，預設來源會自動指定給產品，數量會設為零，狀態會設為「無庫存」。

<u>要再現的步驟</u>：

1. 建立新的來源。
1. 使用新來源建立新庫存。
1. 在Adobe Commerce管理員的產品編輯頁面上，僅指派自訂庫存、設定一些數量並將庫存狀態設定為&#x200B;**[!UICONTROL In Stock]**。
1. 透過&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**&#x200B;匯入產品。

<u>預期結果</u>：

匯入後預設來源不會自動指派給產品。

<u>實際結果</u>：

以無庫存狀態和零數量匯入後，預設來源會指定給產品。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
