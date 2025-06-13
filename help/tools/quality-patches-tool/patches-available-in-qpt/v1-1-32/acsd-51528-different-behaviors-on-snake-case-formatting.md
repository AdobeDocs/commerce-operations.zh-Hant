---
title: ACSD-51528：對snake_case格式化的不同行為
description: 套用ACSD-51528修補程式以修正Snake_case格式有不同行為的Adobe Commerce問題。
feature: Variables
role: Admin
exl-id: 5f2add4b-8209-47a7-bfbd-cc434a050f0f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-51528：對snake_case格式化的不同行為

ACSD-51528修補程式可修正snake_case格式化的不同行為。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.32時，即可使用此修補程式。 修補程式ID為ACSD-51528。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

Snake_case格式化的不同行為。

<u>要再現的步驟</u>：

1. 使用各種不同的屬性名稱來測試`\Magento\Framework\Api\DataObjectHelper::populateWithArray`函式。
1. 名稱類似&#x200B;*NewPName*&#x200B;的屬性應該轉換為&#x200B;*new_p_name*，而要轉換為&#x200B;*new_pname*。
1. 此外，在物件中使用&#x200B;*getNewPName*&#x200B;函式時，將會傳回&#x200B;*null*，因為&#x200B;*抽象模型*&#x200B;會正確地將呼叫轉換成&#x200B;*new_p_name*，使這兩個函式彼此不相容。

<u>預期結果</u>

**[!UICONTROL populateWithArray]**&#x200B;函式應正確地將物件屬性轉換為snake_case，使其與&#x200B;**[!DNL AbstractModel's]** `Getters`和`Setters`相容。

<u>實際結果</u>

使用&#x200B;**[!UICONTROL populateWithArray]**&#x200B;函式時，任何物件屬性若其名稱一列中包含兩個以上大寫字母，將會導致最終資料陣列中的snake_case轉換不正確。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
