---
title: MDVA-41350：當管理員在存取權之外新增產品時會發生例外狀況
description: MDVA-41350修補程式修正了當管理員使用者按其存取權以外的SKU的順序新增產品時，擲回例外狀況錯誤，而非限制存取通知的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11後，即可使用此修補程式。 修補程式ID為MDVA-41350。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: Admin Workspace, Products
role: Admin
exl-id: 4dc5ee5c-bd93-42e1-9c63-93ffb8e5f21c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-41350：當管理員在存取權之外新增產品時會發生例外狀況

MDVA-41350修補程式修正了當管理員使用者按其存取權以外的SKU的順序新增產品時，擲回例外狀況錯誤，而非限制存取通知的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11時，即可使用此修補程式。 修補程式ID為MDVA-41350。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.3.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當具有受限制存取權的管理員使用者在順序中其存取權之外透過SKU新增產品時，會發生例外狀況，而不是出現通知使用者其受限制存取權的訊息。

<u>要再現的步驟</u>：

1. 以僅能存取特定網站的使用者身分登入管理員。
1. 移至&#x200B;**銷售** > **訂單**，然後按一下&#x200B;**建立新訂單**。
1. 選取客戶和商店檢視。
1. 按一下&#x200B;**「依SKU新增產品」**。
1. 搜尋未指派給任何網站或未指派給您有權存取之網站的SKU。
1. 按一下&#x200B;**新增至訂單**。

<u>預期結果</u>：

此時會顯示適當的錯誤訊息。

<u>實際結果</u>：

發生例外狀況。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
