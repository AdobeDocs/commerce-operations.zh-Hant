---
title: 取得Adobe Commerce軟體
description: 瞭解如何下載Adobe Commerce軟體。
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# 取得Adobe Commerce軟體

全世界有24萬名商家，信任我們的電子商務軟體，而您正是其中之一。 我們已收集一些資訊，協助您開始安裝。

## 如何取得軟體

檢查令人興奮的新功能和發行版本的可用性，並瞭解如何在我們的[產品可用性頁面](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability)上取得這些功能和版本。

請參閱下表，瞭解如何開始安裝Adobe Commerce。

<table>
    <tbody>
        <tr>
            <th>使用者需求</th>
            <th>說明</th>
            <th>高階安裝和升級步驟</th>
            <th>開始使用連結</th>
        </tr>
    <tr>
        <td><p>Integrator， packager</p></td>
        <td><p>想要完整控制所有已安裝的元件、存取應用程式伺服器、技術含量高，可能會將Magento Open Source與其他元件重新封裝。</p>
        </td>
        <td><ol><li>建立包含要使用的元件清單的撰寫器<em>專案</em>。</li>
            <li>使用Composer更新套件相依性；使用<code>composer create-project</code>取得Composer中繼套件。</li>
            <li>使用<a href="../advanced.md">命令列</a>安裝應用程式。</li>
        <li>使用<a href="../../upgrade/implementation/perform-upgrade.md">命令列</a>升級應用程式和擴充功能。</li></ol></td>
        <td><p><a href="../composer.md">取得中繼資料</a></p></td>
    </tr>
    <tr>
        <td><p>參與開發人員</p></td>
        <td><p>參與Magento Open Source程式碼基底、檔案錯誤和自訂應用程式。 技術含量高，擁有自己的開發伺服器，瞭解Composer和GitHub。</p>
            <p>您<em>無法</em>在生產環境中使用應用程式。</p>
      <p>您必須使用<a href="../../upgrade/developer/git-installs.md">Composer和Git命令</a>升級。</p></td>
        <td><ol><li>複製GitHub存放庫。</li>
            <li>使用撰寫器更新套件相依性。</li>
            <li>使用<a href="../advanced.md">命令列</a>安裝應用程式。</li>
            <li>使用<a href="../../upgrade/developer/git-installs.md">撰寫器和Git命令</a>升級應用程式。</li>
            <li>在<code>app/code</code>目錄下自訂程式碼。</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">複製GitHub存放庫</a></p></td>
    </tr>
    </tbody>
</table>

## 有用的資訊

使用頁面左側的連結，導覽安裝每個部分的主題。

## 必要的伺服器許可權

UNIX系統需要`root`許可權才能安裝及設定軟體，例如Web伺服器PHP。 如果您需要安裝此軟體，請確定您有`root`存取權。

請&#x200B;*不*&#x200B;以`root`使用者身分在Web伺服器docroot中安裝應用程式，因為Web伺服器可能無法與這些檔案互動。

您需要`root`許可權才能建立[檔案系統擁有者](file-system/overview.md)，並將該擁有者新增至網頁伺服器的群組。 您使用檔案系統擁有者從命令列執行`bin/magento`命令，並設定cron工作，為您排程工作。
