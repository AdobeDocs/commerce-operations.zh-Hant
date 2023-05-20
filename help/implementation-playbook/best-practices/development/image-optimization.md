---
title: 優化映像，使站點響應更快
description: 瞭解優化影像的步驟，並使用Abmeist影像優化來優化您的Adobe Commerce站點上的響應時間。
role: Developer, Admin
feature: Best Practices
feature-set: Commerce
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# 優化映像，使站點響應更快

對於Adobe Commerce雲基礎架構部署，請在上傳映像之前優化映像以縮短站點響應時間。 然後，利用Rembiste影像優化技術，加快影像傳輸速度，簡化影像源集的維護。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

Adobe Commerce在雲基礎架構上


## 優化和壓縮影像

在將影像上載到您的Commerce站點之前，優化並壓縮這些影像，以平衡效能與查看質量。 這有助於增加空間並減少頁面載入時間。

- PNG格式為具有大面積實色的影像提供較小大小的影像。

- JPEG格式為所有其他影像類型提供較小大小的影像。 使用最高壓縮（沒有明顯降級）。 通常是60%到80%。

## 啟用和配置Rembistible映像優化

在你為你的Adobe Commerce Cloud項目設定了&quot;Rabeist&quot;服務後，請參閱 [快速影像優化](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html) 以獲取啟用和配置映像優化的說明。

## 其他資訊

- [設定Repost](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
- [優化程度低的映像可能會導致效能問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)
