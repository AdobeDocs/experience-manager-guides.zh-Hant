---
title: 設定AEM Site輸出的有效檔案名稱
description: 瞭解如何為AEM網站輸出設定有效的檔案名稱
exl-id: 1e69d6f8-7baf-4189-bbbd-34cd0fec6634
feature: Filename Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# 設定AEM Site輸出的有效檔案名稱 {#id214GK0X0KXA}

與DITA主題允許的有效檔案名稱字元清單類似，您也可以為AEM Site輸出設定有效的檔案名稱字元清單。 URL中不允許使用的部分已知字元為： ```'<>`@$```。 這些字元的設定為在產生AEM Site輸出檔案名稱時，找到時自動轉換為底線「_」。 允許您在AEM Site輸出中設定有效字元的組態存在於`com.adobe.fmdita.common.SanitizeNodeNameImpl`套件組合中。 **設定發佈至AEM Sites時不允許的字元集**&#x200B;設定，在AEM Site輸出檔案名稱中包含要以底線取代的字元。

**父級主題：**&#x200B;[&#x200B;設定檔名](conf-file-names.md)
