---
title: ACSD-63454：下拉式清單和多選屬性的預設值未正確儲存在資料庫中
description: 套用ACSD-63454修補程式以修正Adobe Commerce中，下拉式清單和多選屬性的預設值未正確儲存在資料庫中的問題。
feature: Attributes, Products
role: Admin, Developer
exl-id: fa79a3bb-e615-44cb-8d84-da892f924fd0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-63454：資料庫中未正確儲存[!UICONTROL Dropdown]和[!UICONTROL Multiple Select]屬性的預設值

ACSD-63454修補程式修正[!UICONTROL Dropdown]和[!UICONTROL Multiple Select]屬性的預設值未正確儲存在資料庫中的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59時，即可使用此修補程式。 修補程式ID為ACSD-63454。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

[!UICONTROL Dropdown]和[!UICONTROL Multiple Select]屬性的預設值未正確儲存在資料庫中；新值會附加至舊值（以逗號分隔），而不是更新預設值。

<u>要再現的步驟</u>：

1. 登入後端，前往&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Product]**。
1. 按一下&#x200B;**[!UICONTROL Add New Attribute]**。
1. 在&#x200B;**[!UICONTROL Properties]**&#x200B;索引標籤中，設定下列專案：
   * **[!UICONTROL Default Label]**： *測試*
   * **[!UICONTROL Catalog Input Type for Store Owner]**： *[!UICONTROL Multiple Select]*
   * **[!UICONTROL Manage Options]**：新增兩個選項，但不選取&#x200B;**[!UICONTROL Is Default]**。
1. 按一下&#x200B;**[!UICONTROL Save Attribute]**。
1. 在資料庫中檢查`default_value`資料行是否空白。

   `select attribute_code, default_value from eav_attribute where attribute_code = 'test';`

1. 返回並將兩個選項之一設定為&#x200B;**[!UICONTROL Is Default]**。
1. 再次檢查資料庫，以確定`default_value`現在包含選取的選項識別碼。
1. 返回並選取其他選項來變更預設選項。

<u>預期結果</u>：

新的預設值應該取代資料庫中的舊值。

<u>實際結果</u>：

此方法不會將預設值取代為新值，而是將新值附加至舊值，並以逗號分隔。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
