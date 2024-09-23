---
title: 「ACSD-56760：管理員使用者僅限於特定網站，無法排序或新增產品」
description: 套用ACSD-56760修補程式來修正Adobe Commerce問題，該問題導致僅限特定網站的管理員使用者無法排序或新增產品，以致於網路商店擁有自己的根類別。
role: Admin
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# ACSD-56760：管理員使用者僅限於特定網站，無法排序或新增產品

ACSD-56760修補程式修正僅限特定網站的Admin使用者無法排序或新增類別（萬一網站商店有自己的根類別）中的新產品問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.47時，即可使用此修補程式。 修補程式ID為ACSD-56760。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

僅限特定網站使用的管理員使用者，如果網站商店擁有自己的根類別，則無法在類別內排序或新增產品。

<u>要再現的步驟</u>：

1. 建立&#x200B;*2*&#x200B;網站。
1. 建立只能存取&#x200B;*1*&#x200B;網站的&#x200B;**[!UICONTROL restricted admin user]**。
1. 以&#x200B;**[!UICONTROL restricted admin user]**&#x200B;身分登入，並嘗試變更類別中的產品位置。

*案例1*：

* *2*&#x200B;個存放區。
* *2*&#x200B;根類別，每個網站都指派給自己的類別根目錄。

*案例2*：

* *2*&#x200B;個存放區。
* 只將&#x200B;*1*&#x200B;根類別指派給兩個網站。

<u>預期結果</u>：

* *案例1*：受限制的管理員應該能夠排序可用類別中的產品。
* *案例2*：受限管理員無法排序可用類別中的產品，因為這樣也會影響受限商店。

<u>實際結果</u>：

* *案例1*：受限制的管理員無法排序可用類別中的產品。
* *案例2*：受限制的管理員可以對可用類別中的產品進行排序，進而影響受限制的商店。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
