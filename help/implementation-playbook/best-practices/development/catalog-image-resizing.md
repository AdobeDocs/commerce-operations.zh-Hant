---
title: 目錄影像調整大小最佳實務
description: 瞭解如何在Adobe Commerce網站生產推出之前防止效能降低。
feature: Best Practices
role: Developer
exl-id: 591b1a62-bdba-4301-858a-77620ee657a9
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# 目錄影像調整大小最佳實務

在商店投入生產之前，應調整所有目錄影像的大小。 無法在生產前調整影像大小，而會在頁面載入期間強制調整影像大小，這會大幅降低網站速度，並增加伺服器在啟動後第一天到幾週的負載。

## 慢速方式

使用預設的CLI指令來調整所有影像的大小：

```bash
bin/magento catalog:images:resize
```

此方法的缺點包括：

- 該程式是單執行緒
- 此程式會重新調整已調整大小的影像大小
- 此程式無法中斷，可能需要數天的時間

## 快速方式

Adobe Commerce 2.4已匯入非同步影像調整大小，且可更快調整影像大小。

1. 在每部網頁伺服器上，暫時啟動一些額外的佇列處理常式（每部伺服器實體處理器數目的兩倍）：

   ```bsh
   for i in {1.."$((2 * `nproc --all`))"};do bin/magento queue:consumers:start media.storage.catalog.image.resize &;done;
   ```

1. 確認佇列處理常式正在執行：

   ```bash
   pgrep -fl media.storage.catalog.image.resize
   ```

1. 以所有影像大小調整要求填滿佇列：

   ```bash
   bin/magento catalog:images:resize --async
   ```

1. 調整所有影像大小之後，請終止程式：

   ```bash
   pkill -f media.storage.catalog.image.resize
   ```

## 快速方式

還有另一種方式可以使用前端來調整影像大小。

此方法的優點包括：

- 此程式為多執行緒
- 處理程式是多伺服器（如果您有多個Web節點、負載平衡器以及`media/`目錄的共用磁碟空間）
- 此程式會略過已調整大小的影像

此方法可在8小時內重新調整100,000個影像的大小，而CLI命令需要6天才能完成。

1. 登入伺服器。
1. 導覽至`pub/media/catalog/product`並記下其中一個雜湊(例如0047d83143a5a3a4683afdf1116df680)。
1. 在下列範例中，將`www.example.com`取代為您存放區的網域，並將雜湊取代為您指出的網域。

>[!BEGINTABS]

>[!TAB sed]

```bash
cd pub/
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' > images.txt
```

>[!TAB 圍攻]

`siege`的缺點是，如果並行設定為10，則會在10次中造訪所有URL。

```bash
siege --file=./images.txt --user-agent="image-resizer" --no-follow --no-parser --concurrent=10 --reps=once
```

>[!TAB curl]

```bash
xargs -0 -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n" < <(tr \\n \\0 <images.txt)
```

`-P`引數決定執行緒的數目。

>[!TAB bash one-liner]

`find/curl`範例的單一內嵌專案，如果您可以從影像所在的相同電腦執行`curl`：

```bash
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' | xargs -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n"
```

再次將`www.example.com`取代為您的網站網域，並將`-P`設定為伺服器可處理的執行緒數目而不會當機。

>[!ENDTABS]

輸出會傳回存放區中所有產品影像的清單。 您可以使用所有可用的伺服器和處理器核心來編目影像（使用`siege`或任何其他編目程式），並以比其他方法快得多的速度產生大小調整快取。

造訪一個影像快取URL會在背景產生所有影像大小（如果尚未存在）。 此外，它會略過已調整大小的檔案。

>[!NOTE]
>
>- 雲端基礎結構專案上的Adobe Commerce可將產品影像調整大小解除安裝到Fastly服務。 請參閱[雲端指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html#deep-image-optimization)中的&#x200B;_深度影像最佳化_。
>- 如果您使用遠端儲存模組，也可以嘗試將影像大小調整解除安裝到nginx。 請參閱[設定指南](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/storage/remote-storage/remote-storage-image-resize.html)中的&#x200B;_設定遠端儲存裝置的影像大小_。
