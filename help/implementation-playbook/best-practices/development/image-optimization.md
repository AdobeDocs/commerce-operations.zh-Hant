---
title: 最佳化回應更快的網站影像
description: 了解最佳化影像和使用Abmey影像最佳化來最佳化Adobe Commerce網站回應時間的步驟。
role: Developer, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 最佳化回應更快的網站影像

針對Adobe Commerce部署雲端基礎架構，請先最佳化影像，再上傳影像，以縮短網站回應時間。 然後，利用Ampliet影像優化技術來加快影像傳送速度，簡化影像源集的維護。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

Adobe Commerce雲基礎架構


## 優化和壓縮影像

將影像上傳至您的商務網站之前，請先最佳化和壓縮影像，以平衡效能與檢視品質。 這有助於增加空間並縮短頁面載入時間。

- PNG格式可為實色區域較大的影像提供較小大小的影像。

- JPEG格式可為所有其他影像類型提供較小的影像大小。 使用最高的壓縮（沒有明顯的降級）。 這通常是60%到80%。

## 啟用和配置Abmey映像優化

為Adobe Commerce Cloud專案設定Ampley服務後，請參閱 [快速影像優化](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html) 以獲得啟用和配置映像優化的說明。

## 其他資訊

- [設定Obmey](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
- [最佳化的影像可能會導致效能問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)
