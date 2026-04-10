---
title: 設定AEM網站輸出的有效檔案名稱
description: 瞭解如何為AEM網站輸出設定有效的檔案名稱
feature: Filename Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# 設定AEM網站輸出的有效檔案名稱 {#id214GK0X0KXA}

與DITA主題允許的有效檔案名稱字元清單類似，您也可以為AEM網站輸出設定有效檔案名稱字元清單。 URL中不允許使用的部分已知字元為： ``'<>`@$``。 這些字元已設定為在產生AEM Site輸出檔案名稱時找到時自動轉換為底線&quot;`_`&quot;。

下列標籤會提供根據您的AEM設定，為Experience Manager Guides網站輸出設定有效檔案名稱的指示： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

使用[組態覆寫](download-install-config-override.md#)中提供的指示來建立組態檔。 在設定檔中，提供下列\(property\)詳細資訊，以設定AEM網站輸出中的有效字元：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.common.SanitizeNodeNameImpl` | `aemsite.DisallowedFileNameChars` | 在AEM網站輸出檔案名稱中新增要以底線取代的字元。<br> **預設值**： ``'<\>\`@$`` |

>[!TAB 內部部署]

允許您在AEM站台輸出中設定有效字元的設定存在於`com.adobe.fmdita.common.SanitizeNodeNameImpl`套件組合中。 **設定發佈至AEM Sites時不允許的字元集**&#x200B;設定，在AEM網站輸出檔案名稱中包含要以底線取代的字元。

>[!ENDTABS]
