---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---
# 2024年8月安全性修補程式重點說明

此版本包含下列重點專案：

* **[!DNL one-time passwords]**&#x200B;的速率限制 — 下列新的系統組態選項現在可用於在[!DNL two-factor authentication (2FA)] [!DNL one-time password (OTP)]驗證上啟用速率限制：

   * [!UICONTROL **雙因素驗證的重試限制**]
   * [!UICONTROL **雙因素驗證鎖定時間（秒）**]

  Adobe建議設定2FA OTP驗證的臨界值，以限制重試次數，減少暴力攻擊。 如需詳細資訊，請參閱&#x200B;_組態參考指南_&#x200B;中的[安全性> 2FA](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/config/security/2fa)。<!-- AC-12095 -->

* **加密金鑰輪換** — 現在有新的CLI命令可用來變更您的加密金鑰。 如需詳細資訊，請參閱[疑難排解加密金鑰輪換： CVE-2024-34102](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102)知識庫文章。

* **修正[CVE-2020-27511](https://nvd.nist.gov/vuln/detail/CVE-2020-27511)** — 解決[!DNL Prototype.js]安全性弱點。<!-- AC-11936 -->

* **修正[CVE-2024-39397](https://nvd.nist.gov/vuln/detail/CVE-2024-39397)** — 解決遠端程式碼執行安全性弱點。 此弱點會影響使用Apache Web Server進行內部部署或自行託管部署的商家。 此修正也可作為獨立修補程式使用。 檢視可用於Adobe Commerce的[安全性更新 — APSB24-61](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-61)知識庫文章以取得詳細資料。<!-- ACSD-60551 -->
