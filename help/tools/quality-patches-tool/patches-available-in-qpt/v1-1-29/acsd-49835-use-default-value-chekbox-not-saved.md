---
title: 'ACSD-49835：未儲存[!UICONTROL Use Default Value]核取方塊'
description: 套用ACSD-49835修補程式以修正Adobe Commerce問題，該問題導致在多重選取屬性的存放區層級上未正確儲存[!UICONTROL Use Default Value]核取方塊。
feature: Storefront
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# acsd-49835：未儲存[!UICONTROL Use Default Value]核取方塊

ACSD-49835修補程式修正多選屬性之存放區層級未正確儲存「[!UICONTROL Use Default Value]」核取方塊的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29時，即可使用此修補程式。 修補程式ID為ACSD-49835。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

多選屬性的[!UICONTROL Use Default Value]核取方塊未正確儲存在存放區層級。

<u>要再現的步驟</u>：

1. 在&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**&#x200B;中建立&#x200B;**[!UICONTROL Multiple-select Attribute]**，並將其新增至屬性集。
1. 移至&#x200B;**[!UICONTROL Product]**&#x200B;並在&#x200B;**[!UICONTROL All Store Views (Default Scope)]**&#x200B;中儲存&#x200B;**[!UICONTROL Values]**。
1. 前往特定&#x200B;**[!UICONTROL Store View Scope]**&#x200B;並儲存產品。
1. 移至&#x200B;**[!UICONTROL Store View Scope]**&#x200B;並勾選&#x200B;**[!UICONTROL Use Default Value]**&#x200B;核取方塊。

<u>預期結果</u>：

核取[!UICONTROL Store View Scope]中的[!UICONTROL Use Default Value]核取方塊時，多選屬性值已正確儲存。

<u>實際結果</u>：

核取[!UICONTROL Store View Scope]中的[!UICONTROL Use Default Value]核取方塊時，未正確儲存多重選取屬性值。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
