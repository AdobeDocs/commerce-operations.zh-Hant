---
title: 建立、編輯或解除鎖定管理員帳戶
description: 請依照下列步驟管理Adobe Commerce Admin應用程式的管理員帳戶。
feature: Install, User Account
exl-id: d87871a1-717d-4662-b84d-98a018518286
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 建立、編輯或解除鎖定管理員帳戶

您必須先執行下列動作，才能使用此指令：

- [建立部署設定](deployment.md)
- [至少啟用Magento_Authorization和Magento_User模組](manage-modules.md)
- 建立資料庫綱要

>[!NOTE]
>
>建立資料庫最簡單的方法是使用命令`magento setup:upgrade`。

## 建立或編輯管理員

使用此命令來建立管理員或編輯現有的管理員。

>[!NOTE]
>
>如果您正在編輯管理員，則只能編輯`first name`、`last name`和`password`。

命令使用方式：

```bash
bin/magento admin:user:create [--<parameter_name>=<value>, ...]
```

下表定義引數和值：

| 名稱 | 值 | 必填？ |
|--- |--- |--- |
| `--admin-firstname` | 管理員使用者的名字。 | 是 |
| `--admin-lastname` | 管理員使用者的姓氏。 | 是 |
| `--admin-email` | 管理員使用者的電子郵件地址。 | 是 |
| `--admin-user` | 管理員使用者名稱。 | 是 |
| `--admin-password` | 管理員使用者密碼。 密碼長度必須至少為7個字元，且必須至少包含一個字母和至少一個數字字元。 <br><br>建議您使用更長、更複雜的密碼。 如果密碼字串包含需要常值解譯的特殊字元（例如反斜線或空格），請以單引號將密碼括住。 | 是 |
| `--magento-init-params` | 新增至任何命令以自訂應用程式初始化引數<br/><br/>例如： `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | 否 |

使用範例：

```bash
bin/magento admin:user:create --admin-firstname=John --admin-lastname=Doe --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A0b9%t3g
```

```
Created Magento administrator user named j.doe
```

如果您未指定任何必要的引數，應用程式會在CLI中詢問它們：

```bash
bin/magento admin:user:create
```

```
Admin user: John
Admin password:
Admin email: j.doe.young@example.com
Admin first name: John
Admin last name: Doe Young
```

```
Created Magento administrator user named John
```

下列範例更新`j.doe`管理員使用者的`first name`、`last name`和`password`：

```bash
bin/magento admin:user:create --admin-firstname="John X" --admin-lastname="Doe X" --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A1234567
```

```
Created Magento administrator user named j.doe
```

## 解除鎖定管理員帳戶

使用此命令可解除鎖定管理員的帳戶，該帳戶通常是因為多次不正確的登入嘗試而遭鎖定。

```bash
bin/magento admin:user:unlock {username}
```

您必須指定管理員的使用者名稱。 範例：

```bash
bin/magento admin:user:unlock admin
```

```
The user account "admin" has been unlocked
```

如果帳戶未解除鎖定或發生問題，則會顯示下列訊息：

```
The user account "admin" was not locked or could not be unlocked
```

確認使用者是否為管理員、使用者是否使用中，以及帳戶是否已鎖定。 若要檢視Admin中鎖定的使用者清單，請以系統管理員身分登入，然後按一下&#x200B;**系統** > **許可權** > **鎖定的使用者**。

如果帳戶不存在，則會顯示下列訊息：

```
Couldn't find the user account "bob"
```
