---
title: ACSD-65983：在Admin中重新設定套件式產品報價時發生錯誤
description: 套用ACSD-65983修補程式以修正嘗試在後端的[!UICONTROL Sales] > [!UICONTROL Quotes] > [!UICONTROL Edit]畫面中設定套件組合產品時出現錯誤的Adobe Commerce問題。
feature: B2B, Quotes
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8a8f2b273bcbcf135677ad7ca289398bf660e02e
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---


# ACSD-65983：在Admin中重新設定套件式產品報價時發生錯誤

ACSD-65983修補程式修正在Admin後端重新設定隨附的產品報價傳回錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69時，即可使用此修補程式。 修補程式ID為ACSD-65983。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在管理員後端重新設定套件產品報價傳回錯誤。

<u>要再現的步驟</u>：

1. 移至[管理]面板並啟用&#x200B;**[!UICONTROL B2B Feature]**： **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Feature]**。
1. 建立固定數量的套件組合產品（例如： *$10*），並加入&#x200B;*0*&#x200B;數量、*選項1*&#x200B;中的&#x200B;**2**&#x200B;以及&#x200B;*選項2*&#x200B;中的&#x200B;**other**&#x200B;的三個或更多簡單產品。
1. 從前端建立公司帳戶。
1. 移至&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]**，將建立的公司和產品指派給新的/自訂共用目錄。
1. 在前端以&#x200B;**公司使用者**&#x200B;身分登入，並從套件新增一個簡單的產品至購物車。
1. 開啟購物車頁面，並以&#x200B;**要求報價**&#x200B;的形式提交。
1. 移至後端，並編輯建立的報價。
1. 在&#x200B;**報價專案**&#x200B;區段中，按一下&#x200B;**設定**&#x200B;按鈕。
1. 從&#x200B;**選項2**&#x200B;中選取其他簡單產品。
1. 現在按一下&#x200B;**確定**&#x200B;按鈕並檢視錯誤訊息。

<u>預期結果</u>：

您可以正常地從管理員成功設定要求的報價專案，而不會顯示錯誤訊息。

<u>實際結果</u>：

您會看到錯誤訊息：

*伺服器的技術問題造成錯誤。 請再試一次，繼續您正在執行的動作。 如果問題仍然存在，請稍後再試。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]： Tools指南中用於品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具
