---
title: 最佳化影像以建立回應速度較快的網站
description: 瞭解最佳化影像的步驟，並使用Fastly影像最佳化來最佳化Adobe Commerce網站上的回應時間。
role: Developer, Admin
feature: Best Practices
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 1%

---

# 最佳化影像以建立回應速度較快的網站

針對雲端基礎結構部署的Adobe Commerce，請先最佳化影像再上傳以縮短網站回應時間。 然後，使用Fastly影像最佳化來加速影像傳送並簡化影像來源集的維護。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md)：

雲端基礎結構上的Adobe Commerce


## 最佳化和壓縮影像

在將影像上傳至Commerce網站之前，請先最佳化並壓縮影像，以便在效能與檢視品質之間取得平衡。 這有助於增加空間並減少頁面載入時間。

- PNG格式可針對具有大範圍的純色影像提供較小大小的影像。

- JPEG格式可針對所有其他影像型別傳送較小大小的影像。 使用最高的壓縮率（不會明顯降低）。 這通常是60%到80%。

## 啟用和設定Fastly影像最佳化

在您為您的Adobe Commerce Cloud專案設定Fastly服務後，請參閱[Fastly影像最佳化](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html)以取得啟用和設定影像最佳化的指示。

## 其他資訊

- [設定Fastly](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
- [影像最佳化不良可能會導致效能問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)
