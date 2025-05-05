---
title: ACSD-63067：解決店面分組產品的數量驗證問題
description: 套用ACSD-63067修補程式來修正Adobe Commerce問題，即當只有一個產品的數量不正確時，已分組產品中的所有產品數量會不正確地標示為無效。
feature: Storefront
role: Admin, Developer
source-git-commit: 7446f4d83932eedc6fa711ad09c6ee559d357f70
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-63067：解決店面分組產品的數量驗證問題

ACSD-63067修補程式修正了當只有一個產品的數量不正確時，已分組產品中的所有產品數量會不正確地標示為無效的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58時，即可使用此修補程式。 修補程式ID為ACSD-63067。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.7-p2

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在群組產品中，其中一個子產品的無效數量會導致所有數量都錯誤地反白為無效。 此外，所有產品都會顯示驗證訊息，而非僅針對數量無效的產品。

<u>要再現的步驟</u>：

1. 建立新的群組產品，並至少包含兩個簡單產品作為選項。
1. 在店面開啟產品。
1. 為其中一個選項輸入無效數量（例如： -1），為剩餘選項輸入有效數量（例如： 1）。
1. 按一下&#x200B;**[!UICONTROL Add to Cart]**。

<u>預期結果</u>：

只有具有無效數量的產品才會反白為無效。

<u>實際結果</u>：

所有產品數量都會標示為無效，且訊息&#x200B;*請指定產品數量。 會針對所有產品*&#x200B;顯示。


## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
