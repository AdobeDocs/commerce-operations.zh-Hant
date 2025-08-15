---
title: ACSD-48313：如果屬性值包含逗號，則未剖析[!UICONTROL configurable_variations]欄
description: 套用ACSD-48313修補程式以修正Adobe Commerce問題，若屬性值包含逗號，則不會剖析[!UICONTROL configurable_variations]欄。
feature: Attributes, Configuration
role: Admin
exl-id: 1ce0c8dc-0d03-4ebd-b02a-08090b244190
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-48313：如果屬性值包含逗號，則未剖析&#x200B;**[!UICONTROL configurable_variations]**&#x200B;欄

ACSD-48313修補程式解決屬性值包含逗號時無法剖析&#x200B;**[!UICONTROL configurable_variations]**&#x200B;欄的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25時，即可使用此修補程式。 修補程式ID為ACSD-48313。 尚未提供將修正此問題的版本。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.4-p5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

匯出可設定的產品後，由於&#x200B;**[!UICONTROL configurable_variations]**&#x200B;屬性的格式問題，無法再次匯入產生的檔案。 當屬性選項包含逗號時，就會發生這種情況。

<u>要再現的步驟</u>：

1. 移至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**&#x200B;並建立新的屬性&#x200B;_大小_：
1. 存放區擁有者的目錄輸入型別： **[!UICONTROL Dropdown]**。
1. 建立包含逗號在內的選項，例如：
   * 10,2公分
   * 15,5公分
1. **[!UICONTROL Advanced Attribute Properties]** — 範圍： _全域_。
1. 使用「建立組態」功能建立新的可設定產品。
1. 選取上述屬性&#x200B;_Size_&#x200B;以及包含逗號的兩個選項。
1. 前往&#x200B;**[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**&#x200B;並建立新的產品匯出（執行cron以觸發CSV檔案的產生）。
1. 前往「**[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**」，然後嘗試重新匯入上述建立的相同CSV檔案。

<u>預期結果</u>：

使用者應該能夠匯入檔案。

<u>實際結果</u>：

```
1. Column configurable_variations: Attribute with code "2cm" does not exist or is missing from product attribute set in row(s): 3
2. Column configurable_variations: Attribute with code "5cm" does not exist or is missing from product attribute set in row(s): 3
3. Column configurable_variations: Invalid option value for attribute "size" in row(s): 3
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
