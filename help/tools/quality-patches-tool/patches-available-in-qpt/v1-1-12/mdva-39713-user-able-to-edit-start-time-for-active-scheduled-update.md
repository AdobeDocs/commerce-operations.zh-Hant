---
title: MDVA-39713：使用者可以編輯作用中排程更新的開始時間
description: MDVA-39713修補程式修正使用者可編輯作用中排程更新之開始時間的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12後，即可使用此修補程式。 修補程式ID為MDVA-39713。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: CMS
role: Admin
exl-id: 450a968f-a5ed-478f-a857-579fea1eb3b7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# MDVA-39713：使用者可以編輯作用中排程更新的開始時間

MDVA-39713修補程式修正使用者可編輯作用中排程更新之開始時間的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12時，即可使用此修補程式。 修補程式ID為MDVA-39713。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.3.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.3.6

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用者可以編輯作用中排程更新的開始時間。

<u>要再現的步驟</u>：

1. 建立新的CMS頁面。
1. 選取&#x200B;**排程新更新**&#x200B;並將&#x200B;**開始日期**&#x200B;設定為目前的+1分鐘。
1. 在本機環境中執行命令`bin/magento cron:run --group=staging`以啟動排程更新。 請等候數分鐘，然後檢查排程是否作用中。
1. 排程啟動後，請重新整理頁面。
1. 按一下[排程變更]區段中的[檢視/編輯&#x200B;****。
1. 新增+2分鐘以編輯時間並儲存變更。
1. 儲存CMS頁面。
1. 再次執行以下命令： `bin/magento cron:run --group=staging`。
1. 按一下排程更新的&#x200B;**檢視/編輯**。

<u>預期結果</u>：

使用者無法編輯作用中排程更新的開始時間。

<u>實際結果</u>：

使用者收到類似相同識別碼「11」的&#x200B;*專案(Magento\Cms\Model\Page)的錯誤。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
