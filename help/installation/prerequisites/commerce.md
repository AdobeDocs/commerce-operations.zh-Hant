---
title: 獲取Adobe Commerce軟體
description: 瞭解如何下載Adobe Commerce和Magento Open Source軟體。
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# 獲取Adobe Commerce軟體

您是全球24萬家信任我們電子商務軟體的商家之一。 我們收集了一些資訊，以幫助您開始安裝。

## 如何獲取軟體

檢查激動人心的新功能和版本的可用性，並瞭解您如何將它們與我們 [產品可用性頁](https://devdocs.magento.com/release/availability.html)。

有關安裝Adobe Commerce或Magento Open Source的入門資訊，請參閱下表。

<table>
    <tbody>
        <tr>
            <th>用戶需要</th>
            <th>說明</th>
            <th>高級安裝和升級步驟</th>
            <th>開始連結</th>
        </tr>
    <tr>
        <td><p>整合商、打包器</p></td>
        <td><p>希望對已安裝的所有元件進行完全控制，能夠訪問應用程式伺服器，而且技術性很強，可能會重新打包與其他元件的Magento Open Source。</p>
        </td>
        <td><ol><li>建立作曲家 <em>項目</em> 包含要使用的元件清單。</li>
            <li>使用Composer更新包依賴項；使用 <code>composer create-project</code> 來得到作曲家的暗喻。</li>
            <li>使用 <a href="../advanced.md">命令行</a>。</li>
        <li>使用  <a href="../../upgrade/implementation/perform-upgrade.md">命令行</a>。</li></ol></td>
        <td><p><a href="../composer.md">獲取暗喻</a></p></td>
    </tr>
    <tr>
        <td><p>派遣開發人員</p></td>
        <td><p>導致Magento Open Source代碼庫、檔案錯誤和自定義應用程式。 高度技術性，有自己的開發伺服器，瞭解Composer和GitHub。</p>
            <p>你 <em>不能</em> 在生產環境中使用應用程式。</p>
      <p>您必須使用 <a href="../../upgrade/developer/git-installs.md">Composer和Git命令</a>。</p></td>
        <td><ol><li>克隆GitHub儲存庫。</li>
            <li>使用Composer更新包依賴項。</li>
            <li>使用 <a href="../advanced.md">命令行</a>。</li>
            <li>使用 <a href="../../upgrade/developer/git-installs.md">Composer和Git命令</a>。</li>
            <li>自定義 <code>app/code</code> 的子菜單。</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">克隆GitHub儲存庫</a></p></td>
    </tr>
    </tbody>
</table>

## 有用資訊

使用頁面左側的連結導航安裝各部分中的主題。

## 所需的伺服器權限

UNIX系統需要 `root` 安裝和配置軟體（如Web伺服器PHP）的權限。 如果需要安裝此軟體，請確保 `root` 訪問。

做 *不* 在web伺服器docroot中安裝應用程式， `root` 用戶，因為Web伺服器可能無法與這些檔案交互。

你需要 `root` 建立權限 [檔案系統所有者](file-system/overview.md) 並將該所有者添加到Web伺服器組。 使用檔案系統所有者運行 `bin/magento` 命令行和設定cron作業，這些作業將為您安排任務。
