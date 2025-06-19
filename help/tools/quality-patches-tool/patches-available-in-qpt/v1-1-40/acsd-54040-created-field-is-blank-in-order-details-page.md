---
title: ACSD-54040：啟用B2B模組時，順序詳細資料中的[!UICONTROL Created]欄位為空白
description: 套用ACSD-54040修補程式以修正Adobe Commerce的問題，亦即啟用B2B模組時，訂單詳細資料頁面上的[!UICONTROL Created]欄位為空白。
feature: B2B
role: Admin, Developer
exl-id: 09fc1e0f-2e02-4cfc-9a7a-7c6aacd9fee0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-54040：啟用B2B模組時，順序詳細資料中的&#x200B;*[!UICONTROL Created]*&#x200B;欄位為空白。

ACSD-54040修補程式修正啟用B2B模組時，訂單詳細資料頁面上的&#x200B;*[!UICONTROL Created]*&#x200B;欄位保持空白的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40時，即可使用此修補程式。 修補程式ID為ACSD-54040。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4-p5、2.4.4-p6、2.4.5-p4、2.4.5-p5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

啟用B2B模組時，訂單詳細資訊頁面上的&#x200B;*[!UICONTROL Created]*&#x200B;欄位會保持空白。

<u>要再現的步驟</u>：

1. 使用B2B模組安裝Adobe Commerce。
1. 建立新客戶並下訂單。
1. 前往前端上的訂單詳細資料，並檢查&#x200B;*[!UICONTROL Created]*&#x200B;欄位。

<u>預期結果</u>：

*[!UICONTROL Created]*&#x200B;欄位會顯示建立訂單的日期。

<u>實際結果</u>：

*[!UICONTROL Created]*&#x200B;欄位為空白

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
