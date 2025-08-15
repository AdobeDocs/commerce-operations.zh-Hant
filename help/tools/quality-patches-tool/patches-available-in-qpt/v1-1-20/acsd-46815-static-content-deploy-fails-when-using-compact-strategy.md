---
title: ACSD-46815：靜態內容部署無法使用壓縮策略
description: 套用ACSD-46815修補程式，修正使用壓縮策略時靜態內容部署失敗的Adobe Commerce問題。
feature: Deploy, Page Content, SCD
role: Admin
exl-id: 66941a83-daf8-4bb2-a575-b615e1c5dc7c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# ACSD-46815：使用精簡策略時，靜態內容部署失敗

ACSD-46815修補程式修正了使用精簡策略時，靜態內容部署失敗的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://support.magento.com/hc/en-us/articles/360047139492) 1.1.20時，即可使用此修補程式。 修補程式ID為ACSD-46815。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用精簡策略進行部署時，靜態內容部署會失敗。

<u>要再現的步驟</u>：

1. 執行下列命令，以壓縮策略部署靜態內容：

```bash
bin/magento setup:static-content:deploy -f -s compact
```

<u>預期結果</u>：

靜態內容部署已完成，沒有發生任何錯誤。

<u>實際結果</u>：

靜態內容部署因精簡策略而失敗。 部署過程中發生下列錯誤： *來自/app/pub/static/adminhtml/Magento/base/default/的內容。無法讀取/node_modules/@spectrum-css/vars/dist/spectrum-global.css檔案。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
