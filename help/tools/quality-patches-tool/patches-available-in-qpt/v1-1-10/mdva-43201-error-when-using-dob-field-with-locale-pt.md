---
title: MDVA-43201：搭配地區設定PT使用DOB欄位時發生錯誤
description: MDVA-43201修補程式可解決在葡萄牙地區設定的客戶登錄檔單中使用DOB客戶屬性時發生錯誤的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10時，即可使用此修補程式。 修補程式ID為MDVA-43201。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
feature: B2B, Cache
role: Admin
exl-id: be087420-1ee3-40cc-8ff7-62c5641609cc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-43201：搭配地區設定PT使用DOB欄位時發生錯誤

MDVA-43201修補程式可解決在葡萄牙地區設定的客戶登錄檔單中使用DOB客戶屬性時發生錯誤的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10時，即可使用此修補程式。 修補程式ID為MDVA-43201。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

將DOB客戶屬性新增至葡萄牙地區設定的客戶登錄檔單時，表單會提供錯誤&#x200B;*傳遞給iterator_to_array()的引數1必須實作介面可移轉，指定null*。

<u>必要條件</u>：

B2B模組已安裝。

<u>要再現的步驟</u>：

1. 移至[管理] > **商店** > **設定** > **一般** > **地區設定選項**，將地區設定設為&#x200B;**葡萄牙文（葡萄牙）**，然後按一下[儲存] ****。
1. 重新索引並清除快取。
1. 移至&#x200B;**商店** > **屬性** > **客戶**。
1. 開啟DOB客戶屬性並將&#x200B;**在店面顯示**&#x200B;設定為&#x200B;**是**。
1. 從&#x200B;**表單中選取要在**&#x200B;中使用的全部。
1. 儲存屬性。
1. 前往前端的「建立新帳戶」頁面。

<u>預期結果</u>：

葡萄牙商店的客戶登錄檔單在新增DOB屬性時沒有提供錯誤。

<u>實際結果</u>：

葡萄牙商店的客戶登錄檔單在新增DOB屬性時發生錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
