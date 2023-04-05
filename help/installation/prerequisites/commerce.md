---
title: 取得Adobe Commerce軟體
description: 了解如何下載Adobe Commerce和Magento Open Source軟體。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---


# 取得Adobe Commerce軟體

您是全球240,000家信任我們電子商務軟體的商家之一。 我們已收集一些資訊來幫助您開始安裝。

## 如何獲取軟體

查看令人興奮的新功能和發行版本的可用性，並了解如何將它們應用於我們的 [產品可用性頁面](https://devdocs.magento.com/release/availability.html).

請參閱下表，了解如何開始安裝Adobe Commerce或Magento Open Source。

<table>
    <tbody>
        <tr>
            <th>使用者需求</th>
            <th>說明</th>
            <th>高級安裝和升級步驟</th>
            <th>快速入門連結</th>
        </tr>
    <tr>
        <td><p>整合商、封裝商</p></td>
        <td><p>想要完全控制已安裝的所有元件，能夠訪問應用程式伺服器，而且技術性很強，可能會將Magento Open Source重新打包到其他元件上。</p>
        </td>
        <td><ol><li>建立撰寫器 <em>專案</em> 包含要使用的元件清單。</li>
            <li>使用Composer來更新套件相依性；uses <code>composer create-project</code> 來得到作曲家暗喻。</li>
            <li>使用安裝應用程式 <a href="../advanced.md">命令行</a>.</li>
        <li>使用升級應用程式和擴充功能  <a href="../../upgrade/implementation/perform-upgrade.md">命令行</a>.</li></ol></td>
        <td><p><a href="../composer.md">獲取元包</a></p></td>
    </tr>
    <tr>
        <td><p>貢獻開發人員</p></td>
        <td><p>導致Magento Open Source程式碼基底、檔案錯誤及自訂應用程式。 技術性極強、有專屬的開發伺服器、了解撰寫器和GitHub。</p>
            <p>您 <em>不能</em> 在生產環境中使用應用程式。</p>
      <p>您必須使用 <a href="../../upgrade/developer/git-installs.md">撰寫器和Git命令</a>.</p></td>
        <td><ol><li>克隆GitHub儲存庫。</li>
            <li>使用撰寫器來更新套件相依性。</li>
            <li>使用安裝應用程式 <a href="../advanced.md">命令行</a>.</li>
            <li>使用升級應用程式 <a href="../../upgrade/developer/git-installs.md">撰寫器和Git命令</a>.</li>
            <li>在 <code>app/code</code> 目錄。</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">複製GitHub存放庫</a></p></td>
    </tr>
    </tbody>
</table>

## 實用資訊

使用頁面左側的連結來導覽安裝每個部分的主題。

## 所需的伺服器權限

UNIX系統需要 `root` 安裝和配置軟體（如Web伺服器PHP）的權限。 如果需要安裝此軟體，請確保您 `root` 存取權。

做 *not* 在web伺服器中安裝應用程式，作為 `root` 用戶，因為web伺服器可能無法與這些檔案交互。

您需要 `root` 建立權限 [檔案系統所有者](file-system/overview.md) 並將該所有者添加到Web伺服器的組中。 使用檔案系統所有者運行 `bin/magento` 命令行中的命令，以設定cron作業，為您調度任務。
