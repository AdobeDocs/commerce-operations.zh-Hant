---
title: ACSD-62355：改善Adobe Commerce中可設定的產品編輯效能
description: 套用ACSD-62355修補程式來修正Adobe Commerce問題，該問題導致當產品根據具有許多值的許多屬性時，可設定的產品編輯頁面載入緩慢。
feature: Admin Workspace
role: Admin, Developer
exl-id: cd934aa9-901a-4f03-ab83-716131e6bd85
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# ACSD-62355：改善Adobe Commerce中可設定的產品編輯效能

ACSD-62355修補程式修正了可設定產品編輯頁面上，產品具有許多值屬性時，載入時間緩慢及記憶體耗用量高的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56時，即可使用此修補程式。 修補程式ID為ACSD-62355。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當可設定產品是根據多個具有多個值的屬性時，可設定的產品編輯頁面需要很長時間才能載入，導致延遲以及潛在的逾時或記憶體限制問題。

<u>要再現的步驟</u>：

1. 在預設屬性集中建立9個新屬性，每個都是[!UICONTROL Filterable]且有[!UICONTROL Scope]： [!UICONTROL Global]。
   * 屬性1:50個選項
   * 屬性2:20個選項
   * 屬性3:10個選項
   * 屬性4:5個選項
   * 屬性5:5個選項
   * 屬性6:5個選項
   * 屬性7:5個選項
   * 屬性8:3個選項
   * 屬性9:2個選項

1. 使用新建立屬性的選項組合，建立9個簡單產品。
   * 產品1：每個屬性的第一個選項
   * 產品2：每個屬性的第二個選項
   * 產品3：每個屬性的第三個選項
   * 產品4：每個屬性的第四個選項
   * 如果屬性的選項數少於產品數，請將剩餘產品指派給該屬性內的隨機選項。

1. 建立使用新建立屬性的可設定產品：
   * 使用下列設定新增一個子產品：
      * 使用屬性1的最後一個選項，以及屬性2至9的第一個選項。
      * 這會產生1個可設定的產品和1個子產品。
1. 前往可設定產品的&#x200B;**[!UICONTROL Configurations]**&#x200B;標籤。
1. 手動按一下&#x200B;**[!UICONTROL Add Products]**，開始逐一新增先前建立的簡單產品。
1. 每次新增後儲存變更。
1. 當您新增產品時，請觀察編輯可設定產品頁面的載入時間。
1. 新增7項產品後，您應該會注意到RAM耗用量和頁面載入時間大幅增加

<u>預期結果</u>：

產品編輯表單應可快速有效率地載入，而不會造成記憶體過度耗用。

<u>實際結果</u>：

編輯可設定的產品需要很長時間才能載入，而且可能會達到記憶體限制或逾時錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
