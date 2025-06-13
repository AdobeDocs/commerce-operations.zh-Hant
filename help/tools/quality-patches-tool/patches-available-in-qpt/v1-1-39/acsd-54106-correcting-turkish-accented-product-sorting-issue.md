---
title: ACSD-54106：修正產品類別中的土耳其文重音字元排序
description: 套用ACSD-54106修補程式，修正Adobe Commerce中土耳其文重音字元依名稱排序的類別產品順序不正確的問題。
feature: Categories, Products, Search
role: Admin
exl-id: 45c8efbb-85d0-4d25-9d7e-9c41a97e80fa
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-54106：修正產品類別中的土耳其文重音字元排序

ACSD-54106修補程式修正土耳其文重音字元依名稱排序的類別產品順序不正確的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.39時，即可使用此修補程式。 修補程式ID為ACSD-54106。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1 - 2.4.4-p5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

按名稱排序類別中的產品時，土耳其重音字元排序不正確。

<u>要再現的步驟</u>：

1. 登入管理面板。
1. 建立以下命名的簡單產品，並將其指派給任何類別：

* 名稱A
* 名稱C
* 名稱D
* 名稱
* 名稱M
* Ö姓名
* 名稱U
* 名稱Y
* 名稱Z

1. 導覽至店面並存取包含產品的類別。
1. 將排序順序修改為&#x200B;*[!UICONTROL By Name]*。

<u>預期結果</u>：

產品會依照下列順序正確排序：

* 名稱A
* 名稱C
* 名稱D
* 名稱
* 名稱M
* Ö姓名
* 名稱U
* 名稱Y
* 名稱Z

<u>實際結果</u>：

產品未正確依下列順序排序：

* 名稱A
* 名稱D
* 名稱M
* 名稱Y
* 名稱Z
* 名稱C
* Ö姓名
* 名稱U
* 名稱

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
