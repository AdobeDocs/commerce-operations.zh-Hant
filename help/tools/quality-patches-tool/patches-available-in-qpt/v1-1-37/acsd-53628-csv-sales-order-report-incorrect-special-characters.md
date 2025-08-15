---
title: ACSD-53628：CSV銷售訂單報表顯示不正確的特殊字元
description: 套用ACSD-53628修補程式，修正CSV銷售訂單報表顯示錯誤特殊字元的Adobe Commerce問題。
feature: Orders, Data Import/Export
role: Admin, Developer
exl-id: b6293efe-fbeb-4b1e-b408-34dc86228b8e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-53628：CSV銷售訂單報表顯示不正確的特殊字元

ACSD-53628修補程式修正CSV銷售訂單報表顯示錯誤特殊字元的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.37時，即可使用此修補程式。 修補程式ID為ACSD-53628。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法）： 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法）： 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

CSV銷售訂單報表顯示不正確的特殊字元。

<u>要再現的步驟</u>：

1. 在貨幣設定中將&#x200B;**[!UICONTROL Base Currency]**&#x200B;和&#x200B;**[!UICONTROL Default Display Currency]**&#x200B;變更為歐元。
1. 下訂單。
1. 在管理員側邊欄上，前往&#x200B;**[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**。
1. 選取日期。 按一下&#x200B;**[!UICONTROL Show Report]**。 按一下&#x200B;**[!UICONTROL Export]**&#x200B;匯出CSV。

<u>預期結果</u>：

轉存的CSV檔案中的特殊字元會在Excel中正確顯示。

<u>實際結果</u>：

CSV銷售訂單報告顯示的特殊字元不正確。


## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜尋修補程式[!DNL Quality Patches Tool]。
