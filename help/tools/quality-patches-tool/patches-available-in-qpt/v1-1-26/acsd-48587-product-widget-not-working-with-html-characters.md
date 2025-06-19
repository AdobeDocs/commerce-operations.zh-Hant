---
title: ACSD-48587：產品Widget無法使用包含HTML字元的SKU
description: 套用ACSD-48587修補程式，修正Adobe Commerce中產品Widget比對規則中的HTML特殊字元無法顯示相符產品的問題。
feature: Admin Workspace, CMS, Orders, Products
role: Admin
exl-id: c3e31835-03be-46b4-a080-09edf55b5b4e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-48587：產品Widget無法使用包含HTML字元的SKU

ACSD-48587修補程式修正產品Widget比對規則中HTML特殊字元無法顯示相符產品的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26時，即可使用此修補程式。 修補程式ID為ACSD-48587。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

產品Widget無法使用包含&#x200B;*&amp;&quot;*&#x200B;符號的SKU。

<u>要再現的步驟</u>：

1. 在SKU中建立包含&#x200B;*&amp;&quot;*&#x200B;的產品（例如s000&amp;01）。
1. 在&#x200B;*頁面產生器*&#x200B;上編輯CMS頁面的內容。
1. 新增產品Widget。
1. 編輯Widget並設定&#x200B;**[!UICONTROL Select Products by]** = **[!UICONTROL SKU]**。
1. 在產品SKU欄位中輸入包含&#x200B;*&amp;&quot;*&#x200B;的SKU。
1. 儲存內容和CMS頁面。
1. 檢查&#x200B;*CMS頁面*&#x200B;內容，以取得&#x200B;*頁面產生器預覽*&#x200B;和產品店面。

<u>預期結果</u>：

SKU中具有&#x200B;*&amp;&quot;*&#x200B;的產品會顯示在「頁面產生器」預覽和店面上。

<u>實際結果</u>：

SKU中具有&#x200B;*&amp;&quot;*&#x200B;的產品未顯示在頁面產生器預覽中。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
