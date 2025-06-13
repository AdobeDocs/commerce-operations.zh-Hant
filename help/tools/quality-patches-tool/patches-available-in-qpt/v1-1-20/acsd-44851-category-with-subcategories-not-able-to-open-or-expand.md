---
title: ACSD-44851：子類別無法開啟或展開的類別
description: 本文提供使用者無法開啟或展開具有子類別的類別問題的解決方案。
feature: Categories
role: Admin
exl-id: c1ad13d8-94e1-47cf-ad65-9bc5ce1c26ad
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-44851：子類別無法開啟或展開的類別

ACSD-44851修補程式解決使用者無法開啟或展開具有子類別的類別的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20時，即可使用此修補程式。 修補程式ID為ACSD-44851。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用者無法開啟或展開具有子類別的類別。

<u>要再現的步驟</u>：

1. 在「Adobe Commerce管理員」中，建立包含兩個根類別的類別樹狀結構，並為每個類別設定幾個子類別。
1. 開啟行動檢視/模擬器或縮小視窗寬度，直到版面配置變成行動為止。
1. 開啟目錄的主功能表。
1. 嘗試展開根類別。
1. 嘗試開啟類別。

<u>預期結果</u>：

功能表可供存取。

<u>實際結果</u>：

行動功能表的第二層級未開啟。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [品質修補工具>使用狀況](/help/tools/quality-patches-tool/usage.md) （在品質修補工具指南中）。

* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
