---
title: ACSD-49065：報價專案在管理員中不可見
description: 套用ACSD-49065修補程式來修正Adobe Commerce問題，亦即如果報價專案僅指派給自訂庫存，則無法在管理員中看到報價專案。
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
exl-id: fc3bea92-305b-4598-9915-3422d61c76ec
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-49065：報價專案在管理員中不可見

ACSD-49065修補程式修正了報價專案僅指定給自訂庫存時無法在管理員中顯示的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28時，即可使用此修補程式。 修補程式ID為ACSD-49065。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果報價專案僅指派給自訂庫存，則不會在管理員中顯示。

先決條件：

必須安裝&#x200B;**[!UICONTROL B2B]**&#x200B;與&#x200B;**[!UICONTROL Inventory]**&#x200B;模組。

<u>要再現的步驟</u>：

1. 在&#x200B;**[!UICONTROL Company]** > **[!UICONTROL B2B Quote]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]**&#x200B;下啟用&#x200B;**[!UICONTROL General]**&#x200B;和&#x200B;**[!UICONTROL B2B Features]**。
1. 建立次要&#x200B;**[!UICONTROL Inventory Source]**&#x200B;並將其指派給次要&#x200B;**[!UICONTROL Inventory Stock]**。
1. 僅指派次要（非預設） **[!UICONTROL Inventory Source]**&#x200B;以建立新產品。
1. 前往店面並建立新的公司帳戶。 以&#x200B;**[!UICONTROL Company Admin]**&#x200B;身分登入，並將建立的產品加入購物車。
1. 瀏覽到購物車和&#x200B;*[!UICONTROL Request a Quote]*。
1. 前往管理員，並在&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Quotes]**&#x200B;檢視要求的報價。

<u>預期結果</u>：

專案會顯示在以新產品建立的新報價中，而不需重新儲存產品。

<u>實際結果</u>：

*[!UICONTROL Items Quoted]*&#x200B;區段是空的。 如果您重新儲存新建立的產品，專案就會出現。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
