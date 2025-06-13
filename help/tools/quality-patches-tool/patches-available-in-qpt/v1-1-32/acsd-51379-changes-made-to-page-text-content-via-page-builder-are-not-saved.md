---
title: ACSD-51379：未儲存透過 [!DNL Page Builder] 對頁面文字內容所做的變更
description: 套用ACSD-51379修補程式以修正無法透過 [!DNL Page Builder] 儲存對頁面文字內容所做變更的Adobe Commerce問題。
feature: Page Builder, Page Content
role: Admin
exl-id: 03fc2865-04b6-4330-b80c-8d694baa8c88
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-51379：未儲存透過[!DNL Page Builder]對頁面文字內容所做的變更

ACSD-51379修補程式修正無法透過[!DNL Page Builder]儲存對頁面文字內容所做變更的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32時，即可使用此修補程式。 修補程式ID為ACSD-51379。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

未儲存透過[!DNL Page Builder]對頁面文字內容所做的變更。

<u>要再現的步驟</u>：

1. 登入管理員。
1. 前往&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**。
1. 在&#x200B;**[!UICONTROL Content]**&#x200B;索引標籤上建立一個包含一個列和一個文字元素的測試頁面。
1. 儲存頁面並返回&#x200B;**[!UICONTROL Content]**&#x200B;標籤。
1. 選取文字並加以變更，即可編輯文字。

   **注意：**&#x200B;只有選取並變更文字而未啟動編輯器時，此問題才能重現。

1. 按一下測試頁面上的&#x200B;**[!UICONTROL Save and Close]**&#x200B;按鈕。
1. 再次開啟測試頁面並檢查&#x200B;**[!UICONTROL Content]**&#x200B;索引標籤。

<u>預期結果</u>：

新文字已成功儲存為原始和重複的文字元素。

<u>實際結果</u>：

文字元素已成功複製，但未儲存新文字。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
