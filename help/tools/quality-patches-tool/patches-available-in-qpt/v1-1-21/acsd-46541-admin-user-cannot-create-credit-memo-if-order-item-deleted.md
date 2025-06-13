---
title: ACSD-46541：如果刪除訂單專案，管理員使用者無法建立銷退折讓單
description: 套用ACSD-46541修補程式以修正Adobe Commerce問題，其中一旦刪除產品，您就無法在Adobe Commerce管理員中建立銷退折讓單。
feature: Admin Workspace, Orders, Returns
role: Admin
exl-id: c46ee888-92b1-4798-bd2b-1a082fd1406a
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-46541：如果刪除訂單專案，管理員使用者無法建立銷退折讓單

ACSD-46541修補程式修正了刪除訂單專案時，管理員使用者無法建立銷退折讓單的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21時，即可使用此修補程式。 修補程式ID為ACSD-46541。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

刪除產品後，您就無法在「Commerce管理員」中建立銷退折讓單。

<u>要再現的步驟</u>：

1. 登入Commerce管理員。
1. 建立訂單。
1. 為訂單開立商業發票。
1. 從訂單中刪除產品。
1. 按一下訂單編輯頁面上的&#x200B;**[!UICONTROL Credit Memo]**&#x200B;連結。
1. 按一下&#x200B;**[!UICONTROL Refund Offline]**&#x200B;以建立銷退折讓單。

<u>預期結果</u>：

已成功建立銷退折讓單。

<u>實際結果</u>：

找不到&#x200B;_含有要求SKU的下列產品：顯示SKU001_&#x200B;錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
