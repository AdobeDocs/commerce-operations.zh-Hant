---
title: ACSD-59514：Admin中的Forms在瀏覽器控制檯中出現 [!DNL Page Builder] 擲回錯誤
description: 套用ACSD-59514修補程式以修正Admin中具有 [!DNL Page Builder] 擲回的表單錯誤「[!DNL Page Builder]」呈現達5秒而未釋放鎖定的Adobe Commerce問題。 在瀏覽器主控台中提交表單後，變更無法儲存。
feature: Page Builder
role: Admin, Developer
exl-id: 3d1167d2-0a75-48ac-bc31-5bbd3c4a409e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-59514：在瀏覽器控制檯中出現[!DNL Page Builder]擲回錯誤的Admin中的Forms

ACSD-59514修補程式修正Admin中具有[!DNL Page Builder]的表單擲回錯誤&#x200B;*[!DNL Page Builder]未解除鎖定就呈現5秒的問題。在瀏覽器主控台中提交表單後*，變更無法儲存。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50時，即可使用此修補程式。 修補程式ID為ACSD-59514。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

具有[!DNL Page Builder]的Admin中的Forms擲回錯誤&#x200B;*[!DNL Page Builder]呈現了5秒鐘，但未釋放鎖定。在瀏覽器主控台中提交表單後*，變更無法儲存。

<u>必要條件</u>：

Adobe Commerce [!DNL Page Builder]模組已安裝且已啟用。

<u>要再現的步驟</u>：

1. 開啟管理面板，然後按一下[!UICONTROL Content]按鈕。
1. 選取區塊並編輯區塊。
1. 變更內容並按一下[!UICONTROL Save]。
1. 開啟主控台並檢視錯誤訊息。

<u>預期結果</u>：

已成功儲存區塊。

<u>實際結果</u>：

載入器不會停止旋轉，而且不會儲存區塊。 瀏覽器主控台中顯示下列錯誤：
*[!DNL Page Builder]已呈現5秒鐘，但未解除鎖定。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
