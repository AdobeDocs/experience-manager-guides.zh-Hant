---
title: 設定AEM網站輸出的有效檔案名稱
description: 瞭解如何為AEM網站輸出設定有效的檔案名稱
exl-id: 1e69d6f8-7baf-4189-bbbd-34cd0fec6634
feature: Filename Configuration
role: Admin
level: Experienced
hidefromtoc: true
source-git-commit: 3aadc59f5034828cf319992b7acb32d5a88eaf93
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# 設定AEM網站輸出的有效檔案名稱 {#id214GK0X0KXA}

與DITA主題允許的有效檔案名稱字元清單類似，您也可以為AEM網站輸出設定有效檔案名稱字元清單。 URL中不允許使用的部分已知字元為： ```'<>`@$```。 這些字元已設定為在產生AEM網站輸出檔案名稱時，找到時自動轉換為底線「_」。 允許您在AEM站台輸出中設定有效字元的設定存在於`com.adobe.fmdita.common.SanitizeNodeNameImpl`套件組合中。 **設定發佈至AEM Sites時不允許的字元集**&#x200B;設定，在AEM網站輸出檔案名稱中包含要以底線取代的字元。

**父級主題：**[&#x200B;設定檔名](conf-file-names.md)
